@bean注解主要用于配置类里。用于方法级别

@Bean
   public TransferService transferService() {
       return new TransferServiceImpl();
   }

等于

<beans>
  <bean id="transferService" class="com.acme.TransferServiceImpl"/>
</beans>
