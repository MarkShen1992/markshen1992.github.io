# 使用Docker中，出错记录整理

### 1. Navicat连接Docker容器中的MySQL出现

> 2059 - authentication plugin 'caching_sha2_password' can't be loaded

**解决方案**

```sql
-- 在进入容器内root用户对应的密码 
-- step0: launch container from an image
-- docker run -p 3307:3306 --name=mysql-node0 -e MYSQL_ROOT_PASSWORD=123456 -d mysql
-- step1: docker exec -it mysql-node1 bash
-- step2: mysql -uroot -p123456
-- step3: execute following statement
ALTER USER 'root' IDENTIFIED WITH mysql_native_password BY '123456';
```

补充内容之Docker中MySQL的环境变量，[MySQL镜像信息](<https://hub.docker.com/_/mysql>)

```
MYSQL_ROOT_PASSWORD
MYSQL_DATABASE
MYSQL_USER, MYSQL_PASSWORD
MYSQL_ALLOW_EMPTY_PASSWORD
MYSQL_RANDOM_ROOT_PASSWORD
MYSQL_ONETIME_PASSWORD
```

### 2. Docker可视化工具

<https://github.com/weaveworks/scope>

<https://github.com/kevana/ui-for-docker>

<https://rancher.com/>

[推荐portainer](https://www.portainer.io/)



[back2index](./../../index.html)