### 为什么要学习数据库集群？

单机单节点数据库没有**冗余设计**。就数据来说，如果单点机房停电，服务就不能听够相应的服务。冗余设计就是，当数据库一个节点挂掉后，服务可以正常进行访问。数据库的节点(Node)都集群在一起，可以提高性能。搭建大型互联网技术，肯定要使用到数据库集群技术。

| 行业 | 打车      | 电商      | 直播      | 支付        | 媒体社交 |
| ---- | --------- | --------- | --------- | ----------- | -------- |
| 案例 | 滴滴/滴答 | 淘宝/京东 | 斗鱼/花椒 | 微信/支付宝 | QQ/微信  |

学习要高标准。**请求排队串行化，双维度分库表**等设计。

### 学习方式

- 向大型互联网应用看齐，学习架构设计和业务处理
- 不管学习什么东西，一定要深挖， 不要学习到入门阶段就停止
- 由浅入深，循序渐进，案例由小到大，逐步扩展
- 在开发的时候，一定要用成熟的技术
- 技术学到一定深度的时候，再带着案例学习
- **视频学习**优于**看书学习**
- 好图胜千言

### 学习目标

- 掌握PXC集群MySQL方案原理
- PXC集群的**强一致性**
- PXC集群的**高可用**方案

### 单节点数据库介绍

要想发挥数据库的全部性能，必须采用集群的方式。

单点问题：

​	大型互联网程序用户群体庞大，所以架构必须特殊设计(**性能**)

​	单节点数据库无法满足性能上的要求

​	单节点数据库无冗余设计，无法满足高可用

### [单节点数据库压力测试](<https://blog.csdn.net/wfg18801733667/article/details/52160161>)

**mysqlslap** 是 Mysql 自带的压力测试工具，可以模拟出大量客户端同时操作数据库的情况，通过结果信息来了解数据库的性能状况

```sql
mysqlslap -hlocalhost -uroot -proot -P3306 --concurrency=10000 --iterations=1 --auto-generate-sql --auto-generate-sql-load-type=mixed --auto-generate-sql-add-autoincrement --engine=innodb --number-of-queries=10000 --debug-info
```

### [数据库集群的演进方案](<https://www.imooc.com/video/17160>)(慕课网)

MySQL数据库瓶颈：单表数据达到**两千万**，性能会变得非常的差劲。

第一种集群方案：PXC(Percona XtraDB Cluster)集群(牺牲速度，保证数据强一致性), [搭建PXC集群](./pxc_cluster_build.html)

![PXC集群](https://markshen1992.github.io/document/mysql/arch_01.png)

第二种集群方案：Replication集群, [搭建Replication集群](./rep_cluster_build.html)

![Replication集群](https://markshen1992.github.io/document/mysql/arch_02.png)

第三种集群方案：组合前两种方案

![组合前两种方案](https://markshen1992.github.io/document/mysql/arch_03.png)

大数据领域，**[协同过滤算法](<https://blog.csdn.net/xiaokang123456kao/article/details/74735992>)**

定目标，分解目标，逐步去实现。

### 系统架构方案

#### 系统架构方案1

![系统架构方案1](https://markshen1992.github.io/document/mysql/arch_04.png)

#### 系统架构方案2

![系统架构方案2](https://markshen1992.github.io/document/mysql/arch_05.png)

#### 系统架构方案3

![系统架构方案3](https://markshen1992.github.io/document/mysql/arch_06.png)

[mariadb 与percona server 哪个更适合生产环境](<https://blog.csdn.net/xuheng8600/article/details/79947595>)

[Percona software](<https://www.percona.com/software>)



---



[back2index](./../../index.html)