---
title: mybatis的使用
date: 2024-01-31 13:34:28
tags: [mybatis,maven,xml,java]
categories: 学习笔记
---

# Mybatis的使用流程

## 1.导入pom依赖

* **mybatis依赖**

  ```xml
  <dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis</artifactId>
  <version>3.5.10</version>
  </dependency>
  ```

* **mysql驱动依赖**

  ```xml
  <dependency>
  <groupId>mysql</groupId>
  <artifactId>mysql-connector-java</artifactId>
  <version>8.0.30</version>
  </dependency>
  ```

* **junit依赖（单元测试jar包，可选）**

  ```xml
  <dependency>
  <groupId>junit</groupId>
  <artifactId>junit</artifactId>
  <version>4.13.2</version>
  <scope>test</scope>
  </dependency>
  ```

* **logback依赖（日记记录jar包，可选）**

  ```xml
  <dependency>
  <groupId>ch.qos.logback</groupId>
  <artifactId>logback-classic</artifactId>
  <version>1.2.11</version>
  </dependency>
  ```

* 

## 2.配置xml文件

* **mybatis-config.xml**

  ```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE configuration
    PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-config.dtd">
  <configuration>
      <!--resource一般为类路径下 url为相对路径-->
      <properties resource='jdbc.properties'/>
      <!--environments可以配置多个环境environment-->
          <!--default用于配置默认的环境设置,取值为环境的id名-->
    <environments default="development">    
        <!--每个环境拥有唯一id-->
      <environment id="development">
          <!--type分为JDBC以及MANAGED-->
          <!--设置MANAGED默认mybatis不负责事务，依靠第三方容器负责-->
          <!--设置JDBC即为依靠JDBC自带的提交与回滚-->
        <transactionManager type="JDBC"/>
          <!--数据源type配置分三种-->
          <!--1.POOLED 使用mybatis自带的线程池-->
          <!--2.UNPOOLED 不使用连接池-->
        <dataSource type="POOLED">
            <!--引用为美元符加大括号 需要先用properties标签引用resource-->
          <property name="driver" value="${driver}"/>
          <property name="url" value="${url}"/>
          <property name="username" value="${username}"/>
          <property name="password" value="${password}"/>
        </dataSource>
      </environment>
    </environments>
    <mappers>
        <!--mapper映射-->
      <mapper resource="org/mybatis/example/BlogMapper.xml"/>
    </mappers>
  </configuration>
  ```

  

* **ObjectMapper.xml** 

* **logback.xml（可选）**

![](https://raw.githubusercontent.com/44528zja/tc001/main/images202401311408739.png)
