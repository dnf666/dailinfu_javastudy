# ConcurrentHashMap 结构

1.8 之前
ConcurrentHashMap 当中维护一个 segment 数组，将元素分作若干部分，segment 继承了 ReentrantLock，在每一个 segment 当中又包含一个 HashEntry 数组。每一次并发都是第一次 hash 获取 segement 锁，再次 hash 找到元素。所以默认的 segment 为16，也就只支持 16 个线程并发

1.8 之后
ConcurrentHashMap 当中维护了一个 Node 数组 + 链表/红黑树，Node 当中有 final 的 key 与 volatile 的 value 与 next。并发的方式该做了 synchronized。

在 ConcurrentHashMap 当中使用 volatile 关键来保证读取到工作内存当中的 table 都是最新的
