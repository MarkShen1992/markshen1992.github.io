## Linux(CentOS 7) 安装 Percona DB-5.7.21-21

- Percona DB-5.7.21-21 软件下载
- 安装前准备
- 安装
- 测试安装是否成功
- MySQL修改用户密码的两种方法
- 使用Navicat连接不上MySQL怎么办
- Linux下MySQL大小写敏感问题
- 参考资料



### Percona DB-5.7.21-21 软件下载

```
# Percona db 可以在其官网上下载
https://www.percona.com/downloads/Percona-Server-5.7/LATEST/

# 下载下来文件 
Percona-Server-5.7.21-21-r2a37e4e-el7-x86_64-bundle.tar

# 使用 tar 命令解压文件
tar -xvf Percona-Server-5.7.21-21-r2a37e4e-el7-x86_64-bundle.tar
```

### 安装前准备

```
rpm -ivh *.rpm

# Percona 安装装在 CentOS 7 上，安装 Percona 前要先安装 Percona 依赖的程序包
pkgconfig(openssl) 被 Percona-Server-devel-57-5.7.21-21.3.el7.x86_64 需要
net-tools 被 Percona-Server-server-57-5.7.21-21.3.el7.x86_64 需要
mariadb-libs 被 Percona-Server-shared-compat-57-5.7.21-21.3.el7.x86_64 取代
perl(Data::Dumper) 被 Percona-Server-test-57-5.7.21-21.3.el7.x86_64 需要
perl(JSON) 被 Percona-Server-test-57-5.7.21-21.3.el7.x86_64 需要
jemalloc >= 3.3.0 被 Percona-Server-tokudb-57-5.7.21-21.3.el7.x86_64 需要

# 特别要注意的是， jemalloc 这个包可以在网站 
# https://www.rpmfind.net/linux/rpm2html/search.php?query=jemalloc 下载
# 其余软件包直接使用 yum 安装即可

yum remove mariadb-libs
yum install -y net-tools
yum install -y openssl-devel
yum install -y autoconf
yum install -y perl-JSON
```

### 安装

```
rpm -ivh *.rpm

[root@localhost percona5.7]# rpm -ivh *.rpm
警告：jemalloc-3.6.0-1.el6.x86_64.rpm: 头V3 RSA/SHA256 Signature, 密钥 ID 0608b895: NOKEY
警告：Percona-Server-57-debuginfo-5.7.21-21.3.el7.x86_64.rpm: 头V4 DSA/SHA1 Signature, 密钥 ID cd2efd2a: NOKEY
准备中...                          ################################# [100%]
正在升级/安装...
   1:Percona-Server-shared-compat-57-5################################# [ 10%]
   2:Percona-Server-shared-57-5.7.21-2################################# [ 20%]
   3:Percona-Server-client-57-5.7.21-2################################# [ 30%]
   4:Percona-Server-server-57-5.7.21-2################################# [ 40%]
Percona Server is distributed with several useful UDF (User Defined Function) from Percona Toolkit.
Run the following commands to create these functions:
mysql -e "CREATE FUNCTION fnv1a_64 RETURNS INTEGER SONAME 'libfnv1a_udf.so'"
mysql -e "CREATE FUNCTION fnv_64 RETURNS INTEGER SONAME 'libfnv_udf.so'"
mysql -e "CREATE FUNCTION murmur_hash RETURNS INTEGER SONAME 'libmurmur_udf.so'"
See http://www.percona.com/doc/percona-server/5.7/management/udf_percona_toolkit.html for more details
   5:jemalloc-3.6.0-1.el6             ################################# [ 50%]
   6:Percona-Server-tokudb-57-5.7.21-2################################# [ 60%]


 * This release of Percona Server is distributed with TokuDB storage engine.
 * Run the following script to enable the TokuDB storage engine in Percona Server:

        ps-admin --enable-tokudb -u <mysql_admin_user> -p[mysql_admin_pass] [-S <socket>] [-h <host> -P <port>]

 * See http://www.percona.com/doc/percona-server/5.7/tokudb/tokudb_installation.html for more installation details

 * See http://www.percona.com/doc/percona-server/5.7/tokudb/tokudb_intro.html for an introduction to TokuDB


   7:Percona-Server-rocksdb-57-5.7.21-################################# [ 70%]


 * This release of Percona Server is distributed with RocksDB storage engine.
 * Run the following script to enable the RocksDB storage engine in Percona Server:

        ps-admin --enable-rocksdb -u <mysql_admin_user> -p[mysql_admin_pass] [-S <socket>] [-h <host> -P <port>]

   8:Percona-Server-devel-57-5.7.21-21################################# [ 80%]
   9:Percona-Server-test-57-5.7.21-21.################################# [ 90%]
  10:Percona-Server-57-debuginfo-5.7.2################################# [100%]
```

### 测试安装是否成功

```
# 查看 Percona 默认密码
cat /var/log/mysqld.log  | grep "A temporary password" | awk -F " " '{print$11}'

# 使用 mysql 工具连接数据库, 输入临时密码
mysql -uroot -p

# 设置验证密码策略
set global validate_password_policy=0;
ALTER USER USER() IDENTIFIED BY '123456';
```

### MySQL修改用户密码的两种方法

#### ALTER USER 

**基本使用**

```SQL
ALTER USER testuser IDENTIFIED BY '123456';
```

**修改当前登录用户**

```sql
ALTER USER USER() IDENTIFIED BY '123456';
```

**使密码过期**

```
ALTER USER testuser IDENTIFIED BY '123456' PASSWORD EXPIRE;
```

**使密码从不过期**

```
ALTER USER testuser IDENTIFIED BY '123456' PASSWORD EXPIRE NEVER;
```

**按默认设置过期时间**

```
ALTER USER testuser IDENTIFIED BY '123456' PASSWORD EXPIRE DEFAULT;
```

**指定过期间隔**

```
ALTER USER testuser IDENTIFIED BY '123456' PASSWORD EXPIRE INTERVAL 90 DAY;
```

**在MySQL文档里，推荐使用ALTER USER修改用户密码**

#### SET PASSWORD

使用SET PASSWORD的password有两种：

使用默认加密

```
SET PASSWORD FOR testuser = '123456'
```

使用PASSWORD()函数加密

```
SET PASSWORD FOR testuser = PASSWORD("123456")
```

**注意：使用PASSWORD('auth_string')的方式已经被废弃，在以后的版本会把它移除，所以不建议使用它来修改密码。**

### 使用Navicat连接不上MySQL怎么办

- 使用 Navicat 连不上MySQL可能的原因可能有好多种

  - Linux 服务器开着防火墙

    ```shell
    # CentOS 7 中开关防火墙方法
    systemctl start|stop firewalld
    ```

  - MySQL 数据库自己的权限问题

    ```SQL
    # 对于MySQL自己的问题, 我们有两种方式来修改
    1. 改表法
    use mysql;
    update user set host = '%' where user = 'root';
    select host, user from user;
    flush privileges;  
    
    2. 授权法
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'192.168.1.102' IDENTIFIED BY 'aA111111' WITH GRANT OPTION;
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'aA111111' WITH GRANT OPTION;
    FLUSH PRIVILEGES;
    ```

### [Linux下MySQL大小写敏感问题](https://blog.csdn.net/zhaopeng_yu/article/details/80785813)

- Linux 下 case_sensitive 是由`lower_case_table_names`变量控制的。只需要在 `my.cnf` 的配置文件配置下就可以了。`my.cnf` 配置文件位于 /etc/my.cnf 下，使用编辑命令 `vim /etc/my.cnf` 编辑，并添加如下配置即可。

  ```
  [mysqld]
  lower_case_table_names=1
  ```

- 配置完成后, 保存文件退出即可。

  ```
  Esc
  :wq
  ```

- 重启 Percona MySQL 服务

  ```
  service mysqld restart
  systemctl restart mysqld
  ```

## 参考文章

[1] https://www.cnblogs.com/ivictor/p/5142809.html

[2] https://majing.io/posts/10000005531181