# 示例

``` xml
    <update id="updateAuthor">
        update author set
            username = #{username},
            password = #{password},
            email = #{email}
        where id = #{id}
    </update>
```
