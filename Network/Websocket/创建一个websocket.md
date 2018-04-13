# 创建一个 websocket

```java

// 声明一个端点，链接地址为 :ws://localhost:8080/hello
@ServerEndpoint("/hello")
public class HelloWorldEndpoint {


    //接受消息的时候被调用的方法
    @OnMessage
    public String hello(String message) {
        System.out.println("Received : "+ message);
        return message;
    }

    //端点第一次链接的时候被调用的方法
    @OnOpen
    public void myOnOpen(Session session,Endpoint endpoint) {
        System.out.println("WebSocket opened: " + session.getId());
    }

    //端点关闭的时候被调用的方法
    @OnClose
    public void myOnClose(CloseReason reason) {
        System.out.println("Closing a WebSocket due to " + reason.getReasonPhrase());
    }

    //这里处理异常
    @onErrot
    public void errorHandler(Throwable a){
        System.out.println("这里处理异常")
    }

}
```

当一个客户端与 Websocket 服务器建立链接的时候，就会有一个端点实例被创建，如果 WebSocket 端点有多个用户链接，那么 WebSocket 的实现将示例化多次，链接的每个新客户都会示例化一次
