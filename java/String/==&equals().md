# == 与 equals 的区别

== 测试的两个引用是否指向了同一个对象

equals 有程序员自己定义的对比逻辑, 如果 equals 没有重写, 那么默认为 Object 当中的 equals , 其中的实现是使用 ==
