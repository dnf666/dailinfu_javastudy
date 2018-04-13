# afterNodeInsertion() 方法是什么

```
 void afterNodeAccess(Node<K,V> p) { }
 void afterNodeInsertion(boolean evict) { }
 void afterNodeRemoval(Node<K,V> p) { }
```

这三个方法都是子类需要用的方法, 所以在子类当中实现, 子类调用父类的 `putValue()` 方法的时候, 就可以被父类调用, 以保持子类的特性, 例如: LinkedHashMap 的有序性
