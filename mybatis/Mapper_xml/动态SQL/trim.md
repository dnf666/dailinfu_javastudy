# trim

- prefix 在最开始的时候插入内容
- prefixOverrides 去掉最开始的那一个标记值
- suffixOverrides 去掉最后的那一个标记值

# where 替代方法

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
            <if test="author != null AND author.name != null">
                AND author_name like #{author_name}
            </if>
        </where>
    </select>
```

```xml

    <!-- <trim prefix="WHERE" prefixOverrides="AND | OR"/> -->

    <select id="findActiveBlogLike" resultType="Blog">
        select * from Blog
        <trim prefix="WHERE" prefixOverrides="AND |OR">
            <if test="state != null">
                state = #{state}
            </if>
            <if test="title != null">
                AND title like #{title}
            </if>
            <if test="author != null AND author.name != null">
                AND author_name like #{author_name}
            </if>
        </trim>
    </select>
```

# update

```xml
    <update id="updateAuthorIfNecessary">
        update author
        <set>
            <if test="username != null"> username = #{username}, </if>
            <if test="password != null"> password = #{password}, </if>
            <if test="email != null"> email = #{email}, </if>
            <if test="bio != null"> bio = #{bio} </if>
        </set>
    </update>
```

```xml
    <update id="updateAuthorIfNecessary">
        update author
        <trim prefix="SET" suffixOverrides=",">
            <if test="username != null"> username = #{username}, </if>
            <if test="password != null"> password = #{password}, </if>
            <if test="email != null"> email = #{email}, </if>
            <if test="bio != null"> bio = #{bio} </if>  
        </trim>
    </update>
```
