# 什么是 ConcurrentHashMap

ConcurrentHashMap 是一个类似于 HashTable 的线程安全的 HashMap，它遵循了 HashTable 的功能规范，含有 HashTable 当中每个方法的方法版本，但是与 HashTable 同步的细节无关。在访问 ConcurrentHashMap 的哈希表的时候，所有的操作都是要求是线程安全的，但是检索操作通常是不需要的，并且使用方法的所有参数都不能为空，也不允许存在空的 key 与 value。它的状态查询方法例如：isEmpty()、size 都是反应某一个时刻的状态，其创建的迭代器也只是某一时刻所包含的键值对，并且只能被一个线程持有，而且不会有 ConcurrentModificationException

ConcurrentHashMap 的 table 初始化发生在第一次插入的操作时候
