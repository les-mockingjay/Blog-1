---
title: SpringMVC
date: 2017-01-15 17:19:50
tags: Java
---
参考文档:  
[Spring MVC框架官方文档](http://docs.spring.io/spring/docs/4.0.x/spring-framework-reference/html/mvc.html)

#  导语
>是一个建立在中央前端控制器servlet（DispatcherServlet）的模型 - 视图 - 控制器（MVC）Web框架，这是负责发送每个请求到合适的处理器，解决视图并最终返回响应的概念。

![Spring mvc工作原理](http://ojifsovoq.bkt.clouddn.com/image/jpg/Spring%20mvc%E5%B7%A5%E4%BD%9C%E5%8E%9F%E7%90%86.png)

#  Spring MVC基础
**[Spring4 MVC Hello World – XML实例](http://www.yiibai.com/spring_mvc/spring-mvc-tutorial-for-beginners.html):**使用Spring MVC XML配置的简单 HelloWorld Web应用程序  
**[Spring4 MVC Hello World – 注解 (Java Config)实例](http://www.yiibai.com/spring_mvc/spring-4-mvc-helloworld-tutorial-annotation-javaconfig-full-example.html):**使用Spring MVC基于注解配置（Java的配置）的简单HelloWorld Web应用程序。  
**[Spring4 MVC 表单验证和资源处理 (使用注解)](http://www.yiibai.com/spring_mvc/spring-4-mvc-form-validation.html):**Web应用程序显示使用JSR303 来验证Spring表单标签，表单验证，访问静态资源(CSS,js,images..)。  
**[Spring4 MVC ContentNegotiatingViewResolver实例](http://www.yiibai.com/spring_mvc/spring-4-mvc-contentnegotiatingviewresolver-example.html):**基于注解Web应用程序实例，支持多种输出格式（XML，JSON，XLS，PDF，HTML）使用不同的视图解析器相同的数据。  
**[Spring4 MVC REST服务示例使用@RestController](http://www.yiibai.com/spring_mvc/spring-4-mvc-rest-service-example-using-restcontroller.html):**使用Spring REST API创建一个简单的JSON+ XML服务  
**[Spring4 MVC RESTFul Web Services CRUD实例+RestTemplate](http://www.yiibai.com/spring_mvc/spring-mvc-4-restful-web-services-crud-example-resttemplate.html):**使用Spring MVC4写一个CRUD RESTful Web服务, 写一个REST客户端RestTemplate来使用这些服务。我们也将使用外部客户端测试这些服务  
**[Spring4 MVC + AngularJS – 使用$http异步服务交互](http://www.yiibai.com/spring_mvc/spring-mvc-4-angularjs-example.html):**基于前端AngularJS，使用$http与Spring REST API 根据服务后端异步通信。  

#  Spring MVC + Hibernate
**[Spring4 MVC + Hibernate4 + MySQL + Maven使用注解集成实例](http://www.yiibai.com/spring_mvc/spring-4-mvc-and-hibernate4-integration-example.html):**基于Hibernate和Spring注释配置实例，创建一个简单的应用程序显示如何使用事务管理，JSR303验证，数据库CRUD操作，所有都使用注解  
**[Spring4 MVC + Hibernate4 Many-to-many连接表+MySQL+Maven实例](http://www.yiibai.com/spring_mvc/springmvc-hibernate-many-to-many-join-table.html):**基于注解的Spring MVC4和Hibernate4多对多的例子，显示CRUD操作，管理所有使用视图/JSP，Spring转换器的例子，显示事务管理和JSR303验证、使用多对多的映射。

#  Spring MVC 4 文件上传和下载支持
**[Spring4 MVC使用Servlet 3 MultiPartConfigElement文件上传实例](http://www.yiibai.com/spring_mvc/spring4-mvc-file-upload-using-multipartconfigelement.html):**使用Spring StandardServletMultipartResolver和Servlet API3 的MultipartConfigElement 文件上传实例  
**[Spring4 MVC文件下载实例](http://www.yiibai.com/spring_mvc/spring-mvc-4-file-download-example.html):**Spring4 MVC的文件下载实例，应用程序从文件系统内部以及外部文件下载文件。