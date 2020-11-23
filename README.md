# dubbo2.7.2 源码分析学习

## 服务端源码分析入口说明：
1. Spring解析dubbo的xml配置文件生成bean实例被IOC容器管理，用到的类是：`DubboNamespaceHandler.java`
2. Dubbo 服务端启动提供服务，用到了 `ServiceBean`，对于dubbo2.7.2版本服务暴露的入口是 `ServiceBean.onApplicationEvent()`，对于2.7.8版本服务暴露入口是 `DubboBootstrapApplicationListener.onContextRefreshedEvent()`

## 客户端源码分析入口说明(注解方式)：
1. 客户端首先需要与注册中心（我以Zookeeper作为注册中心为例）建立连接获取服务提供列表，客户端启动时首先通过`AnnotationInjectedBeanPostProcessor.getInjectedObject()`与zk建连，创建远程调用代理对象。
2. 客户端真正发起调用时，入口为 `AnnotationInjectedBeanPostProcessor.AnnotatedFieldElement.inject()`

## 关于服务端和客户端debug调试代码：

- 服务端调试代码地址：https://github.com/shiluoheroking/springboot-dubbo
- 客户端调试代码地址：https://github.com/shiluoheroking/dubbo-consumer

## 关于调试启动问题：

需要先启动Zookeeper，然后才能正常启动dubbo服务端和客户端，
- 服务端启动入口类：`DubboProviderApplication.java`
- 客户端启动类入口：`DubboConsumerApplication.java`




