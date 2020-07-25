### 简介

> 这个文档，记录了关于自己对于Spring-Cloud的理解。由于作者水平有限，不正确的地方还请批评指正。

**官网上面spring-cloud的相关介绍：**

> Spring Cloud provides tools for developers to quickly build some of the common patterns in distributed systems (e.g. configuration management, service discovery, circuit breakers, intelligent routing, micro-proxy, control bus). Coordination of distributed systems leads to boiler plate patterns, and using Spring Cloud developers can quickly stand up services and applications that implement those patterns. They will work well in any distributed environment, including the developer’s own laptop, bare metal data centres, and managed platforms such as Cloud Foundry.

**上面文字的翻译：**

> Spring Cloud为开发人员提供了快速构建`分布式系统中`常见模式的工具(`配置管理`、`服务发现`、`断路器`、`智能路由`、`微代理`、`控制总线`)。分布式系统的协调产生了模板模式，使用Spring Cloud开发人员可以快速建立实现这些模式的服务和应用程序。它们在任何分布式环境中都能很好地工作，包括开发者自己的笔记本电脑、裸机数据中心以及云计算等托管平台。

**Spring-cloud 的特性：**

> Spring Cloud专注于为典型用例提供良好的开箱即用体验，并为其他用例提供扩展机制。

1. 分布式/版本配置

2. 服务注册和发现

3. 路由

4. service - to - service调用

5. 负载平衡

6. 断路器

**本次测试的版本：**

1. Spring-cloud:**Hoxton.SR1**
2. Spring-boot:**2.2.2.RELEASE**
3. Spring-Cloud-alibaba: **2.1.0.RELEASE**

### 一、包含的内容

> 这个文档包含了`服务注册中心`、`服务调用`、`服务降级`、`服务网关`、`服务总线`、`消息驱动`等章节。

#### 1.1 服务注册中心

Eureka 服务注册中心

Zookeeper服务注册中心

Consul服务注册中心

Nacos服务注册中心

#### 1.2 服务调用

Ribbon

LoadBlancer （目前还没有完善）

Feign

OpenFeign

#### 1.3 服务降级

Hystrix 断路器

resilience4j 熔断器

Sentinel

#### 1.4 服务网关

Zuul

Zuul2

GateWay

#### 1.5 服务配置中心

Spring Cloud Config 分布式配置中心

Nacos

#### 1.6 消息驱动

SpringCloud Stream 消息驱动

#### 1.7分布式请求链路追踪

 Spring Cloud Sleuth分布式请求链路追踪

### 二、Spring Cloud Alibaba

> Spring Cloud Alibaba 系列是阿里公司出来的一款更加方便高效的微服务框架。

主要包含的内容：

#### 2.1 分布式配置、服务注册、消息总线（SpringcloudAlibaba Nacos）

#### 2.2 实现熔断与限流（SpringcloudAlibaba sentinel）

#### 2.3 Springcloud Alibaba seata 处理分布式事务

### 三、版本的相关配置

> 我们采用父子项目的方式进行学习。

**相关依赖的版本号：**

```xml
	<properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <junit.version>4.12</junit.version>
        <log4j.version>1.2.17</log4j.version>
        <mysql.version>8.0.19</mysql.version>
        <druid.version>1.1.16</druid.version>
        <spring.boot.version>2.2.2.RELEASE</spring.boot.version>
        <spring.cloud.version>Hoxton.SR1</spring.cloud.version>
        <spring.cloud.alibaba.version>2.1.0.RELEASE</spring.cloud.alibaba.version>
        <mybatis.spring.boot.version>1.3.0</mybatis.spring.boot.version>
        <lombok.version>1.18.8</lombok.version>
    </properties>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>${spring.boot.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>${spring.cloud.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>com.alibaba.cloud</groupId>
                <artifactId>spring-cloud-alibaba-dependencies</artifactId>
                <version>${spring.cloud.alibaba.version}</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>${mysql.version}</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba</groupId>
                <artifactId>druid</artifactId>
                <version>${druid.version}</version>
            </dependency>
            <dependency>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
                <version>1.18.8</version>
            </dependency>
            <dependency>
                <groupId>org.mybatis.spring.boot</groupId>
                <artifactId>mybatis-spring-boot-starter</artifactId>
                <version>1.3.0</version>
            </dependency>
            <!--
                SR5会有下面的问题
               Correct the classpath of your application so that it contains a single, compatible version of reactor.netty.resources.ConnectionProvider

               https://www.yht7.com/news/18312
               -->
            <!--<dependency>-->
            <!--<groupId>io.projectreactor.netty</groupId>-->
            <!--<artifactId>reactor-netty</artifactId>-->
            <!--<version>0.9.2.RELEASE</version>-->
            <!--</dependency>-->
        </dependencies>
    </dependencyManagement>

    <build>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <fork>true</fork>
                    <addResources>true</addResources>
                </configuration>
            </plugin>
        </plugins>
    </build>
```

