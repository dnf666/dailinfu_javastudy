# 为什么 notify 和 notifyAll 和 wait 方法不在 Thread 里面

1. java 提供的锁或者等待队列是一个对象级别的不是一个线程级别的
2. 往往我们在调用的时候, 都是希望我们的线程在一个线程的等待队列当中去阻塞, 所以如果在 Thread 里面无法更便捷的制定对象的等待队列
