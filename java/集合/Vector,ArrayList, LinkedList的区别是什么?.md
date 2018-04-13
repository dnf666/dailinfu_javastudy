# Vector & ArrayList & LinkedList

## 存放形式

都是以类似数组的形式存放的，LinkedList 是以链表的形式存放的

## 线程同步

Vector 是线程同步的

ArrayList 和 LinkedList 不是线程同步的

## 使用场景

LinkedList 实现方式为链表适用于指定位置的插入与删除操作，不适合查找

ArrayList 与 Vector 适用于查找，不适合于指定为的插入与删除操作

## Vector & ArrayList 扩容

Vector 在 50% 的时候扩容

ArrayList 在 100% 的时候扩容
