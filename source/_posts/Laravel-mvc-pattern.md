---
title: laravel大型架构的MVC分层
date: 2017-12-24 10:37:30
tags: laravel,mvc
desc: Laravel-mvc-pattern
---
小型架构的MVC分层
 - Model 数据层
 - View 视图层
 - Controller 控制层
<!-- more -->

原本将这些逻辑处理都放在了Model层，随着项目的不断发展，数据逻辑和业务逻辑越发复杂，有时会将第三方信息发送获取，Redis数据存储，不同model的调度都写在了同一个Model上，导致model在原本数据访问的基础上，承担了更多的责任，编写维护都不再优雅高效。

## 大型架构的MVC分层

![MVC分层](https://raw.githubusercontent.com/areirei/fileStore/master/pic/mvc_big.png)

1. Model      : 数据映射层
1. Repository : 将Model获取的数据封装成对像的集合并提供操作
1. Service    : 封装业务逻辑
1. Controller ：接收请求并调用Service
1. View       : HTML页面


Service调用Repository来获取数据，相互协调
1. 通过Repository将数据操作和数据访问从Model中分离
1. 通过Services处理复杂的业务逻辑
1. Controller可调度不同的Service

![MVC分层](https://raw.githubusercontent.com/areirei/fileStore/master/pic/file_interface.png)

### 最后
当你开始接受这种设定，会感觉到laravel式的优雅编程和其它优点
1. 数据访问逻辑集中处理（易于维护）
1. 业务和数据逻辑的完全分离（易于调试）
1. 减少重复代码
1. 降低程序出错的机率
1. 将来切近到其它的ORM也很容易（解耦对数据源的依赖）

### 参考链接
[Laravel 的中大型專案架構](http://oomusou.io/laravel/laravel-architecture/)