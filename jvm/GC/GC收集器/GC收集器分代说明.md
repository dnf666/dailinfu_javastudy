# 垃圾收集器

垃圾收集器是 GC 算法的具体实现, 需要根据老年代与新生代的特征来具体设计, JVM 规范当中没有强制限定的要求

新生代垃圾收集器: **Serial** **ParNew** **Parallel Scavenge**

老年代垃圾收集器: **CMS** **Serial Old** **Parallel Old**

全能收集器: **G1**
