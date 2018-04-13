# 示例

``` sql
/**

    useGeneratedKeys 如果数据库支持自动生成主键的字段（比如 MySQL 和 SQL Server） 那么就可以开启
    然后设置
    keyProperty="某一字段" 就可以在该列上使用自动生成主键
**/
    <insert id="insertAuthor" useGeneratedKeys="true" keyProperty="id">
        insert into Author (username,password,email,bio)
        values (#{username},#{password},#{email},#{bio})
    </insert>
```

## foreach

```sql
    <insert id="insertAuthor" useGeneratedKeys="true" keyProperty="id">
        insert into Author (username, password, email, bio) values
        <foreach item="item" collection="list" separator=",">
           (#{item.username}, #{item.password}, #{item.email}, #{item.bio})
        </foreach>
    </insert>
```
