
### Runnable 还是 Thread ？

采用 Thread 的时候, 只能继承一个类, 如果这个类需要继承其它类则不考虑 Thread。同时如果使用 Runnable 实现接口能够更好的独立出逻辑块, 因为一个 Runnable 通常被理解为一个任务
