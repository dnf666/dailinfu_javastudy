# Monitor 的简单描述

Monitor 是一个同步机制，也是一个对象

所有的 Java 对象从被创建起就关联一个 Monitor 对象，所以每个对象都有一把锁，叫做内部锁或者 Monitor 锁

# Monitor Record

monitor record 是线程私有的

Owner：初始时为NULL表示当前没有任何线程拥有该monitor record，当线程成功拥有该锁后保存线程唯一标识，当锁被释放时又设置为NULL；

EntryQ:关联一个系统互斥锁（semaphore），阻塞所有试图锁住monitor record失败的线程。

RcThis:表示blocked或waiting在该monitor record上的所有线程的个数。

Nest:用来实现重入锁的计数。

HashCode:保存从对象头拷贝过来的HashCode值（可能还包含GC age）。

Candidate:用来避免不必要的阻塞或等待线程唤醒，因为每一次只有一个线程能够成功拥有锁，如果每次前一个释放锁的线程唤醒所有正在阻塞或等待的线程，会引起不必要的上下文切换（从阻塞到就绪然后因为竞争锁失败又被阻塞）从而导致性能严重下降。Candidate只有两种可能的值0表示没有需要唤醒的线程1表示要唤醒一个继任线程来竞争锁。
