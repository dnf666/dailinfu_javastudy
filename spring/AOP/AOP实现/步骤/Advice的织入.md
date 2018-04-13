# Advice 的织入

AdviceAdapter 有两个接口，一个是判断 advice 的类型，另外一个是返回一个 AdviceAdapater 的具体实例

例如 MethodBeforeAdviceAdapter

在 MethodBeforeAdviceAdapter 当中可以通过 getInterceptor 方法得到一个 MethodBeforeAdviceInterceptor 对象，这个对象当中的 invoke 方法封装了 advice 的执行逻辑
