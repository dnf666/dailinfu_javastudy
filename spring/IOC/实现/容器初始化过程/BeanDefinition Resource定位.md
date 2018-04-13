# BeanDefinition Resource 定位过程

在定位过程当中，会由一个 Resource 来表示容器使用的 BeanDefinition 存在的地址与查找方法，例如 ClassPathResource 就以为这 Spring 会在类路径当中寻找文件形式的 beandefinition 信息

Resource 一般是被 BeanDefinitionLoader 来处理的，在 AbstractApplicationContext 是 DefaultResourceLoader 的子类，在其中就有 getResourceByPath 来获得 Resource

BeanDefinition 的定位过程是通过 refresh 来触发的，在其中创建了一个 DefaultListableBeanFactroy 工厂，同时它启动了 AbstractRefreshableApplicationContext 当中的 loadBeanDefinitions 方法来载入 BeanDefinition
