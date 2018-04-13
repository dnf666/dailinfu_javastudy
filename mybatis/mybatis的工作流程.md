# mybatis 的工作流程

1. 加载配置文件，会加载全局配置文件、Sql映射文件
2. 创建 SessionFactory ，然后用 SessionFactory 来读取配置文件当中的内容
3. 创建 Session，Session 会在 SessionFactory 当中被创建，Session 是一个接口，包含了对数据的基本操作
4. 创建 Executor，Executor 帮助 Session 来执行 Sql 代码
5. 封装 Sql 对象，Executor 把要处理的 Sql 信息装到 MappedStatemen 对象当中，这里面有 Sql 、参数、结果信息
6. 把 Sql 对向提交并且执行
