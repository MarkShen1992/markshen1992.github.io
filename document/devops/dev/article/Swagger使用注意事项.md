## Swagger 使用注意事项

### 1. 问题01

TypeError: Failed to execute 'fetch' on 'Window': Request with GET/HEAD method cannot have body.

请求方式是 GET/HEAD 的方法不可以有 请求体，修改方法，在Controller中将请求方法修改成 **Post|Put**

