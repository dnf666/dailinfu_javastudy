# SELECT

**SELECT** 的操作通常会返回一个数据集, 所以 MVCC 模式下的 SELECT 会以下面两个要求来塞选数据

- InnoDB 只查找比当前事务把版本早的系统版本, 也就是说行的系统版本要小于或者等于当前事务版本, 这样可以确保得到的每一行数据, 要么是事务开始前就存在的, 要么是事务自己插入或者修改的
- **行的过期时间** 标记要么没有定(为空) 要么大于当前的事务版本号(这样就表示事务读取到这一行的时候, 这个数据是没有被删除的)
