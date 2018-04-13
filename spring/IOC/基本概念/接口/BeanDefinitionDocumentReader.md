# BeanDefinitionDocumentReader

用来解析定义了 Bean Definition 的 XMl 文档

## 接口方法

```java

/**
读取 DOM document 当中定义的 Bean Definition 的定义
并且把 Bean Definition 的定义注入到给定的 Reader Context 当中
**/
void registerBeanDefinitions(Document doc, XmlReaderContext readerContext)
