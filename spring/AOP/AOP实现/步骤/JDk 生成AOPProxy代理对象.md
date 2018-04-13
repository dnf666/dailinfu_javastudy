#JDK 生成 AopProxy 代理对象

首先需要从 advised 对象当中取得代理对象的代理接库的信息

然后调用 Proxy 当中的 newProxyInstance 方法得到对应的 Proxy 代理对象

在生成代理对象的时候，需要指明三个参数：1.类加载器。2.代理接口。3.InvocationHandler 接口定义的 invoke 方法，提供代理对象的回调入口

# JdkDynamicAopProxy 的 invoke 拦截

在整个创建代理对象的方法当中，第三个参数要求是实现了 InvocationHandler 接口当中 invoke 方法的类，而在创建的时候传入的是 this，也就是说在生成代理类后，调用目标方法的时候，会返回来调用 JdkDynamicAopProxy 当中的 invoke 方法

JdkDynamicAopProxy 中的 invoke 方法会做以下事情

检查是否有实现 Object 的基本方法 equals、hashCode 如果调用的这样的方法，就返回方法结果

然后得到目标对象与拦截器链条

如果拦截器链条为空，那么就直接执行目标对象的方法，否则构造一个 ReflectiveMethodInvocation 优先执行拦截器当中的事情

# 目标方法的调用

对于目标方法的调用是通过 AopUtils 使用反射机制执行其对象当中的 invokeJoinpointUsingReflection 的方法当中实现的

在 InvokeJoinPointUsingReflection 当中直接调用 Method 对象当中的 invoke 方法，但是封装了对异常的处理

# JDK 代理方式

代理对象和目标对象实现了相同的接口，目标对象作为代理对象的一个属性，具体接口实现中，可以在调用目标对象相应方法前后加上其他业务处理逻辑。
