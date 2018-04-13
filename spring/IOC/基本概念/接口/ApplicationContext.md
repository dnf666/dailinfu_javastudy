# ApplicationContext

ApplicationContext 是大多数容器的入口，其内部仅定义了 获取 Bean 的方法和容器属性的方法

## ApplicationContext 集成的接口

ApplicationContext 集成了其它的许多接口，所以它也有很多其它的体系功能

1. EnvironmentCapable

这是一个用来获取公开环境的接口，环境也就是上下文

2. LisableBeanFactory

这是一个 BeanFactory 接口的扩展，主要是实现一些对 BeanDefinition 的操作

3. HieralchicalBeanFactory

这是 BeanFactory 的子接口，不知道用来干什么，描述不详细，但是有两个方法一个是 `BeanFactory getParentBeanFactory()` 另一个是 `boolean containsLocalBean(String name)`

4. MessageSource

这是用来解析消息的策略接口，支持国际化参数

有两个开箱即用的实现类：`ResourceBundleMessageSource` & `ReloadableResourceBundleMessageSource`

5. ApplicationEventPublisher

这个接口是专门为，内部封装了事件的推送函数

6. ResourcePatternResolver

策略接口

用来把本地地址参数转化成 Resource 对象
