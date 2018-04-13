# 什么是 SQL 注入

Sql 注入指的是通过无参数的拼接来查找数据库当中的数据

例如查找的 sql 语句为

```java
String sql = "select * from user where name = " + username;
```

username 是从前段页面传入的，如果 `username ="or 1=1";`，那么就会获取数据库的大部分数据
