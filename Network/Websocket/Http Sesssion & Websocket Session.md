# HttpSession 与 WebsokcetSession

从浏览器客户端发起一系列 Http 请求的同一用户都会与同一个 HttpSession 相关联

WebSocket 的握手连接也是一种 Http 交互，所以每个 WebSocket Session 对象都与 Http Sesion 对应想有关系，在每个运行于 web 应用的 WebSocket 上都存在一个与它关联的 HttpSession 对象

如果 Http Session 被中断，也例如超时，那么 Websocket 实现会关闭 Webscoket Session

## webSocket 如何获取 HttpSession

因为 webSocket 的连接建立阶段是通过 Http 请求完成的，所以如果要 webSocket 持有 HttpSession，在 WebSocket 当中这个过程是通过自定义类并且继承 Configurator 类并重写方法

```java

    public void modifyHandshake(ServerEndpointConfig sec, HandshakeRequest request, HandshakeResponse response) {

          HttpSession httpSession = (HttpSession) request.getHttpSession();
　　　　　　
          sec.getUserProperties().put(HttpSession.class.getName(), httpSession);
    }

```

在 HandshakeRequest 当中封装了 HttpSession，可以获取到，ServerEndpointConfig 可以把 HttpSession 保存起来

修改注解，再通过 EndPointConfig 来获取

```java


@ServerEndpoint(value = "/example",
                configurator = GetHttpSessionConfigurator.class)
public class GetHttpSessionSocket
{
    private Session wsSession;
    private HttpSession httpSession;

    @OnOpen
    public void open(Session session, EndpointConfig config) {
        this.wsSession = session;
        this.httpSession = (HttpSession) config.getUserProperties()
                                           .get(HttpSession.class.getName());
    }

    @OnMessage
    public void echo(String msg) throws IOException {
        wsSession.getBasicRemote().sendText(msg);
    }
}

```

最后配置一个 web 的 Http 监听器

```java

public class RequestListener implements ServletRequestListener {

    public void requestInitialized(ServletRequestEvent sre)  {
        //将所有request请求都携带上httpSession
        ((HttpServletRequest) sre.getServletRequest()).getSession();
    }

    public RequestListener() {
    }

    public void requestDestroyed(ServletRequestEvent arg0)  {
    }
}

```
