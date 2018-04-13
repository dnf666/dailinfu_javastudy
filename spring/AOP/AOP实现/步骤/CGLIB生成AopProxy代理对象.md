# CGLIB 生成 AopProxy 代理对象

在 CGLIB 当中首先要从 IOC 容器当中调用到 target 目标对象，然后根据 target 对象配置接口

创建 Enhancer 对象，进行配置 Enhancer 对象

然后再调用 Enhancer 当中的 create 方法创建代理对象

# Cglib2AopProxy 的 intercept 拦截

Cglib2AopProxy 的 AOP 拦截调用的回调方法是在 DynamicAdvisedInterceptor 对象当中的 intercept 方法

取得 Advised 中配置到的 AOP 通知

如果没有通知则直接执行目标方法

有通知则通过 CglibMethodInvocation 来启动 advice 通知

# 目标方法的调用

Cglib2AopProxy 的代理对象对方法的调用是在 invoke 方法当中调用 MethodProxy 对象当中的 ivoke 方法来调用的

# 代理方式

主要是对指定的类生成一个子类，覆盖其中的所有方法，所以该类或方法不能声明称final的。
