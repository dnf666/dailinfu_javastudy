
1. 什么是copyonwritearraylist
    线程安全版本的arraylist
2. copyonwritearraylist在写的时候会生成一个副本。写操作在副本上进行。操作完以后就将原来的引用指向新的容器。一种读写分离的实现，但是如果如果多线程写还是会乱套。所以多线程写的情况下还是会加锁
3. copyonwritearraylist与vector的区别
    vector和copyonwritearraylist都是线程安全的。
    但是vector是有迭代器失败。而copyonwritearraylist没有
    多现程下读的性能更高。vector是利用sychronized锁住方法。而copyonwritearraylist是不会上锁的
4. 缺点
  不能用于大数组，因为每次写都要复制。很可能会发生monior gc full gc。
  只能保证最终一致。但不能实时一致
