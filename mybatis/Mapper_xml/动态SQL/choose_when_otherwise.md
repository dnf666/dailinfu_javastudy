# demo

类似于 Java 中的 switch 语句，在 when、otherwise 当中选一个执行

```xml
    <select id="findActiveBlogLike" resultType="Blog">
        select * from blog
            state = 'ACTIVE'
            <choose>
                <when test="title != null">
                    AND title like #{title}
                </when>
                <when test="author != null and author.name != null">
                    AND author_name like #{author_name}
                </when>
                <otherwise>
                    AND featured = 1
                </otherwise>
            </choose>
    </select>
```
