# JedisPoolConfig

JedisConfig 类当中配置了 Jedis 的一些配置方法，是有一些默认配置的，可以直接申明，不需要自定义

# JedisPool

```java
JedisPool pool = new JedisPool(new JedisPoolConfig(), "localhost");
```

# Jedis

Jedis 是操作 Redis 数据库的示例

```java

Jedis jedis = pool.getResource();

```

## Jedis 实现

Jedis 底层依赖 Socket 通讯，然后对与各种指令都有对应都格式与长度来描述
