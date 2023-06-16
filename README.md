# 基于SpringBoot学生信息管理系统

##sql文件
[Uploading student.sql/*
SQLyog Enterprise v12.09 (64 bit)
MySQL - 8.0.13 : Database - student
*********************************************************************
*/


/*!40101 SET NAMES utf8 */;

/*!40101 SET SQL_MODE=''*/;

/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;
CREATE DATABASE /*!32312 IF NOT EXISTS*/`student` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci */;

USE `student`;

/*Table structure for table `login` */

DROP TABLE IF EXISTS `login`;

CREATE TABLE `login` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '主键',
  `email` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL COMMENT '邮件',
  `password` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL COMMENT '密码',
  `salt` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL COMMENT '盐',
  `validation_time` datetime DEFAULT NULL COMMENT '有效时间',
  `is_valid` tinyint(1) DEFAULT '0' COMMENT '0：不可用 1：可用',
  `confirm_code` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci DEFAULT NULL COMMENT '验证码',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=25 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

/*Data for the table `login` */

insert  into `login`(`id`,`email`,`password`,`salt`,`validation_time`,`is_valid`,`confirm_code`) values (20,'admin','65334cb4cd6bdcbe171b6456119479b1','xxhr37ni9','2021-10-13 16:05:41',1,'1447835852951654400');

/*Table structure for table `st_course` */

DROP TABLE IF EXISTS `st_course`;

CREATE TABLE `st_course` (
  `couId` mediumint(9) NOT NULL AUTO_INCREMENT COMMENT '课程id',
  `couName` varchar(20) NOT NULL COMMENT '课程名称',
  `couGrade` mediumint(9) NOT NULL COMMENT '学分',
  `couTime` mediumint(9) NOT NULL COMMENT '学时',
  `major` varchar(20) NOT NULL COMMENT '所属专业',
  PRIMARY KEY (`couId`)
) ENGINE=MyISAM AUTO_INCREMENT=14 DEFAULT CHARSET=utf8;

/*Data for the table `st_course` */

insert  into `st_course`(`couId`,`couName`,`couGrade`,`couTime`,`major`) values (1,'线性代数a',3,64,'通识教育'),(2,'中国近代史',2,64,'通识教育'),(3,'体育与健康',1,32,'通识教育'),(4,'大学英语4',2,64,'通识教育'),(5,'人工智能',2,32,'计算机科学与技术'),(6,'虚拟现实技术',2,32,'软件工程'),(7,'数据库系统概论',4,64,'软件工程'),(8,'java语言设计',3,64,'软件工程'),(9,'计算机组成原理',3,64,'计算机科学与技术'),(10,'计算机网络',3,64,'计算机科学与技术'),(11,'web开发',4,64,'软件工程');

/*Table structure for table `st_dorm` */

DROP TABLE IF EXISTS `st_dorm`;

CREATE TABLE `st_dorm` (
  `dormId` mediumint(9) NOT NULL AUTO_INCREMENT COMMENT '宿舍id',
  `dormNum` varchar(6) NOT NULL COMMENT '宿舍号',
  `dormAddress` varchar(20) NOT NULL COMMENT '宿舍地址号',
  PRIMARY KEY (`dormId`)
) ENGINE=MyISAM AUTO_INCREMENT=18 DEFAULT CHARSET=utf8;

/*Data for the table `st_dorm` */

insert  into `st_dorm`(`dormId`,`dormNum`,`dormAddress`) values (1,'640','兰五'),(2,'642','兰五'),(3,'643','兰五'),(4,'122','梅一'),(5,'123','梅一'),(6,'124','梅一'),(7,'435','竹三'),(8,'436','竹三'),(9,'437','竹三'),(10,'543','兰三'),(11,'542','兰三'),(12,'638','兰三'),(13,'541','兰二'),(14,'638','兰二'),(15,'633','兰二'),(17,'001','兰五');

/*Table structure for table `st_grade` */

DROP TABLE IF EXISTS `st_grade`;

CREATE TABLE `st_grade` (
  `stuNumber` varchar(20) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '学号',
  `couId` mediumint(9) NOT NULL COMMENT '课程号',
  `grade` smallint(6) NOT NULL COMMENT '成绩',
  `point` float(2,1) NOT NULL COMMENT '绩点',
  PRIMARY KEY (`stuNumber`,`couId`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;

/*Data for the table `st_grade` */

insert  into `st_grade`(`stuNumber`,`couId`,`grade`,`point`) values ('311909010412',1,89,3.9),('311909010412',2,81,3.1),('311909010412',3,79,2.9),('311909010412',11,67,1.7),('311907263218',7,60,1.0),('311909010412',6,68,1.8),('311909010418',1,84,3.4),('311909010418',2,82,3.2),('311909010418',3,91,4.1),('311909010418',4,94,4.4),('311909010418',5,63,1.3),('311909010412',8,81,3.1),('311909010417',1,78,2.8),('311909010417',2,74,2.4),('311909010417',3,86,3.6),('311909010417',4,91,4.1),('311909010417',8,89,3.9),('311909010417',6,60,1.0),('311354786297',1,78,2.8),('311354786297',2,71,2.1),('311354786297',3,64,1.4),('311354786297',4,96,4.6),('311354786297',5,76,2.6),('311909010412',7,79,2.9),('311907263218',1,67,1.7),('311907263218',2,69,1.9),('311907263218',3,74,2.4),('311907263218',4,78,2.8),('311909010417',7,60,1.0),('311907263218',6,74,2.4),('311907263218',8,93,4.3),('311909010418',9,67,1.7),('311909010418',10,83,3.3),('311354786297',9,95,4.5),('311354786297',10,89,3.9);

/*Table structure for table `st_login` */

DROP TABLE IF EXISTS `st_login`;

CREATE TABLE `st_login` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT 'id',
  `stuNumber` varchar(20) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '学号',
  `password` varchar(30) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '账户密码',
  PRIMARY KEY (`id`)
) ENGINE=MyISAM AUTO_INCREMENT=10 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;

/*Data for the table `st_login` */

insert  into `st_login`(`id`,`stuNumber`,`password`) values (1,'311909010418','123456'),(2,'diucd','123456'),(3,'嫡女','123456'),(4,'8的VG','123456'),(5,'对吧','123456'),(6,'刺骨','iucebwc'),(7,'李同学','123456'),(8,'311909010417','123'),(9,'311909010416','123456');

/*Table structure for table `st_name` */

DROP TABLE IF EXISTS `st_name`;

CREATE TABLE `st_name` (
  `name` varchar(20) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '姓名',
  `stuNumber` varchar(20) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '学号',
  `age` int(11) NOT NULL COMMENT '年龄',
  `stuId` mediumint(9) NOT NULL AUTO_INCREMENT COMMENT '学生id',
  `dormNumber` varchar(20) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '宿舍地址好',
  `sex` varchar(4) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '性别',
  `majorClass` varchar(20) CHARACTER SET utf8 COLLATE utf8_unicode_ci NOT NULL COMMENT '专业班级',
  `stuDay` datetime NOT NULL COMMENT '入学日期',
  `stuPic` varchar(100) CHARACTER SET utf8 COLLATE utf8_unicode_ci DEFAULT NULL COMMENT '头像图片',
  `major` varchar(30) CHARACTER SET utf8 COLLATE utf8_unicode_ci DEFAULT NULL COMMENT '专业全称',
  PRIMARY KEY (`stuId`)
) ENGINE=MyISAM AUTO_INCREMENT=63 DEFAULT CHARSET=utf8 COLLATE=utf8_unicode_ci;

/*Data for the table `st_name` */

insert  into `st_name`(`name`,`stuNumber`,`age`,`stuId`,`dormNumber`,`sex`,`majorClass`,`stuDay`,`stuPic`,`major`) values ('编辑','311909010412',23,1,'兰五555','男','软件1903','1999-06-17 16:00:00','94e19dea-1f82-4fd8-9b1b-fd80e616584c-1815.jfif','软件工程'),('李同学','311909010418',12,2,'兰五642','男','软件1903','2020-10-11 16:00:00','ed6715b7-b22f-4580-8872-4febd546bea1-2.jfif','计算机科学与技术'),('徐同学','311354786297',18,47,'梅园123','男','材料1802','2019-02-05 16:00:00','e4f37d25-4844-431e-9ca0-424120e329d4-OIP-C.jpg','计算机科学与技术'),('姜同学','311907263218',22,5,'梅园232','女','计科1906','1999-08-20 16:00:00','501203e0-3db1-4bac-a251-c27b08725831-1123.jpg','软件工程'),('伏虎','311909010417',23,55,'竹一642','女','软件1907','2021-09-04 16:00:00','e22028d3-340e-40b9-a70b-d3bc54355e14-1.jfif','软件工程');

/*Table structure for table `computer` */

DROP TABLE IF EXISTS `computer`;

/*!50001 DROP VIEW IF EXISTS `computer` */;
/*!50001 DROP TABLE IF EXISTS `computer` */;

/*!50001 CREATE TABLE  `computer`(
 `couId` mediumint(9) ,
 `couName` varchar(20) ,
 `couGrade` mediumint(9) ,
 `couTime` mediumint(9) 
)*/;

/*Table structure for table `ranks` */

DROP TABLE IF EXISTS `ranks`;

/*!50001 DROP VIEW IF EXISTS `ranks` */;
/*!50001 DROP TABLE IF EXISTS `ranks` */;

/*!50001 CREATE TABLE  `ranks`(
 `stuNumber` varchar(20) ,
 `name` varchar(20) ,
 `couName` varchar(20) ,
 `grade` smallint(6) ,
 `point` float(2,1) ,
 `ranks` bigint(21) unsigned 
)*/;

/*Table structure for table `score` */

DROP TABLE IF EXISTS `score`;

/*!50001 DROP VIEW IF EXISTS `score` */;
/*!50001 DROP TABLE IF EXISTS `score` */;

/*!50001 CREATE TABLE  `score`(
 `stuNumber` varchar(20) ,
 `couId` mediumint(9) ,
 `name` varchar(20) ,
 `couName` varchar(20) ,
 `grade` smallint(6) ,
 `point` float(2,1) ,
 `major` varchar(20) 
)*/;

/*Table structure for table `software` */

DROP TABLE IF EXISTS `software`;

/*!50001 DROP VIEW IF EXISTS `software` */;
/*!50001 DROP TABLE IF EXISTS `software` */;

/*!50001 CREATE TABLE  `software`(
 `couId` mediumint(9) ,
 `couName` varchar(20) ,
 `couGrade` mediumint(9) ,
 `couTime` mediumint(9) 
)*/;

/*View structure for view computer */

/*!50001 DROP TABLE IF EXISTS `computer` */;
/*!50001 DROP VIEW IF EXISTS `computer` */;

/*!50001 CREATE ALGORITHM=UNDEFINED DEFINER=`root`@`localhost` SQL SECURITY DEFINER VIEW `computer` AS select `st_course`.`couId` AS `couId`,`st_course`.`couName` AS `couName`,`st_course`.`couGrade` AS `couGrade`,`st_course`.`couTime` AS `couTime` from `st_course` where (`st_course`.`major` = '计算机科学与技术') WITH CASCADED CHECK OPTION */;

/*View structure for view ranks */

/*!50001 DROP TABLE IF EXISTS `ranks` */;
/*!50001 DROP VIEW IF EXISTS `ranks` */;

/*!50001 CREATE ALGORITHM=UNDEFINED DEFINER=`root`@`localhost` SQL SECURITY DEFINER VIEW `ranks` AS select `score`.`stuNumber` AS `stuNumber`,`score`.`name` AS `name`,`score`.`couName` AS `couName`,`score`.`grade` AS `grade`,`score`.`point` AS `point`,rank() OVER (PARTITION BY `score`.`couName` ORDER BY `score`.`grade` desc )  AS `ranks` from `score` */;

/*View structure for view score */

/*!50001 DROP TABLE IF EXISTS `score` */;
/*!50001 DROP VIEW IF EXISTS `score` */;

/*!50001 CREATE ALGORITHM=UNDEFINED DEFINER=`root`@`localhost` SQL SECURITY DEFINER VIEW `score` AS select `st_grade`.`stuNumber` AS `stuNumber`,`st_grade`.`couId` AS `couId`,`st_name`.`name` AS `name`,`st_course`.`couName` AS `couName`,`st_grade`.`grade` AS `grade`,`st_grade`.`point` AS `point`,`st_course`.`major` AS `major` from ((`st_course` join `st_name`) join `st_grade`) where ((`st_grade`.`stuNumber` = `st_name`.`stuNumber`) and (`st_grade`.`couId` = `st_course`.`couId`)) */;

/*View structure for view software */

/*!50001 DROP TABLE IF EXISTS `software` */;
/*!50001 DROP VIEW IF EXISTS `software` */;

/*!50001 CREATE ALGORITHM=UNDEFINED DEFINER=`root`@`localhost` SQL SECURITY DEFINER VIEW `software` AS select `st_course`.`couId` AS `couId`,`st_course`.`couName` AS `couName`,`st_course`.`couGrade` AS `couGrade`,`st_course`.`couTime` AS `couTime` from `st_course` where (`st_course`.`major` = '软件工程') WITH CASCADED CHECK OPTION */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;
…]()




设计实现与系统测试
## 1、设计目的

（1）熟悉基于SpringBoot 学生管理系统开发的基本过程。

（2）实现了注册用户邮箱认证功能。

（3）了解mybatis。会集成mybatis。使用mybatis查询数据和新增数据。

（4）认识Thymeleaf模板。在springboot中集成Thymeleaf。使用Thymeleaf。

（5）了解Springboot的日志文件以及配置错误页，拦截器等。

（6）实现Springboot 提供的文件上传功能。

### 1.1实现功能
（1）实现基本的增删改查功能。

（2）实现登录注册及邮箱认证功能

（3）共有以下数据库表：

 Login：用户登录表，随机生成邮件激活码
 
![image](https://github.com/lijiaa1/student-management-system/assets/114298041/dc312577-31e8-414b-947c-79990c085950)

 St_course：课程表
 
![image](https://github.com/lijiaa1/student-management-system/assets/114298041/0c454561-4c24-4805-bb7d-6c7d1572f1f3)

 St_drom：学生宿舍表
 
 ![image](https://github.com/lijiaa1/student-management-system/assets/114298041/fc79bb43-9c90-4f85-96fe-5387193071a0)

 St_grade：学生成绩表
 
![image](https://github.com/lijiaa1/student-management-system/assets/114298041/2724e9c4-7fc7-4d48-889e-3a7011ec5a3c)

 St_login：学生登录表
 
 ![image](https://github.com/lijiaa1/student-management-system/assets/114298041/97580f4c-5983-4fac-974b-87aad0956e47)

 St_name：学生登记表
 
 ![image](https://github.com/lijiaa1/student-management-system/assets/114298041/b2707e1e-5a2f-44ea-a1c5-167e1ff237d4)


## 2、设计背景
### 2.1需求分析
#### 2.1.1概述
随着社会的发展，人们生活水平的不断提高，物质文化的发展已经远远满足不了人们的需求，精神文明有了飞速的发展， 因此学校也更需要快速便捷的方法来管理学生。
#### 2.1.2开发环境
运行环境：推荐JDK 1.8；
开发工具：IDEA（推荐）、Eclipse、MyEclipse；
操作系统：windows 10 8G内存以上（其他windows以及macOS支持，但不推荐）；
数据库：MySQL5.6(推荐)及其他版本（支持）；
数据库可视化工具：Navicat Premium 15（推荐）以及其他Navicat版本 
## 3、设计思路
根据学生信息管理系统的需求，该系统实施后，应达到以下目标。

（1）界面设计友好、美观，数据存储安全、可靠

（2） 查看功能，保证数据查询的灵活性。

（3） 提供用户登录的功能，保证系统的安全性。

（4） 提供灵活、方便的权限设置功能，使整个系统的管理分工明确。

（5） 系统要最大限度地实现易维护性和易操作性。 

## 4、总体设计
### 4.1模块设计
学生信息管理系统总体设计系统功能模块图如下：

 ![image](https://github.com/lijiaa1/demo/assets/114298041/edc8dfb1-89b9-4e18-881b-21d7460d4ed0)
 
 
图1  系统功能模块图


 ![image](https://github.com/lijiaa1/demo/assets/114298041/13bfbb49-089f-40af-ad90-71f3e367ba88)
 
 
图2  系统登录流程图


![image](https://github.com/lijiaa1/demo/assets/114298041/c523d498-d6a2-401b-9da3-5e433812709a)

图3  数据库E-R图

#### 4.1.1文件组成结构
为了直观地看到整个网站的文件包组成结构，下图将网站的组织结构已展示出来。
 ![image](https://github.com/lijiaa1/demo/assets/114298041/0bd7cefa-8a2e-422a-a1bc-f54b70b194c2)
 
图4  系统文件结构图
#### 4.1.2主要组件以及文件夹说明
DispatcherServlet	框架提供的前端控制器，它是整个 Spring MVC 流程控制中心，负责统一处理请求和响应，调用其他组件对用户请求进行处理。

HandlerMapping框架提供的处理器映射器，根据请求的 url、method 等信息查找相应的对象

Handler开发人员提供的后端处理器，它可以在 HandlerAdapter 的控制下，对具体的用户请求进行处理。

HandlerAdapter框架提供的处理器适配器，负责拿到Handler返回的结果

ModelAndView，然后将结果返回给前端控制器DispatcherServlet。

ViewResolver	框架提供的视图解析器，其职责是将从DispatcherServlet中拿到的ModelAndView对象进行解析，生成View对象返回给DispatcherServlet。

View开发人员提供的视图，它作用是将View对象渲染成页面，展示给用户。

Controller包 调用业务层

Service包 处理业务

Mapper包 数据库访问

Vo包 value object

### 解释：
Controller依赖service 获取传递过来的user，发送到service
Service 处理业务 有时需要调用数据库中的数据 依赖mapper 从数据库获取user，对比，返回true或false
Mapper 数据库访问 获得本地保存的user
Vo  （value object）  user对象----ok
## 5、详细设计
### 5.1用户信息管理页面
#### 5.1.1登录界面
 ![image](https://github.com/lijiaa1/demo/assets/114298041/892574fe-33c2-4079-8d47-221da63787bc)

#### 5.1.2注册界面
 ![image](https://github.com/lijiaa1/demo/assets/114298041/8bbd1de5-3828-4ba5-83f5-ae7f3ebfa9c0)

#### 5.1.3激活成功
![image](https://github.com/lijiaa1/student-management-system/assets/114298041/9a5d3c95-8f5c-4212-b178-df3669dc3ec1)


    
### 5.2学生信息管理页面
#### 5.2.1学生信息
 
 ![image](https://github.com/lijiaa1/demo/assets/114298041/ea9150e0-5cef-487d-86c4-05439a5130ee)

#### 5.2.2宿舍信息
 ![image](https://github.com/lijiaa1/demo/assets/114298041/55c0a228-3659-47bc-aff9-df10ea51a2ae)



### 5.3课程信息管理页面
#### 5.3.1课程管理
 ![image](https://github.com/lijiaa1/demo/assets/114298041/54681100-0d2c-4d6d-9acd-194cb1de9746)

#### 5.3.2选课信息
 
![image](https://github.com/lijiaa1/demo/assets/114298041/23dd87e7-8985-4ba7-a623-f408bc808ff1)


### 5.4成绩信息管理页面
#### 5.4.1学科排名
 ![image](https://github.com/lijiaa1/demo/assets/114298041/bed25c23-ce31-40c2-b3ff-5021dac5e016)

#### 5.4.2学生个人成绩信息
 ![image](https://github.com/lijiaa1/demo/assets/114298041/100cdec8-2858-4b5e-a7e8-e18e0861a086)

#### 5.4.3专业绩点排名
![image](https://github.com/lijiaa1/demo/assets/114298041/995fbfa0-468d-4d42-8780-c56ff5238747)
