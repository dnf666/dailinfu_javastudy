# demo

```xml
    <select id="findActiveBlogWithTitleLike" resultType="Blog">
        select * from Blog
            where state = 'ACTIVE'
            <if test="title != null">
                AND title like #{title}
            </if>
            <if test="author != null and author.name != null">
                AND author_name like #{author_name}
            </if>
    </select>
```
