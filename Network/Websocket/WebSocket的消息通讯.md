# Websocket 的消息通讯

Websocket 消息通讯支持三种消息类型：文本信息、二进制信息、Ping/Pong消息

文本消息 的两种发送方式

```java

//把消息全部发送过去
public void sendText(String args) throws IOException

//以片段的方式发送消息
public void sendText(String args,boolean isLast) throws IOException

```

二进制消息 的两种发送方式

二进制消息适合发送图片、音频这样的特殊格式的数据

```java

//整段发送消息
public void sendBinary(ByteBuffer data) throws IOException

//以片段的方式发送消息
public void sendBinary(ByteBuffer partialByte,boolean isLast) throws IOException

```

Ping/Pong 的发送方式

Ping/Pong 是用来检测连接的健康性和测算连接的效率的，一般最大为 125 个字节

```java

public void sendPing(ByteBuffer applicationData) throws IOException,IllegalArgumentException

public void sendPong(ByteBuffer applicationData) throws IOException,IllegalArgumentException

```

*！*

1. WebSocket 可以传送 Java 对象，取决于把 Java 对象转化成什么样的消息
2. 每当有新的客户端连接进来的时候，都会创建一个新的 Websocket 的端点
3. 任意时候只能有一个线程访问某一个端点
4. Java WebSocket API 可以保证消息以片段的方式发送时的顺序的正确性
