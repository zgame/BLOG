# Spring

	Spring框架是Java平台上的一种开源应用框架，提供具有控制反转特性的容器。

# Spring cloud

	在微服务架构中，Spring Cloud为基于JVM的云应用开发中的服务发现、负载均衡、断路器、智能路由、配置管理、控制总线等等操作提供了一种简单、快捷的开发方式。 Spring Cloud包含了多个子项目，比如：Spring Cloud Netflix 、Spring Cloud Config、Spring Cloud Stream、Spring Cloud Bus、Spring Cloud Sleuth等项目。

	Spring Cloud是一个完整的工具箱，而Dubbo只集成了部分组件，其他组件依赖于第三方，二者比较类似。

	Eureka 服务发现框架
	Ribbon 进程内负载均衡器
	Open Feign 服务调用映射
	Hystrix 服务降级熔断器
	Zuul 微服务网关	鉴权、限流、 路由、监控等功能。
	Config 微服务统一配置中心
	Bus 消息总线   管理和广播分布式系统中的消息

# Spring boot

	全新开源的轻量级Spring框架，通过简化配置来进一步简化了Spring应用的整个搭建和开发过程。


# Spring MVC

	前端控制器 （DispatcherServlet）
	映射处理器（HandlerMapping）
	处理器（Controller）
	模型和视图（ModelAndView）
	视图解析器（ViewResolver）

	控制器是单例模式，所以在多线程访问的时候有线程安全问题，不要用同步，会影响性能，解决方案是在控制器里面不能写字段。


# MyBatis

	MyBatis是支持定制化 SQL、存储过程以及高级映射的优秀的持久层框架。MyBatis 避免了几乎所有的 JDBC 代码和手动设置参数以及获取结果集。MyBatis 可以对配置和原生Map使用简单的 XML 或注解，将接口和 Java 的 POJOs(Plain Old Java Objects,普通的 Java对象)映射成数据库中的记录。

	

# Web

	resources 下的 application.properties
	server.port= 8080	
	  