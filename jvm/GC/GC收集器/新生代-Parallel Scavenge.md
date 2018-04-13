# Parallel Scavenge 收集器

Parallel Scavenge 收集器回收新生代内存当中的对象, 采用复制算法

Parallel Scavenge 与其它垃圾收集器的区别在于, Parallel Scavenge 更多关注达到一个可控制的吞吐量( 吞吐量 = 运行用户代码时间/虚拟机运行总时间 虚拟机运行总时间等于 = 运行用户代码时间 + 垃圾收集时间), 也就是 CPU 用于运行用户代的时间与 CPU 总消耗时间的比值, 从而提高 CPU 时间的利用率更快的完成计算任务

Parallel Scavenge 主要适合后台运算很多而且不需要太多与用户交互的服务

可以配合 Serial Old & Paralle Old 老年收集器一起工作
