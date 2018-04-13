hset hash名称 属性名 属性值 
hmset hash名称 属性名 属性值  属性名 属性值  可以一次设置多个
hget hash名称 属性名 属性值  获得某个属性
hmget  hash名称 属性名 属性值  属性名 属性值  可以一次获得多个
hgetall hash名称 获得所有的键值对
hdel  hash名称 属性名 属性名 删除 hash名称里的多个字段
hincrby hash名称 属性 数字 增加数字
hexists hash名称 属性   看集合里属性是否存在
hlen hash名称 获得所有的值的长度
hkeys hash名称 获得所有的key的名称
hvals hash名称 获得所有值得内容