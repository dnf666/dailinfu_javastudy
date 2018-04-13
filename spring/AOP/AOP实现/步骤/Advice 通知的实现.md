# Advice 通知的实现

在 DefaultAdvisorChainFactory 当中，遍历 Advisor 通知器，通过 GlobalAdvisorAdapterRegistry 对象来完成拦截器的适配和注册的功能

在 GlobalAdvisorAdapterRegistry 当中持有一个 DefaultAdvisorAdapterRegistry ，其中持有 adapter 适配器集合

使用与 advice 通知相对应的 adapter 适配器来查看当前通知是属于哪个种类的通知从而根据不同类型的 advice 来注册不同的 AdviceInterceptor。

AdviceInterceptor 是 Spring 框架设置好的，为不同的 Advice 功能提供服务。最总实现 advice 通知在 AopProxy 代理对象中的织入功能
