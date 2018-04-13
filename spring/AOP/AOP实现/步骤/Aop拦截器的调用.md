# Aop 拦截器的调用

Jdk 和 CGLIB 都会生成不同 AopProxy 代理对象，然后构造不同的回调方法来启动对拦截器链的调用，但两者都是通过 ReflectiveMethodInvocation 中通过 process 方法实现的

在 process 当中，首先会对拦截器根据需要代理的方法来做一个匹配判断，来决定是否要将通知插入到这里，然后依次调用拦截器上的方法
