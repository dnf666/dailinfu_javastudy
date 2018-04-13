# 为什么wait和notify方法要在同步块中调用？

1. Java APi 强制要求, 如果不再同步块当中调用就会抛出 `IllegalMonitorStateException` 异常
2. 执行 wait 和 notify 方法的话, 需要获取对象的锁权限
