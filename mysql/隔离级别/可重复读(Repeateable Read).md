### 可重复读(Repeateable Read)

可重复读的意思是, 一个事务如果打开了, 那么就算别的事务提交了对数据的修改, 这个事务依旧可以读取到打开时事务的数据, 直到它本身提交后, 才会读取到新的被别的事务修改过后的数据

#### 说明

例如有两个 session 分别为 session A & session B, 还有一个表 **status(id int, number id)**

实验步骤: 打开两个事务 -> 事务 A 插入数据 **id = 3 & number =30** -> 事务 B 执行查询 -> 事务 A 提交事务 -> 事务 B 再次执行查询

打开两个事务，在 client A 当中执行 ```start transaction;```, 在 client B 当中执行 ```start transaction;```

client A 当中执行代码 ```inser into status (id, number) values (3, 30)``` 插入数据, 在 client B 当中执行查询 ```select id,number from status where id = 3``` 再在 client A 当中提交事务 ```commit;```, 当事务 A 提交过后在 client B 当中再次执行查询 ```select id,number from status where id = 3```

按照事务隔离等级的规则, 事务 B 无法查看到事务 A 插入的数据, 即使事务A 提交了事务, 事务 B 也没有办法查看到事务 A 插入的数据.
