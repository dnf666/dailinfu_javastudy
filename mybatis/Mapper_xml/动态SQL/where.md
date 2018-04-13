# demo

```xml
    <select id="findActiveBlogLike" resultType="Blog">
        select * from Blog
        <where>
            <if test="state != null">
                state = #{state}
            </if>
            <if test="title != null">
                AND title like #{title}
            </if>
            <if test="author != null author.name != null">
                AND author_name like #{author_name}
            </if>
        </where>
    </select>
```

where 元素知道只有在一个以上的if条件有值的情况下才去插入“WHERE”子句。而且，若最后的内容是“AND”或“OR”开头的，where 元素也知道如何将他们去除。
