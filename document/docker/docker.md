# 使用Docker中，出错记录整理

### 1. Navicat连接Docker容器中的MySQL出现

> 2059 - authentication plugin 'caching_sha2_password' can't be loaded

**解决方案**

```sql
-- 在进入容器内root用户对应的密码 
-- step1: docker exec -it mysql-node1 bash
-- step2: mysql -uroot -p123456
-- step3: execute following statement
ALTER USER 'root' IDENTIFIED WITH mysql_native_password BY '123456';
```

