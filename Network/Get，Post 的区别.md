# get 与 post 的区别

## 资源角度

get 是从服务器端获取资源，post 是向服务区发送数据

## 提交方式

get 向服务器提交 URL 的方式来通通信，post 通过 Html header 当中提交

## 获取数据的方式

get：服务端用 Request.QueryString 来获取变量的值

post：用 Request.Form 来提交数据的值

## 数据大小

get 最多 1024 字节

post 没有大小限制

## 安全

get 的信息会在地址栏显示

post 信息不会
