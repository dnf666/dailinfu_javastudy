如果一个方法的返回值类型是集合或者数组 ，如果在方法内部需要返回的集合或者数组是零长度的，也就是没有实际对象在里面，

我们也应该放回一个零长度的数组或者集合，而不是返回null。如果返回了null，客户端程序员就要检测返回的是不是null，然后才能

进行下一步操作，否则就会引发NullPointException。但是如果是返回的的是空数组或者集合，就不会再后续的使用这个对象上，引发

空指针异常，我们可以根据代码的行为和表现，来判断数组和集合是不是为空。

在Collections中有专门针对List,Set,Map的空的实现。如：

Collections.emptyList()

Collections.emptySet();

Collections.emptyMap();