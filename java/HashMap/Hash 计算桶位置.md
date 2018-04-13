# Hash 方法过程

```
    static final int hash(Object key) {
        int h;
        return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
    }
```

如果 key == null, 那么 hash 默认为 0

如果不是, 通过虚拟机为该 key 计算得到的一个 hashCode 值的前16位高位与后16位高位做异或运算然后得到一个 hash 值, 这样做是为了混合原始 hash 值的高位和低位增加了低位的随机性

使用的时候用这个 hash 值与容量 n-1 做 与运算就得出在哪个桶位置
