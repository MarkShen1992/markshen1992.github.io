### Linux基本命令

---

### Linux系统开端口

```
# 查看防火墙的状态；
firewall-cmd --state

# 开启防火墙
systemctl start firewalld.service
service firewall start

# 关闭防火墙
systemctl start firewalld.service
service firewall stop

# 重启防火墙
systemctl restart firewalld.service
service firewall restart

# 开启8080端口
firewall-cmd --zone=public --add-port=8080/tcp --permanent
# 关闭端口8080
firewall-cmd --zone=public --remove-port=8080/tcp --permanent

# 开启端口范围
firewall-cmd --permanent --add-port=8080-8085/tcp
# 关闭开放端口(注意：单个对单个，范围对范围)
firewall-cmd --permanent --remove-port=8080-8085/tcp

# 查看Linux系统都开放了哪些端口
firewall-cmd --permanent --list-ports

# 查看开启端口和服务
firewall-cmd --permanent --list-ports 80/tcp 8080-8100/tcp
firewall-cmd --permanent --list-services ssh dhcpv6client

# 重新载入配置
firewall-cmd --reload

## 参数解释
--zone=public：表示作用域为公共的；
--add-port=8080/tcp：添加tcp协议的端口8080；
--permanent：永久生效，如果没有此参数，则只能维持当前服务生命周期内，重新启动后失效；

# 查看端口情况 MySQL 数据库
yum install net-tools -y
netstat -na | grep 3306

# telnet 工具使用
rpm -qa telnet
yum install telnet -y
telnet localhost 6379
```

### CentOS 最小安装开机网络不好用

#### 问题描述

```
[root@localhost ~]: ip addr (或者 ip a)
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: ens33: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether 00:0c:29:16:27:c9 brd ff:ff:ff:ff:ff:ff
[root@localhost ~]: ifup ens33
```

#### 解决方案

```
vi /etc/sysconfig/network-scripts/ifcfg-ens33

ONBOOT=no => ONBOOT=yes
Esc => :wq => service network restart

# 测试
ping www.baidu.com
```

CentOS 配置国内镜像

```
# 先安装 wget 命令
yum install -y wget

# 备份
mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

# 换成国内各厂商的镜像
# 换成阿里云镜像
wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
# 换成华为云镜像
wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.huaweicloud.com/repository/conf/CentOS-7-anon.repo

# 清除原来的 yum 缓存
yum clean all

# 刷新缓存
yum makecache

# 刷缓存替换方案(查看所有配置可以使用的文件，会自动刷新缓存)
yum repolist all
```

### Linux 系统常用配置文件



### Linux 系统常用命令



---

[back2index](./../../../../index.html) 

