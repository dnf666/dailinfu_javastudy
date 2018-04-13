# 简介

传入的参数可以制定一个类型

```SQL
    <select>
        select * from Author
            where id = #{id};
    </select>
```

可以改写成为

```SQL
    <select>
        select * from Author
            where id = #{id,javaType=int,jdbcType=int};
    </seelct>
```

## 保存小数点位数的配置

保存两位小数点

```xml
    <select>
        select * from Author
            where id = #{id,javaTyp=int,jdbcType=int,numericScale=2};
    </select>
```

## 注意事项

1. 如果传入的 parameter 对象不是一个 map，那么 javaType 是可以推算出来的
2. 如果 null 也作为一个值来传递的话，那么 jdbcType 是一定需要被指定的
3. MyBatis 会自己去推断参数的类型，很多时候最多你需要为可能为空的列名指定 jdbcType

## #{} 与 ${} 的区别

/#{} 将传入的数据都当成一个字符串，会对自动传入的数据加一个双引号，例如传入的参数为 111，那么在 sql 语句当中会处理成 “111”

${} 将传入的数据直接显示在 sql 语句当中，不做任何处理

${} 一般用作 order by

/#{} 可以防止 SQL 注入
