# 未提交读(Read Committed)

事务当中的修改, 即使没有提交, 其它事务能看见这个事务当中的修改操作

这个级别当中不经不能保证事务的一致性, 而且本身能够得到的性能优化也非常的有限

## 说明

例如有两个 session 分别为 session A & session B, 还有一个表 **status(id int, number id)**

实验步骤为：打开两个事务 -> 事务 A 插入数据 **id = 1 & number = 10** 并且不提交 -> 在事务 B 当中查询 **id = 1** 可以查到该插入记录

打开两个事务，在 client A 当中执行 ```start transaction```, 在 client B 当中执行 ```start transaction```

client A 当中执行代码 ```insert into status (id,number) values (1,10)``` 插入数据， 在 client B 当中执行查询 ```select id,number from status where id = 1;```

按照事务隔离等级的规则, 事务 B 在事务 A 提交之前或提交之后都可以查看到 session A 插入的结果
