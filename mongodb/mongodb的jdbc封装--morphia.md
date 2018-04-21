morphia是个中间件
用来映射mongodb和javamodel

    @Entity("employees")//被该注解修饰代表文档顶级类
    @Indexes(
    @Index(value = "salary", fields = @Field("salary"))
    )
    class Employee {
    @Id
    private ObjectId id;
    private String name;
    @Reference
    private Employee manager;
    @Reference
    private List<Employee> directReports;
    @Property("wage")
    private Double salary;
    }   