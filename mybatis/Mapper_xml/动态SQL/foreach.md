# demo

```xml
    <select id="selectPostIn" resultType="domain.blog.Post">
        SELECT *
            from post p
            where ID in
            <foreach item="item" index="index" collection="list"
                     open="(" separator="," close=")">
                #{item}
            </foreach>
    </select>
```

1. 允许你在 foreach 当中声明一个集合，声明在循环体内使用的集合项和索引变量
2. 允许指定开闭匹配的字符串以及迭代中间放置的分隔符
3. 这个元素是智能的，不会偶然的附加多余的分隔符

# 元素说明

- item 迭代元素，在 map 当中为 value
- index 索引值，在 map 当中为 key
- collection 迭代的容器例如 list、map
- open 开始新迭代的时候添加的符号
- separator 迭代当中元素的隔离符号
- close 结束迭代时添加的符号
