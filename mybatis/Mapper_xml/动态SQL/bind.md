# demo

```xml
    <select id="selectBlogsLike" resultType="Blog">
        <bind name="pattern" value="% + _parameter.getTitle() + %"/>
        SELECT * from blog
        WHERE title like #{patterm}
    </select>
```

bind 元素可以从 OGNL 表达式中创建一个变量并将其绑定到上下文

不是很会用
