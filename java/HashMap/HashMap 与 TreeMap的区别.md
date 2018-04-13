# HashTable，HashMap，TreeMap的区别

## HashTable & HashMap

- HashMap 不是线程安全的, HashTable 是线程安全的
- HashMap 允许 null 为键或值, Hashtable 不允许
- HashTable 直接使用对象的 hashCod

## TreeMap

TreeMap 能根据键来排序，默认是升序排序，Iterator 遍历 TreeMap 得到的有序的结果
