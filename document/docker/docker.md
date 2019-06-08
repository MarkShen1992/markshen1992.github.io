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

### 3. 启动Docker容器

```
docker run -i -t ubuntu /bin/bash
-i: 保证容器中标准输入是开启的
-t: 告诉Docker要分配给创建出的容器一个为 tty 终端
hostname: 检查容器主机名 cat /etc/hosts
--name: 给容器命名(管理容器，唯一) [a-zA-Z0-9_.-]
docker attach: 附着到容器上
-d: 创建守护进程参数
-c: 里面写可运行的代码
docker logs (--tail 0) -ft：容器内部都在干什么
-t: 时间戳
-f: 监控Docker日志
docker top [container_name]: 查看容器内运行的进程
docker exec: 在容器中启动新进程
docker start/stop [container_name]
docker inspect --format='{{.State.Running}}' [container_name]
docker rm 'docker ps -a -q(只返回容器id)'
# docker 镜像构建
docker commit
docker build命令和Dockerfile(常用)
docker port: 容器内的80端口映射到宿主机器的哪个端口上
```

### 4. Dockerfile

[一次较为完整的Docker入门之旅](<https://www.jianshu.com/p/a9c9569c5558>)



---



[back2index](./../../index.html)