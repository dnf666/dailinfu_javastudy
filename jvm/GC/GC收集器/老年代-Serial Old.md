# Serial Old 收集器

Serial Old 负责回收老年代内存当中的对象, 采用标记 - 整理算法

Serial Old 适合于 Client 客户端, 但在 Server 端也有两大用处
1. 在 JDK 1.5版本之前搭配 Pallel Scavenge 收集器使用
2. 当 CMS 并发收集发生 Concurrent Mode Failure 的适合, 作为备用方案

可以配合 Serial & ParNew & Parallel Scavenge 年轻代收集器一起工作
