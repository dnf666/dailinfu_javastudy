# 区别

## BeanFactory

BeanFactory 定义了一系列管理 bean 的功能，包括框架配置接口、和基础接口

## ApplicationContext

ApplicationContext 是 BeanFactory 的子接口，它增加了 Spring AOP 的功能集成、国际化信息资源处理、事件推送、以及 WEB 应用的上下文

所以 ApplicationContext 与 BeanFactory 的区别在于，BeanFactory 只是基础 IOC 功能，而 ApplicationContext 在 BeanFactory 之上针对多数应用扩展了 BeanFactory 接口
