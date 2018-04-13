springaop是一种模块化的技术。将与业务无关的代码和重复代码分离出来形成一个切面。提高了代码的
复用率，也方便了管理
aop主要基于动态代理实现的。在使用流程中有两个步骤，
首先解析
<aop:aspectj-autoproxy proxy-target-class="true" expose-proxy="true"/>
AopNamespaceHandler 注册AspectJAutoProxyBeanDefinitionParser，
这个类会调用wrapifnessary方法获取到所有的通知。然后为当前类找到合适的通知 。
创建代理工厂接下来然后用ProxyFactory的getProxy创建proxyfactory.代理工厂会选择使用jdk的动态代理还是cglib的动态
代理.然后代理类将合适的通知封装成拦截器链。开始调用。