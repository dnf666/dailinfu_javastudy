同步阻塞的BIO、同步非阻塞的NIO、异步非阻塞的AIO


bio存在大并发问题，因为每个线程都要等待服务端响应，并发量大的话还可能使服务器宕机

而nio就是解决bio的大并发问题。每个客户端都有一个socket连接对应一个socketchannel。每个socketchannel都注册（通过register方法。给selector一个selectionkey对象）
在一个唯一的selector。每个selector 对应多个channel ，服务端只用一个selector或者多个selector做处理连接。
selector不断获取select方法的值。值是selectkey的数目。如果selectkey大于0.说明有channel需要处理。则selector对channel的请求存在bytebuffer中处理
selector处理后返回数据到bytebuffer中。异步读给客户端


aio是nio2.0版本。在jdk1.7的时候，sun公司将nio的select/poll模型改为了select/epoll模型。真正地实现了异步非阻塞


bio通信模型
![image](https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3998843336,2088311625&fm=27&gp=0.jpg)

所有用户进程都由一个acceptor监听并且接收。每个用户进程都会单独创建一个输出流
如果并发量很大的话，服务器就刚不住了


