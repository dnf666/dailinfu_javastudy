# BeanDefiniton 的载入

载入过程相当于把 Bean 的定义结构转化成 IOC 容器当中的内部数据结构的过程，这些 BeanDefinition 通过 HashMap 来保持和维护

在 refresh 方法当中调用 refreshBeanFactory 重新建立 IOC 容器后，就开始了对容器的初始化过程，其中就包含 BeanDefinition 的载入

在 loadBeanDefinitions 当中，首先会初始化一个 BeanDefinitionReader，并且注入到 IOC 容器当中

然后获取 Resource 的定位信息，在调用 BeanDefinitionReader 来读取和载入，载入的过程发生在 Reader 的 loadBeanDefiniton 当中 ，而 AbstractBeanDefinitionReader 以及为它的子类的载入做好了准备

BeanDefinition 的载入分成两部分，首先通过解析器等到文本对象，然后完成文本对象的解析后，又按照 spring bean 规则在 BeanDefinitionDocumentReader 当中处理，由 BeanDefinitionParser 对 Cocument 文档树，处理，把结果给 BeanDefinitionHolder 对象持有， 其中包括了 Bean 的名字、别名集合等等

*！* BeanDefinitionReader 有很多实现类，例如读取 XMl 需要 XmlBeanDefinitionReader 来完成
