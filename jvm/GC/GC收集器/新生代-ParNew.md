# ParNew 收集器

ParNew 负责回收新生代内存中的对象, 采用复制算法

ParNew 是 Serial 收集器的多线程版本, 除了并行(指的是多个垃圾回收线程并行执行, 不过同样要暂停用户线程)的特性外, 其余都一致

在单 CPU 的条件下, 回收效率没有 Serial 高, 但是在并发情况下效果更好

ParNew 用于 Server 端, 是唯一款可以和 CMS 搭配的适用于 Server 新生代收集器

可以配合 CMS & SerialOld 老年代收集器一起工作
