# 客户关系管理系统



## 系统功能



###  系统功能要求

1. 管理员与工作人员两种角色
2. 管理员:工作人员管理(增删改查)
3. 管理员与工作人员:客户资料维护(增删改查)，客户消费记录管
   理(增删改查)。
4. 用户：查询商品信息，购物

### 实际完成情况

- #### 主线任务完成情况

  1. 管理员与工作人员和客户三种角色
  2. 管理员:工作人员管理(增删改查)
  3. 工作人员:客户资料维护(增删改查)，商品信息维护（增删查改），查看用户购物情况

- #### 细节附加功能

  1. 完成登录注册界面
  2. 完成了用户界面分页功能
  3. 完成了登录拦截功能
  4. 完成了对于系统异常错误的处理

## 环境配置

环境：Java8，MySQL8，SpringBoot2.7.5，Mybatis-plus，Vue2，Element2，maven

环境搭建：直接引入pom的坐标依赖



## 程序使用

1. 用户：可以直接注册
2. 管理员：需要手动去数据库中添加人员
3. 工作人员：可以通过管理员界面添加



## 数据库表

**注意**：因为在shop订单表里创建了外键，运行sql语句时要最后创建shop表

User

```Sql
CREATE TABLE `user` (
  `id` int NOT NULL AUTO_INCREMENT,
  `username` varchar(255) CHARACTER SET utf8mb4 COLLATE utf8mb4_0900_ai_ci DEFAULT NULL,
  `sex` varchar(255) DEFAULT NULL,
  `phone` varchar(255) DEFAULT NULL,
  `address` varchar(255) DEFAULT NULL,
  `password` varchar(255) DEFAULT NULL,
  `identify` varchar(255) DEFAULT NULL,
  `deleted` varchar(255) NOT NULL DEFAULT '0',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

```

item

```sql
CREATE TABLE `item` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(255) DEFAULT NULL,
  `type` varchar(255) DEFAULT NULL,
  `remark` varchar(255) DEFAULT NULL,
  `deleted` int DEFAULT '0',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=5 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;

```



shop

```sql
CREATE TABLE `shop` (
  `id` int NOT NULL AUTO_INCREMENT,
  `user_id` int DEFAULT NULL,
  `item_id` int DEFAULT NULL,
  `create_time` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  KEY `user_id` (`user_id`),
  KEY `item_id` (`item_id`),
  CONSTRAINT `item_id` FOREIGN KEY (`item_id`) REFERENCES `item` (`id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `user_id` FOREIGN KEY (`user_id`) REFERENCES `user` (`id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB AUTO_INCREMENT=4 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;


```



## 系统界面截图

### 软件包结构图
![image](https://github.com/user-attachments/assets/14616c36-74bf-422f-94cf-48073009946d)



### 登录注册界面


![image](https://github.com/user-attachments/assets/ad102af1-1a8e-42a4-9420-deabd0a3aa57)



### 用户界面
![image](https://github.com/user-attachments/assets/036e84cc-034e-4501-a217-b4f4cc4ec223)



### 工作人员界面


### 管理员界面


