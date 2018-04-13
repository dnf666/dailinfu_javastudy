# HashMap

HashMap 是一个 **key-value** 映射形式的数据结构, 它利用的 **数组** + **链表** + **树** 三种数据结构实现的

允许 **null key** 和 **null value**, 与 HashTable 比起来, HashMap 不是一个线程安全的类, 同时 HashMap 不保证内部的元素是有序的, 同时也不保证在运行期间它内部的元素顺序不会发生改变

影响 HashMap 的性能主要有两个因素 **initial capacity(初识容量)** 和 **load factor(负载因子)**, 如果当前的容量超过了 `负载因子 * 当前最大容量` 就会执行 `resize()` 方法

通常, HashMap 的 `load factory` 为 **0.75** 便可以在 **时间** 和 **空间** 上有一个较好的平衡, 较高的值可以降低空间消耗但是会增大查找的话费, 如果初识数量大于负载因子所限制的最大条目数, 那么就不会发生 `rehash` 操作

如果需要存储大量的元素, 那么应该该创建足够到的容量从而避免 `rehash` 的发生导致额外的时间耗费,

如果有大量的 key 使用了同样的 `hashCode()` 方法, 就会拖累性能, 这个时候为了优化性能, 如果实现了 `Comparable` 接口, 会使用比较顺序的方法是他们保持系数的状态

对于 HashMap 来讲, 修改结构是指添加或删除了内部的一个元素, 如果通过 key 对内部已经存在的值做修改的话, 那么就不算修改了 HashMap 的结构

如果没有类可以封装 HashMap 使它能够线程安全的话, 可以使用 Collections.synchronizedMap `Map map = Collections.synchronizedMap(new HashMap(...))`

fast-fail 策略: 如果一个迭代器被创建了, 一旦 HashMap 发生了结构变化, 那么迭代器就会抛出异常 `ConcurrentModificationException`

如果 Hash 算法把元素放入了一个正确的位置, 那么 get 与 put 方法都是一个常量值. 集合视图迭代需要的时间与 HashMap 当中的实例个数(桶数量)与 HashMap 的大小(key-value 映射数量)来决定的. 所以如果需要考虑到集合视图的性能的话, 就不能设定太高的初始化容量或者太低的 load factory.
