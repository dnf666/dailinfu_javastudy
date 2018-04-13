# AdvisedSupport

AdvisedSupport 当中封装通知和通知器的相关操作以及 AOP 代理对象的生成步骤，但是对于具体的 AOP 对象的创建过程，会交给子类去完成

具体的 AOP 代理对象的生成根据需要，分别会交给 ProxyFactoryBean AspectJProxyFactory ProxyFactory

AspectJProxyFactory 是结合 AspectJ 与 spring AOP 的代理方法来生成代理类

ProxyFactoryBean 需要在 IOC 容器中完成配置

ProxyFactory 是编程的方式使用 spring AOP 功能
