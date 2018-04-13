lrem 删除元素   lrem mylist 2 a 从左删掉2个a的元素  
lrem mylist -2 a 从右删除2个是a的元素
lrem mylist 0 a 删除所有是a的元素
lset mylist 2 a 设置位置是2的元素为a
linsert mylist before a aa 从左在元素为a的元素前面插入aa
linsert mylist after a aa 从左在元素a的后面插入aa
lpushx mylist a 如果有此list则插入元素，没有不插
rpoplpush mylist1 mylist2 从list1右边pop出左插入到list2的前面