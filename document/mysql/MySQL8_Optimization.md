## MySQL8优化

​																											                                        **--by Mark** 2020/6/22

### 1.发现问题

#### 1.1用户反馈上报性能问题

​	某某界面加载慢。

#### 1.2慢查询日志

```
set global slow_query_log=ON|OFF
set global slow_query_log_file=/sql_log/slowlog.log
set global long_query_time=xx.xxx(second)
set global log_queries_not_using_indexes=ON|OFF

show variables like 'long_query_time'

# 分析慢查询日志
mysqldumpslow
pt-query-digest

# percona-toolkit 命令工具
```

##### 1.2.1 例子讲解

```
set global slow_query_log=ON
set global long_query_time=0

# SQL 操作
show databases;
use mysql;
select * from proc;

# 查看慢查询日志
more 日志路径

# 使用工具分析慢查询日志
mysqldumpslow 慢查询日志文件
pt-query-degest 慢查询日志文件
```

#### 1.3实时监控长时间运行SQL

```sql
# 监控长时间运行的SQL
SELECT id, `user`, `host`, DB, command, `time`, state, info
FROM information_schema.PROCESSLIST
WHERE TIME > 60
```

### 2.分析执行计划

#### 2.1执行计划都能干啥

- 了解SQL如何访问表中的数据
- 了解SQL如何使用表中索引
- 了解SQL所使用的查询类型

#### 2.2如何获取SQL的执行计划

​	**EXPLAIN/DESC `SQL`** -> SELECT, INSERT, UPDATE, REPLACE, DELETE

#### 2.3执行计划内容分析

- id: 数字/NULL
  - 数字：表示查询执行的顺序, id相同时由上到下执行，id值不同，id值越高，表示其越优先执行
  - NULL: `union`操作后的结果集
- select_type: 查询类型
  - SIMPLE: 不包含子查询或是 `UNION`操作的查询
  - PRIMARY: 查询中如果包含热很子查询，那么最外层的查询则被标记为 PRIMARY
  - SUBQUERY: SELECT中有子查询
  - DEPENDENT SUBQUERY: 依赖外部结果的子查询
  - UNION: union 操作的第二个或是之后的查询的值为union
  - DEPENDENT UNION: 当UNION作为子查询时，第二个或是第二个后的查询的select_type值
  - UNION RESULT: UNION产生的结果集
  - DERIVED: 出现在FROM子句中的子查询
- table: 执行计划中的数据有哪个表输出的
  - <unionM,N> 由ID为M,N查询union产生的结果集
  - <derived N>/<subquery N> 由ID为N的查询产生的结果
- partitions: 分区表的时候才有意义，分区表id/NULL
- type: **system > const  > eq_ref > ref > ref_or_null > index_merge > range** > index > ALL
  - system: 这是const连接类型的一个特例，当查询的表只有一行时使用
  - const: 表中有且只有一个匹配的行时使用，如对主键或唯一索引的查询，效率最高的方式
  - eq_ref: 唯一或主键索引查找，对于每个索引键，表中只有一条与之匹配的记录
  - ref: 非唯一索引查找，返回匹配某个单独值的所有行
  - ref_or_null: 类似ref，附加了对NULL值列的查询
  - index_merge: 使用了索引合并的优化方法
  - range:索引范围扫描，常见于between, >, < 这样的查询条件
  - index: FULL index scan, 同ALL的区别时，遍历所有的索引树
  - ALL: 全表扫描，效率最差
- possible_keys: 指出查询中可能会被用到的索引, 默认值 NULL
- key: 指出查询中实际用到的索引，默认值 NULL
- key_len: 在索引中使用的字节数，实际使用索引的最大长度
- ref: 指出哪些列或常量被用于索引查找
- rows: 根据统计信息预估扫描的行数， 内嵌循环的次数
- filtered: 表示返回结果的行数占需读取行的百分比，值越大，SQL的性能越好
- Extra: 
  - `Distinct` 优化distinct操作，在找到第一匹配的元组后即停止找同样的值的动作
  - `Not exists` 使用 not exists 来优化查询
  - `Using filesort` 使用文件来进行排序，通常会出现在 order by 或 group by 查询中
  - `Using index` 使用了覆盖索引进行查询
  - `Using temporary` MySQL 需要使用临时表来处理查询，常见于排序，子查询和分组查询
  - `Using where` 需要在MySQL服务器层使用 WHERE 条件来过滤数据
  - `select tables optimized away` 直接通过索引来获取数据，不访问表 

### 3.优化索引

#### 3.1优化手段

- 优化SQL查询所涉及到的表中的索引
- 改写SQL以达到跟好的利用索引的目的

- 索引

  - 告诉存储引擎如何快速的查找到所需要的数据

- Innodb 存储引擎所支持的索引

  - Btree
    - 特点
      - 以 B+ 树的结构存储索引数据
      - 从索引**最左侧列**开始匹配查找列
    - 使用场景
      - 全值匹配的查询
      - 处理范围查找
  - Hash
  - 全文索引(5.7 效果不好，如果使用的话，推荐使用搜索引擎服务)
  - 空间索引


#### 3.2应该在哪些列上建索引呢

- `WHERE` 子句中的列，在重复值，在筛选性好的列上建索引

```sql
-- example
SELECT 
	* 
FROM 
	user 
WHERE 
	sex = 1 AND reg_time > '2019-01-01'

-- 哪些列上建索引
SELECT 
	COUNT(DISTINCT sex),
	COUNT(DISTINCT DATE_FORMAT(reg_time, '%Y-%m-%d')),
	COUNT(*),
	COUNT(DISTINCT sex) / COUNT(*),  -- 计算筛选性
	COUNT(DISTINCT DATE_FORMAT(reg_time, '%Y-%m-%d')) / COUNT(*) -- 计算筛选性
FROM
	user;
	
-- 根据筛选性来判断在哪列上创建索引，哪个值高就在那列上创建索引，并且要按列的可筛选性进行排序来确定
-- 在哪张表中创建索引
CREATE INDEX idx_ksxx1_ksxx2_ksxx3 ON `table`(ksxx1, ksxx2, ksxx3);
```

- 包含在 `order by`, `group by`, `distinct` 中的字段
  - `order by` 子句中使用索引的条件
    - 索引列的顺序和 order by 子句的顺序要完全一致
    - 索引列的方向和 order by 子句中固定列的方向也要一致
    - 多个表的关联查询中 order by 中的字段要全部关联表中的第一张表中
    - 多表关联查询时，在关联列上一定要加好索引
- 如何选择符合索引键的顺序
  - 区分度最高的列放在联合索引最左侧（Btree）
  - 使用最频繁的列放到联合索引的最左侧
  - 尽量把字段长度小的列放在联合索引的最左侧
- Btree 索引的限制
  - 只能从左侧开始按索引的顺序使用索引，不能跳过索引键
  - NOT IN 和 <> 操作无法使用索引
  - 索引列上不能使用表达式或函数
- 索引使用的误区
  - 索引越多越好
  - 使用 IN 列表查询不能用到索引
  - 查询过滤顺序必须同索引键顺序相同才能使用到索引

### 4.改写SQL

#### 4.1改写原则

- 使用 outer join 代替 not in
- 使用 **Common Table Expression** 代替子查询
- 拆分负载的大SQL为多个简单的小的SQL
- 巧用计算列优化查询

```sql
ALTER TABLE `table`
ADD COLUMN total DECIMAL(3, 1) AS (column1 + column2 + ... + column(n))

-- create index
create index idx_total ON `table`(total);
```

