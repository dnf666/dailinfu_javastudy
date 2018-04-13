# 同一个域名下的不同站点的 Session 共享

一般来讲，我们的登陆信息都是放在 Session 当中的，而 Session 是通过 CookiesId 来获取的

按照HTTP协议规定，如果两个站点在同一个域名下面的话，那么它的 Cookie 是可以共享的

假如我们有两个站点

```java

www.alibaba.com/site1

www.alibaba.com/site2

```

这两个站点共享同一个主机地址，并且二者在同一域名下。

如果刚刚在 site1 当中进行了登陆，当你点击 site1 下的任何的子页面的时候，这些cookie都会发送给 site1

这个时候浏览器端会记录下 Cookie 的域：www.alibaba.com

如果 site2 也是属于这个域下面的一个站点，那么就可以拿到相同的 cookie id，也就可以到缓存 session 的地方获取到 session

# 同一个域但是不同的子域的 session 共享

例如现在有两个站点进行部署的方式如下

```java

sub1.alibaba..com

sub2.alibaba.com

```

这两个站点共享同一域 alibaba.com

默认情况下，浏览器会发送 ookie 所属的域对应的主机。也就是说，来自于 sub1.alibaba.com 的 cookie 默认所属的域是 .sub1.alibab.com。因此，sub2.alibaba.com 不会得到任何的属于 sub1.alibaba.com 的 cookie 信息

这个时候就必须改一下 cookie 的所属域了，可以通过把 cookie 的所属域设置为顶级域 .alibaba.com

然后请求再转发给 sub2.alibaba.com 的时候就能得到相同给的 cookie 了
