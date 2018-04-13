# Java中 CyclicBarrier 和 CountDownLatch 有什么不同？

CyclicBarrier 被叫做 CyclicBarrier 是因为当所有 wait 状态的线程被唤醒后这个 Barrier 对象可以重用

CountDownLatch 内部有一个并发计数器, 计其数归零的时候, 所有的 wait 状态的线程会被唤醒和 await 的后续调用都会回归到就绪状态, 但是这个计数只能被初始化一次, 不能被重置
