1、set key value
设置key的value值

2、get key
获取key的value值

3、getset key value
先获取key的value值，再重新赋值

4、del key
删除key键

5、incr key
为key的value值+1，若key不存在，则把value赋值为0后+1；若value数据类型不为integer，则报错。

6、decr key
为key的value值-1，若key不存在，则把value赋值为0后-1；若value数据类型不为integer，则报错。