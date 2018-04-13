# 创建Servlet对象的时机

## Servlet 容器启动的时候

当 Servelt 容器启动的时候，会读取 web.xml 配置文件，然后构造指定的 Servlet 对象，创建 ServletConfig 对象并且把这一对象传入到 Servlet 的 init 方法当中去

## Servlet 启动后

当 Servelt 容器启动后，客户端首次向 Servlet 发出请求，如果容器当中没有 Servlet 对象，那么则会创建它，然后根据客户端的请求创建 HttpRequest 与 HttpResponse 对象并且调用 Servlet 当中的处理方法来处理请求

## Servlet 类文件被更新后

Servlet 类文件被更新后，重新创建 Servelt，这一条没有尝试过
