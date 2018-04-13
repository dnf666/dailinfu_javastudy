# Session 与 Cookies

关键点：集群的建立依赖 Session 与 Cookies 的关系

浏览器端存的是 cookie 每次浏览器发请求到服务端是 http 报文头是会自动加上你的 cookie 信息的。服务端拿着用户的 cookie 作为 key 去存储里找对应的 value(session).

同一域名下的网站的 cookie 都是一样的。所以无论几台服务器,无论请求分配到哪一台服务器上同一用户的 cookie 是不变的。也就是说 cookie 对应的 session 也是唯一的。

所以，这里只要保证多台业务服务器访问同一个 redis 服务器(或集群)就行了。
