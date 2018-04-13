# Session

Session 表示的是与单个连接向关联的状态。

Session 在创建 WebSocket 连接的时候被创建，在创建的时候会被分配一个唯一的标识，一个客户端对应一个 Session

Session 可以获取 RemoteEndpoint 来连接另外一个端点，也可以管理 Session 端点本身例如关闭连接等等功能
