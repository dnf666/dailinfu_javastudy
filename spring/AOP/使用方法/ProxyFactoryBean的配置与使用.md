# ProxyFactoryBean 的配置与使用

1. 配置通知器 Advisor

Advisor 需要当作一个 Bean 来进行配置，Advisor 当中需要定义切面行为

```xml
    <bean id="log" class="commycompany.LogAround"/>  
```

2. 定义 ProxyFactoryBean

```xml

<bean id="testAOP" class="org.springframework.aop.ProxyFactoryBean">
</bean>

```

3. 配置需要代理的接口

```xml

<bean id="testAOP" class="org.springframework.aop.ProxyFactoryBean">
    <property name="proxyInterfaces" value="com.test.Person" />
</bean>

```

4. 配置需要代理的类

```xml

<bean id="personTarget" class="com.mycompany.PersonImpl">
    <property name="name" value="Tony"/>
    <property name="age" value="51"/>
</bean>

<bean id="testAOP" class="org.springframework.aop.ProxyFactoryBean">
    <property name="proxyInterfaces" value="com.test.Person" />
    <property name="target">
        <ref bean="personTarget"/>
    </propery>
</bean>

```

5. 配置代理接口

```xml
<bean id="log" class="commycompany.LogAround"/>  
<bean id="personTarget" class="com.mycompany.PersonImpl">
    <property name="name" value="Tony"/>
    <property name="age" value="51"/>
</bean>

<bean id="testAOP" class="org.springframework.aop.ProxyFactoryBean">
    <property name="proxyInterfaces" value="com.test.Person" />
    <property name="target">
        <ref bean="personTarget"/>
    </propery>
    <propery name="interceptorNames">
        <list>
            <value>log<value>
        </list>
    </property>
</bean>
```

6. 代理指定方法

```xml
<bean id="log" class="commycompany.LogAround"/>  
<bean id="personTarget" class="com.mycompany.PersonImpl">
    <property name="name" value="Tony"/>
    <property name="age" value="51"/>
</bean>

<bean id="logAdvisor" class="org.springframework.aop.support.RegexpMethodPointcutAdvisor">
    <propery name="advice">
        <ref bean="log"/>
    </property>

    <propery name="patterns">
        <value>.*do.*</value>
    </propery>
</bean>

<bean id="testAOP" class="org.springframework.aop.ProxyFactoryBean">
    <property name="proxyInterfaces" value="com.test.Person" />
    <property name="target">
        <ref bean="personTarget"/>
    </propery>
    <propery name="interceptorNames">
        <list>
            <!-- 这里要修改 -->
            <value>logAdvisor<value>
        </list>
    </property>
</bean>
```
