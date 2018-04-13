# ReentrantLock

ReentrantLock 是一个重入锁，也可以通过构造方法来指定其是否是一个公平锁，但默认是一个非公平锁

```java
Lock lock = new ReentranLock();
lock.lock();
try{
    //do something
}finally{
    lock.unlock();
}
```

## 实现原理

ReentrantLock 内部是通过扩展 AQS(AbstractQueuedSynchronizer) 来实现的

### 获取锁

调用 AQS 的 acquire 方法

需要做两个判断

判断AQS的state是否等于0，表示锁没有人占有，接着，hasQueuedPredecessors判断队列是否有排在前面的线程在等待锁，没有的话调用compareAndSetState使用cas的方式修改state，最后线程获取锁成功，setExclusiveOwnerThread将线程记录为独占锁的线程。

若果前面有人占着锁，就会检查是否是当前线程，如果是当前线程就继续执行

如果两个判断都没有执行通过的化，就加入等待队列，加入队列的时候使用的是一个死循环，保证一定会插入到队列当中

在加入等待队列的时候，Node 对象的初始化，会自动的获取当前线程，并传入到 Node 当中持有

如果没有获取到锁并且成功的加入到等待队列当中后，就会中断当前线程

### 释放锁

释放锁的时候，主要对比当前的线程与当前锁拥有者是否一致，然后在改变 AQS 当中的 state 状态码，表示有一个线程已经退出

然后通过获取队列当中的线程，通过 Unsafe 当中的 unpark 方法来取消对锁的限制
