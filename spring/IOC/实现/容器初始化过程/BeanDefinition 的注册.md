# BeanDefinition 的注册过程

BeanDefinition 被载入后，在内部就有了具体的数据结构，但是要通过注册后才能使用

在 DefaultListableBeanFactory 当中，通过一个 HashMap 来持有 BeanDefinition，并且它实现了 BeanDefinitionRegistry 接口，

注册的过程就是把解析得到的 BeanDefinition 设置到 HashMap 当中去

完成了注册的过程，IOC容器初始化过程也就完成了。在 DefaultListableBeanFactory 当中也以及建立了整个 Bean 的配置信息
