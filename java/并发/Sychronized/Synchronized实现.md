# 字节码

synchronized 方法的实现第一步在编译成字节码的时候就开始了，JVM 的字节码中被 synchronized 修饰的方法在的Class 文件方法表当中 access_flag 字段当中的 synchronized 标记为 1 表示是一个同步的方法

编译器会把 synchronized 块编译成 `monitorenter` 与 `monitorexit` 包裹的代码块，然后把方法翻译成普通的方法

JVM 被要求保证当线程执行到 `monitorenter` 与 `monitorexit` 要成对使用，并且任何一个对象都必须关联一个 monitor，当这个对象的 monitor 被持有后，将处于锁定的状态，不允许其它的线程进入到 monitor 的代码块

# monitro

当线程执行 `monitorenter` 的时候，对应的 monitor 对象会被锁定，然后触发线程的 monitor record 列表来获取锁的相关信息，退出便释放锁，如果 monitor 被持有，获取失败，也会刷行 monitor record 列表来获取锁信息
