# 示例

discriminator 工作原理就像 switch 一样

```xml
    <discriminator javaType="String" column="sex">
         <case value="男" resultType="manResult"/>
         <case value="女" resultType="womanResult"/>
    </discriminator>
```

会根据选取的结果列当中的值来把这些数据包装成为一个特定的对象，例如 sex 为男的时候，就会返回一个 manResult 集合的对象

完整的示例

```xml
  <resultMap id="vehicleResult" type="Vehicle">
      <id property="id" column="id" />
      <result property="vin" column="vin"/>
      <result property="year" column="year"/>
      <result property="make" column="make"/>
      <result property="model" column="model"/>
      <result property="color" column="color"/>
      <discriminator javaType="int" column="vehicle_type">
          <case value="1" resultMap="carResult"/>
          <case value="2" resultMap="truckResult"/>
          <case value="3" resultMap="vanResult"/>
          <case value="4" resultMap="suvResult"/>
      </discriminator>
  </resultMap>
```
