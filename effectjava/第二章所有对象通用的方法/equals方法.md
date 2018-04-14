重写equals方法的规定

### x，y,z都必须是非空对象。
自反性:x.equals(x);必须成立
对称性：如果x.equals(y)为true 则y.equals(x)为true;
传递性:x.equals(y)为true，y.equals(z）为true，则x.equals(z)为true
一致性：只要没有修改equals方法所涉及的信息。equals比较结果不变

x.equals(null);一定为false；



如果null对象调用equals会报nullpointer异常。所以一定要用非null对象调用异常



写出高质量的equals方法
1. 先用==做比较。检查是不是这个对象的引用。如果是就不用比了。直接过了。
2. 然后用instanceof比较。如果是再继续
3. 有instanceof的保证后。可以确保转型不会出错




注意事项：
不要改equals方法的object参数为其他类型。
重写的时候一定要注意equals方法的参数是Object obj类型的引用变量。
绝对不可以是其他类型的变量。
因为这样的话，和父类Object的equals方法名相同，但是参数列表不同，javac认为是重载。
当底层方法真的要调用equals方法的时候，不会调用你重载的equals方法，使得原本打算重载的equals方法失去了意义。