### Linux基本命令

---

### Linux系统开端口

```
# 查看防火墙的状态；
firewall-cmd --state

# 开启防火墙
systemctl start firewalld.service

# 开启8080端口
firewall-cmd --zone=public --add-port=8080/tcp --permanent
## 参数解释
--zone=public：表示作用域为公共的；
--add-port=8080/tcp：添加tcp协议的端口8080；
--permanent：永久生效，如果没有此参数，则只能维持当前服务生命周期内，重新启动后失效；

# 重启防火墙
systemctl restart firewalld.service

# 重新载入配置
firewall-cmd --reload
```



---

[back2index](./../../../../index.html) 

