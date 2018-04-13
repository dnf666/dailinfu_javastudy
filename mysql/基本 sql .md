## sql 的基本操作

### 合并多个 select 语句的结果集

- UNION 合并`SELECT`结果集
- UNION ALL 同 UNION 一样, 只不过允许重复

```
SELECT name from china
UNION
SELECT name from usa
// 合并 china 表和 usa 表当中的 name 属性

SELECT name from china
UNION All
SELECT name from usa
// 合并 china 表和 usa 表当中的 name 属性, 并且允许合并
```
### 查看事务的隔离界别

```
select @@session.tx_isolatio
```

### 设置事务的隔离级别

```
set session transaction isolation level serializable;

// transaction-isolation = {READ-UNCOMMITTED | READ-COMMITTED | REPEATABLE-READ | SERIALIZABLE}
```

### 列出不重复的列

```
SELECT DISTINCT 列名称 FROM 表名称;
```
