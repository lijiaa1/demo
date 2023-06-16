# 基于SpringBoot学生信息管理系统

设计实现与系统测试
1、设计目的
（1）熟悉基于SpringBoot 学生管理系统开发的基本过程。
（2）实现了注册用户邮箱认证功能。
（3）了解mybatis。会集成mybatis。使用mybatis查询数据和新增数据。
（4）认识Thymeleaf模板。在springboot中集成Thymeleaf。使用Thymeleaf。
（5）了解Springboot的日志文件以及配置错误页，拦截器等。
（6）实现Springboot 提供的文件上传功能。
2、设计背景
2.1需求分析
2.1.1概述
随着社会的发展，人们生活水平的不断提高，物质文化的发展已经远远满足不了人们的需求，精神文明有了飞速的发展， 因此学校也更需要快速便捷的方法来管理学生。
2.1.2开发环境
运行环境：推荐JDK 1.8；
开发工具：IDEA（推荐）、Eclipse、MyEclipse；
操作系统：windows 10 8G内存以上（其他windows以及macOS支持，但不推荐）；
数据库：MySQL5.6(推荐)及其他版本（支持）；
数据库可视化工具：Navicat Premium 15（推荐）以及其他Navicat版本 
3、设计思路
根据学生信息管理系统的需求，该系统实施后，应达到以下目标。
（1）界面设计友好、美观，数据存储安全、可靠
（2） 查看功能，保证数据查询的灵活性。
（3） 提供用户登录的功能，保证系统的安全性。
（4） 提供灵活、方便的权限设置功能，使整个系统的管理分工明确。
（5） 系统要最大限度地实现易维护性和易操作性。 
4、总体设计
4.1模块设计
学生信息管理系统总体设计系统功能模块图如下：
 
图1  系统功能模块图
 
图2  系统登录流程图
图3  数据库E-R图
4.1.1文件组成结构
为了直观地看到整个网站的文件包组成结构，下图将网站的组织结构已展示出来。
 
图3  系统文件结构图
4.1.2主要组件以及文件夹说明
DispatcherServlet	框架提供的前端控制器，它是整个 Spring MVC 流程控制中心，负责统一处理请求和响应，调用其他组件对用户请求进行处理。
HandlerMapping框架提供的处理器映射器，根据请求的 url、method 等信息查找相应的对象
Handler开发人员提供的后端处理器，它可以在 HandlerAdapter 的控制下，对具体的用户请求进行处理。
HandlerAdapter框架提供的处理器适配器，负责拿到Handler返回的结果ModelAndView，然后将结果返回给前端控制器DispatcherServlet。
ViewResolver	框架提供的视图解析器，其职责是将从DispatcherServlet中拿到的ModelAndView对象进行解析，生成View对象返回给DispatcherServlet。
View开发人员提供的视图，它作用是将View对象渲染成页面，展示给用户。
Controller包 调用业务层
Service包 处理业务
Mapper包 数据库访问
Vo包 value object
解释：
Controller依赖service 获取传递过来的user，发送到service
Service 处理业务 有时需要调用数据库中的数据 依赖mapper 从数据库获取user，对比，返回true或false
Mapper 数据库访问 获得本地保存的user
Vo  （value object）  user对象----ok
5、详细设计
5.1用户信息管理页面
5.1.1登录界面
 
5.1.2注册界面
 

     
5.2学生信息管理页面
5.2.1学生信息
 
 
5.2.2宿舍信息
 


5.3课程信息管理页面
5.3.1课程管理
 
5.3.2选课信息
 


5.4成绩信息管理页面
5.4.1学科排名
 
5.4.2学生个人成绩信息
 
5.4.3专业绩点排名
