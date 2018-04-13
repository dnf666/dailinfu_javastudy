# get 过程

1. spread 计算 hash 值与桶位置
2. 利用 tabAt 方法获取桶元素

tabAt 方法利用的是 Unsafe 类当中的 getObjectVolatile 方法，这是方法获取 obj 对象中 offset 偏移地址对应的 object 型 field 的值,支持volatile load语义，也就是其它线程的修改都是立即可见的，需要重新到主内存去加载数据

3. check first，是则返回当前 Node 的 value ；否则分别根据树、链表查询
