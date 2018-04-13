### 提交读/不可重复读(Read Committed)

提交读的意思是，当一个事务当中执行操作，只有当当前的这个事务提交之后，别的事务才能看到这个事务执行后的数据更新效果

提交读又叫做不可重复度，不可重复读的意识是可能会在读取当中由于另外事务 session A 提交了数据的更改操作，导致没有办法再读取到 session A 提交之前的数据

#### 说明

例如有两个 session 分别为 session A & session B, 还有一个表 **status(id int, number id)**

实验步骤：打开两个事务 -> 事务 A 插入数据 **id = 2 && number = 20** -> 事务 B 执行查询 -> 事务 A 提交事务 -> 事务 B 执行查询

打开两个事务，在 client A 当中执行 ```start transaction;```, 在 client B 当中执行 ```start transaction;```

client A 当中执行代码 ```insert into status (id, number) values (2,20)``` 插入数据, 在 client B 当中执行查询 ```select id,number from status where id = 2;``` 再在 client A 当中提交事务 ```commit;```, 当事务 A 提交过后在 client B 当中再次执行查询 ```select id,number from status where id = 2;```

按照事务隔离等级的规则, 事务 B 无法查看到事务 A 执行 ```commit;``` 命令之前的插入数据, 但是在事务 A 执行完提交语句后 ```commit;```, 事务 B 可以查询到事务 A 执行的插入语句
