### Docker图形化管理工具[portainer](https://www.portainer.io/)安装

---

### 安装前准备

要想安装Docker图形化管理工具portainer，首先要先在Linux系统上安装Docker. 本例中，Linux操作系统使用的是CentOS. 并不是真机，而是基于VMware工具从我的电脑硬件资源中虚拟出来的一台机器。下面我将现在Linux电脑上安装Docker环境。

#### 第一步：配置[Linux镜像](https://mirrors.huaweicloud.com/)加速

```
# 备份配置文件
cp -a /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.bak 

# 下载新的CentOS-Base.repo文件到/etc/yum.repos.d/目录下
1) 第一种方式:
wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.huaweicloud.com/repository/conf/CentOS-7-anon.repo

2) 第二中方式:
sed -i "s/#baseurl/baseurl/g" /etc/yum.repos.d/CentOS-Base.repo
sed -i "s/mirrorlist=http/#mirrorlist=http/g" /etc/yum.repos.d/CentOS-Base.repo
sed -i "s@http://mirror.centos.org@https://mirrors.huaweicloud.com@g" /etc/yum.repos.d/CentOS-Base.repo

# 清除原有yum缓存
yum clean all

# 最后一步
yum makecache（刷新缓存）
yum repolist all（查看所有配置可以使用的文件，会自动刷新缓存）
```

#### 第二步：[Docker安装](https://mirrors.tuna.tsinghua.edu.cn/help/docker-ce/)

```
# 如果你之前安装过 docker，请先删掉
yum remove docker docker-common docker-selinux docker-engine

# 安装一些依赖
yum install -y yum-utils device-mapper-persistent-data lvm2

# 根据你的发行版下载repo文件
wget -O /etc/yum.repos.d/docker-ce.repo https://download.docker.com/linux/centos/docker-ce.repo

# 把软件仓库地址替换为 TUNA
sed -i 's+download.docker.com+mirrors.tuna.tsinghua.edu.cn/docker-ce+' /etc/yum.repos.d/docker-ce.repo

# 最后一步
yum makecache fast
yum install docker-ce
```

#### 第三步：[Docker Hub 镜像加速器](https://segmentfault.com/a/1190000019115546)

编辑文件`daemon.json`，添加如下代码：

```json
{
    "registry-mirrors": [
        "https://1nj0zren.mirror.aliyuncs.com",
        "https://docker.mirrors.ustc.edu.cn",
        "http://f1361db2.m.daocloud.io",
        "https://registry.docker-cn.com"
    ]
}
```

`systemctl daemon-reload`

`systemctl restart docker`

#### 第四步：安装`portainer`.

```
# 下载portainer
docker pull portainer/portainer
docker images

# 修改镜像名字
docker tag portainer/portainer portainer

# 根据镜像 portainer 创建容器
docker volume create portainer_data
docker run -d -p 8000:8000 -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer
```

### 验证 portainer 是否安装成功

![](https://markshen1992.github.io/document/devops/ops/linux/portainer_0100.png)

如图所以，portainer 成功安装。

### 扩展内容

![Docker 知识总结](https://markshen1992.github.io/document/devops/ops/linux/docker_knowledge.jpg)

---

[back2index](./../../../../index.html) 

