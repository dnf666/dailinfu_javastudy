# 用来解决 Java 类与字段名不符合的情况

```xml
     <resultMap id="userResultMap" type="com.mis.model.User">
         <id property="id" column="id" />
         <result property="name" column="name"/>
         <result property="password" column="password"/>
     </reultMap>

     <select id="selectByUserId" resultMap="userResultMap">
         select * from user
             where id = #{id}
     </select>
```

## 高级映射

当有一个作者写了很多篇文章的时候，每一篇文章又有很多评论或者标签

```xml
    <resultMap id="detailedBlogResultMap" type="Blog">
        <constructor>
            <idArg column="blog_id" javaType="int"/>
        </constructor>

        <result property="titile" column="blog_titile"/>

        <!--  -->
        <association property="author" javaType="Author">
             <id property="id" column="author_id"/>
             <result property="name" column="author_name"/>
        </association>

        <!--  -->
        <collection property="posts" ofType="Post">
            <id property="id" column="post_id"/>
            <result property="subject" column="post_subject"/>
            <!--  -->
            <association property="author" javaType="Author"/>
            <!--  -->
            <collection property="comments" javaType="Comment">
                 <id property="id" column="comment_id"/>
            </collection>
            <!--  -->
            <collection property="tags" ofType="Tag">
                <id property="id" column="tag_id"/>
            </collection>
            <!--  -->
            <discriminator javaType="int" column="draft">
              <case value="1" resultType="DraftPost"/>
            </discriminator>
        </collection>
    </resultMap>
```

## resultMap 标签属性

- constructor 类在示例化的时候注入到构造方法当中
  - idArg 标记该结果为 Id 行列可以提高效率
  - arg 注入到构造方法的普通的元素
- id 标记为 ID 元素可以提高效率
- result 注入到字段的普通元素
- association 一个复杂的类型关联;许多结果将包成这种类型 **一对多**
  - 嵌入结果映射 - 结果映射自身的关联,或者参考一个
- collection 复杂类型的集 **一对一**
  - 嵌入结果映射 – 结果映射自身的关联,或者参考一个
- discriminator 使用结果值来决定使用哪个结果映射
  - case 基于某些值的结果映射、
    - 嵌入结果映射 – 这种情形结果也映射它本身,因此可以包含很多相 同的元素,或者它可以参照一个外部的结果映射。
