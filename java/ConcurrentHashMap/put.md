# put 方法流程

1. 计算 hash 值找到桶位置
2. 进入死循环直到插入成功
3. 如果插入的地方为 null ，那么用 Unsafe 中的 compareAndSetObject 插入元素，这个插入方法具有原子性，不会被其它线程打断
4. 然后检查到如果其它线程在扩容，那么会调用 helpTransfer 方法
5. 如果都不是则检查首节点，并且把节点上锁，如果有则更换，没有则直接插入到尾部
6. 最后检查是否需要扩容或者转成树
7. 最后调用 addCount 方法，利用CAS快速更新baseCount的值，然后检查是否需要扩容
