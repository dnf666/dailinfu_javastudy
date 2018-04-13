存储Sorted-Set
1.Sorted-Set和Set的区别
sorted-set：每个成员都有一个分数与之关联，成员唯一，可以对应多个分数
2.Sorted-Set中的成员在集合中的位置是有序的

存储Sorted-Set常用命令：
1.添加元素：zadd
zadd sort 10 a 20 b 30 c #a的分数是10、b的分数是20、c的分数是30
2.获得元素：zscore获得分数、zcard获得成员数量
zscore sort a #获得a的分数
3.删除元素：zrem、zremrangebyrank按照排名范围删除、zremrangebyscore按照分数范围删除
zrem sort a b #删除成员a、b
zremrangebyrank  sort 0 4 #删除排名0-4的成员
zremrangebyscore sort 10 30 #删除分数10-30的成员
4.范围查询：zrange
zrange sort 0 -1 #所有成员
zrange sort 0 -1 withscores #查询成员及分数，从小到大
zrevrange sort 0 -1 withscores #从大到小
5.扩展命令：
zrangebyscore sort 0 100 withscores #显示0-100分数的成员
zrangebyscore sort 0 100 withscores limit 0 2 #显示0-100分数的成员的前两名
zincrby sort 10 c #给c加上10
zcount sort 80 100 # 显示80-100分数的成员个数

Sorted-Set使用场景：
如大型在线游戏积分排行榜
构建索引数据