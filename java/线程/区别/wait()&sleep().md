# wait() 和 sleep() 的区别

wait 的含义是在本对象的等待队列上等待被其它唤醒, 不仅仅要放弃当前所获得的锁权限, 而且在没有被唤醒的时候不参与锁的竞争

sleep 的含义是休眠该线程, 也就是阻塞的意思, 不会放弃当前线程的锁权限, 也不会放弃争夺锁的权限
