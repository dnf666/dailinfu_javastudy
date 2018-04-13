# 功能描述

如果有一段 SQL 语句是被重复使用的那么就可以用 SQL 来定义

# 示例

有这样一段代码

```xml
    <sql id="userColumns"> ${alias}.id,${alias}.username,${alias}.password </sql>
```

那么其它片段就可以这样复用这段代码

```xml
    <select>
        select
            <include refid="userColumns"><property name="alias" value="t1"></include>
            <include refid="userColumns"><property name="alias" value="t2"></include>
        from table1 t1
            cross join table2 t2;
    </select>
```
