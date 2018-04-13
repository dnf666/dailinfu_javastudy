1. ArrayList是实现了基于动态数组的数据结构，LinkedList基于链表的数据结构。

2. 对于随机访问 get 和set，ArrayList觉得优于LinkedList，因为LinkedList要移动指针。

3. 对于新增和删除操作add和remove，LinedList比较占优势，因为ArrayList要移动数据。

4. ArrayList的空间浪费主要体现在在list列表的结尾预留一定的容量空间，而LinkedList的空间花费则体现在它的每一个元素都需要消耗相当的空间
