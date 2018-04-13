# HashMap 与 HashTable 的区别

1. HashMap 不是线程安全的, HashTable 是线程安全的

2. HashMap 允许 null 为键或值, Hashtable 不允许

3. HashTable 直接使用对象的 hashCode 做运算

4. 另一个区别是HashMap的迭代器(Iterator)是fail-fast迭代器，而Hashtable的enumerator迭代器不是fail-fast的。所以当有其它线程改变了HashMap的结构（增加或者移除元素），在迭代过程中将会抛出ConcurrentModificationException

5. HashMap 的数组初始化默认容量为 16，Hashtable 默认为 11
