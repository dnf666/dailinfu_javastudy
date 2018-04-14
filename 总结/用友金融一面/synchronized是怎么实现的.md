### synchronized的实现
    synchronized是基于一个monitor对象实现，在编译阶段，jvm会把synchronized包裹的代码块编译成monitorenter，monitorexit包裹的块
    ，方法会编译为普通方法。并且在class文件方法列表中设置access-flag为1.表示同步方法。每个对象都必须关联一个monitor对象，当线程访问对象成功后会持有monitor对象。对象将进入锁定状态
    不再持有monitor对象即释放锁。monitor被某线程持有，其他线程则无法获取
    
