# Java 中 interrupted 和 isInterruptedd 方法的区别？

两者都是调用 `isInterruptedd(boolean ClearInterrupted)` 方法, 来判断当前运行的线程是否被中断了

interrupted 传递的参数为 `true` 也就是会重置 `interrupted state` 状态变量, 也就是说如果第二次调用, 这个期间当前线程只被中断过一次的话, 就会返回 `false`

isInterruptedd 传递的参数为 `false` 不会重置 `interrupted state` 状态变量

*!* `interrupted state` 用来标识当前线程是否被中断了
