
# 什么是ThreadLocal变量？

ThreadLocal 是一种用空间换取线程安全的做法, 线程可以把原本在内存共享区域的数据拷贝到自己的线程内存上面, 如果线程修改了这个数据不会影响到主内存当中原本的数据, 只会修改自己线程线程空间的那份数据

ThreadLocal 是一个类, 要使用到 ThreadLocal 的类需要内部持有这个类, ThreadLocal 内部有 get 和 set 方法来满足大部分需求, TheadLocal 利用 ThreadLocalMap 来存取对象, Map 当中 key 为 ThreadLocal 自己, value 为值
