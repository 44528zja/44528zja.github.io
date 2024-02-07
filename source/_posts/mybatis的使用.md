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
      <!--typeAlias设置别名 有属性alias可以省略 省略alias后，类的简名为别名-->
      <typeAlias type="com.study.pojo.user"/>
      <!--<package name="com.study.pojo">-->
      <!--包下所有类自动起别名，使用简名作别名-->
      <!--namespace命名空间不能用别名，得用全限定类名-->
      <package name="com.study.pojo"/>
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
        <!--一般使用包扫描,不使用上面的mapper映射-->
        <!--使用前提 mapper文件和接口放在一起，名字得相同-->
        <!--在resource目录下建包得com/study 不能com.-->
        <mapper class"com.study.mapper.SqlMapper"/>
        <package name="com.study.mapper"/>
    </mappers>
  </configuration>
  ```

  

* **SqlMapper.xml** 

  ```xml
  <?xml version="1.0" encoding="UTF-8" ?>
  <!DOCTYPE mapper
    PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
    "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
  <!--一般使用框架的mapper映射，所以命名空间一般起名为类全限定名，sql语句id为接口方法名-->
  <mapper namespace="org.mybatis.example.BlogMapper">
    <select id="selectBlog" resultType="Blog">
      select * from Blog where id = #{id}
    </select>
  </mapper>
  ```

* **jdbc.properties**

  ```properties
  jdbc.driver = com.mysql.cj.jdbc.Driver
  jdbc.username = root
  jdbc.password = root
  jdbc.url = jdbc:mysql//localhost:3306/study
  ```
  
  
  
* **logback.xml（可选）**

  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <configuration debug="false">
  
      <!--定义日志文件的存储地址 勿在 LogBack 的配置中使用相对路径-->
      <property name="LOG_HOME" value="/home" />
  
      <!--控制台日志， 控制台输出 -->
      <appender name="STDOUT" class="ch.qos.logback.core.ConsoleAppender">
          <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
              <!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度,%msg：日志消息，%n是换行符-->
              <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{50} - %msg%n</pattern>
          </encoder>
      </appender>
  
      <!--文件日志， 按照每天生成日志文件 -->
      <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
          <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
              <!--日志文件输出的文件名-->
              <FileNamePattern>${LOG_HOME}/TestWeb.log.%d{yyyy-MM-dd}.log</FileNamePattern>
              <!--日志文件保留天数-->
              <MaxHistory>30</MaxHistory>
          </rollingPolicy>
          <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
              <!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度%msg：日志消息，%n是换行符-->
              <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{50} - %msg%n</pattern>
          </encoder>
          <!--日志文件最大的大小-->
          <triggeringPolicy class="ch.qos.logback.core.rolling.SizeBasedTriggeringPolicy">
              <MaxFileSize>10MB</MaxFileSize>
          </triggeringPolicy>
      </appender>
  
      <!-- show parameters for hibernate sql 专为 Hibernate 定制 -->
      <logger name="org.hibernate.type.descriptor.sql.BasicBinder" level="TRACE" />
      <logger name="org.hibernate.type.descriptor.sql.BasicExtractor" level="DEBUG" />
      <logger name="org.hibernate.SQL" level="DEBUG" />
      <logger name="org.hibernate.engine.QueryParameters" level="DEBUG" />
      <logger name="org.hibernate.engine.query.HQLQueryPlan" level="DEBUG" />
  
      <!--myibatis log configure-->
      <logger name="com.apache.ibatis" level="TRACE"/>
      <logger name="java.sql.Connection" level="DEBUG"/>
      <logger name="java.sql.Statement" level="DEBUG"/>
      <logger name="java.sql.PreparedStatement" level="DEBUG"/>
  
      <!-- 日志输出级别 -->
      <root level="DEBUG">
          <appender-ref ref="STDOUT" />
          <appender-ref ref="FILE"/>
      </root>
  </configuration>
  ```

  ##  3.关于SqlsessionUtil的编写
  
  >关于mybatis的事务管理 每个Sqlsession都有自己的commit以及close
  >
  >而转账类似的功能分为以下三步：
  >
  >1.检测转出账号余额是否充足
  >
  >2.转出账号余额扣除转出金额
  >
  >3.转入账号余额存入转账金额
  >
  >这三个功能都要被同一个事务管理 其中有一个出错都要进行事务回退 所以Sqlsession也要进行统一
  >
  >于是引入了ThreadLocal线程池，通过ThreadLocal实现同一Sqlsession
  >
  >下面是代码实现

 ```java
 public class SqlSessionUtil{
     private SqlSessionUtil(){}
     //SqlSession产生流程
     //先通过SqlSessionFactoryBuilder的build方法造出SqlsessionFactory
     //在通过SqlSessionFactory的openSession方法制造出来sqlsession对象
     private staic SqlSessionFactory sqlSesssionFactory;
     //一个SqlsessionFactory代表一个数据库对象，只需要new一次 所以使用static静态加载
     //Resources.getResourcesAsStream为mybatis框架的包装方法
     //实际方法为ClassLoader.getSystemClassLoader().getResourceAsStream("配置文件.xml")
     staic{
         try{
         SqlSessionFactory = new SqlSessionFactoryBuilder.build(Resources.getResourcesAsStream("mybatis-confgi.xml"));
         } catch(IOException e){
             thorw New RuntimeException(e);
         }
     }
     //全局的 服务器级别的 一个服务器定义一个
     private static ThreadLocal<SqlSession> local = new ThreadLocal<>（);
     //sqlSession对象先从ThreadLocal里面拿 如果为null则openSession一个存进Local对象
     public static SqlSession sqlSession =local.get();
     if(sqlSession == null){
         sqlSession =sqlSessionFactory.openSession();
         local.set(sqlSession);
     }
     public static void close(SqlSession sqlSession){
         //先判断非空
         if(sqlSession != null){
             sqlSession.close();
             local.remove();
         }
     }
 }
 ```

> #{}与${}区别
>
> #{} 会预编译问号 以值传递
>
> ${}排序 asc升序  desc降序
>
> 批量删除方案
>
> delete  from t_user  where id =1 or id =2
>
> delete form t_user where id in (1,2)
>
> delete form t_user where id in (${id})
>
> 模糊查询拼接方案
>
> select * from t_car where brand like '%奔驰%'   
>
> select * from t_car where brand like concat ('%','奔驰','%')
>
> select * form t_car where brand like '%${brand}%'
>
> select * from t_car where brand like "%"#{brand}"%"

![](https://raw.githubusercontent.com/44528zja/tc001/main/images202401311408739.png)
