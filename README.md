# SpringCloudPractice
Spring Cloud 是一个基于 Spring Boot 实现的云应用开发工具，它为基于 JVM 的云应用开发中涉及的配置管理、服务发现、断路器、智能路由、微代理、控制总线、全局锁、决策竞选、分布式会话和集群状态管理等操作提供了一种简单的开发方式。
## 1.Spring Cloud Eureka ---- 服务治理
Spring Cloud Eureka，使用 Netflix Eureka 来实现**服务注册**与**服务发现**，既包含服务端组件，也包含客户端组件。
**Eureka 服务端**：服务注册中心
**Eureka 客户端**：主要用于处理服务注册和服务发现
### 如何构建 Eureka 服务端？
通过 @EnableEurekaserver 注解来启动一个服务注册中心，使得其他应用之间可以互相对话。此项目中实现 3 结点的注册中心，来保证 Eureka 服务端的高可用。此外，Eureka 还有**心跳检测、健康检查、负载均衡**等功能
### 如何构建 Eureka 客户端？
通过 @EnableDiscoveryClient 注解来启动。在 Spring Boot 应用中添加该注解就行。
### Eureka 服务端的配置
```
#设置此项目的端口
# server.port=8761
#向注册中心2，3注册自己
eureka.client.service-url.defaultZone=http://localhost:8761/eureka/,http://localhost:8762/eureka/
spring.application.name=eureka
# 该应用为服务注册中心，所以设置为false,代表不向注册中心注册自己
eureka.client.register-with-eureka=false
# 注册中心的职责就是维护服务实例，所以它不需要去检索服务，也设置为false
eureka.client.fetch-registry=false
# 开发环境一般将健康检查设置为关闭
eureka.server.enable-self-preservation=false
```
### Eureka 客户端的配置
```
# 注册到3个eureka注册中心
eureka.client.service-url.defaultZone=http://localhost:8761/eureka/,http://localhost:8762/eureka/,http://localhost:8763/eureka/
# 为服务命名
spring.application.name=client
```
## 2.

