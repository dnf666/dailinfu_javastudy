# Parallel Old 收集器

Parallel Old 负责老年代的对象回收, 采用标记 - 整理的算法

Parallel Old 是 Parallel Scavenge 的老年代收集器, 同样关注高吞吐量

只能配合 Parallel Scavenge 完成工作, 针对交互少, 需要大量计算的任务
