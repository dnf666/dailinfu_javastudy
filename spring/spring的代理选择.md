(1)当Bean实现接口时，Spring就会用JDK的动态代理

(2)当Bean没有实现接口时，Spring使用CGlib实现

　  (3)可以强制使用CGlib（在spring配置中加入<aop:aspectj-autoproxy proxy-target-class="true"/>）
