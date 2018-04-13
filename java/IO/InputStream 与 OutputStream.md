# InputStream

InputStream 有一个基本的方法 read()，用来读取单个字节或者字节数组

常见的 InputStream 类型为

1. ByteArrayInputStream 可以从包含字节的内部缓冲区读取字节数据
2. StringBufferInputStream 可以把 String 转化成 InputStream
3. FileInputStream 从文件中读取信息

# OutputStream

OutputStream 有一个基本的方法 write()，用来写单个字节或者字节数组

常见的 OutputStream 类型为

1. ByteArrayOutputStream 在内存当中创建缓存区，并把字节流输入到内存缓冲流当中
2. FileOutputStream 用于将信息写至文件

通常，read 方法和 write 方法不会被我们自己调用，都是通过子类对对写着方法的包装来实现更方便使用的方法
