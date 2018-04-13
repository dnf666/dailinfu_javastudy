# HashMap 的死循环

HashMap 的死循环出现在并发环境下执行 `resize` 方法, 当并发加入 put 的时候, 引起扩容操作, 然后多线程导致 HashMap 的 Entry 链表形成环形数据结构, 查找时候会引起死循环.

具体的过程如下

当有一个线程刚进入 get 方法的时候执行 Entry next = e.next() 方法后被挂起，然后新线程进入，并执行了扩容的操作，如果新的扩容后的链表的位置发生了反转，那么这个时候环形就形成了


假如有两个线程P1、P2，以及链表 a=》b=》null
1、P1先执行，执行完"Entry<K,V> next = e.next;"代码后发生阻塞，或者其他情况不再执行下去，此时e=a，next=b

2、而P2已经执行完整段代码，于是当前的新链表newTable[i]为b=》a=》null

3、P1又继续执行"Entry<K,V> next = e.next;"之后的代码，则执行完"e=next;"后，newTable[i]为a《=》b，则造成回路，while(e!=null)一直死循环
