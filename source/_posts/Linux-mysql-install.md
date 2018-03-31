---
title: Linux安装mysql
date: 2018-03-26 14:54:22
tags: Linux,mysql
---

[Mysql](https://www.mysql.com/)是最流行的关系型数据库管理系统，在WEB应用方面MySQL是最好的**RDBMS**（Relational Database Management System：关系数据库管理系统）应用软件之一。尝试了一下在Linux上安装，意外地简单~<!-- more -->

## 下载安装
1. 下载前先看看[RPM软件包管理器](http://rpm.org/)里有没有安装过mysql
```
rmp -qa | grep mysql
```

2. 如果没有的话就可以开始安装mysql啦
```
yum install mysql
yum install mysql-server
yum install mysql-devel
```

3. 启动mysql
```
service mysqld start
```

4. 验证mysql正常
```
mysqladmin --version
```
5. 如果正常的话，会显示以下信息，相关系统信息会有所不同
```
mysqladmin  Ver 8.42 Distrib 5.6.39, for Linux on x86_64
```

<div class="tip">如果在下载的时候提示没有可用包，可以试着下载mysql的repo源`wget http://repo.mysql.com/mysql-community-release-el7-5.noarch.rpm `，并安装`rpm -ivh mysql-community-release-el7-5.noarch.rpm`,成功后再尝试一次</div>

## root用户

1. 首先，我们通过以下命令登录root到数据库
```
mysql -u root -p
```

2. 接着，我们看一下数据库
```
show databases;
```
3. 如果正常的话，将会显示成以下代码，其中mysql的内置数据库，存储了一些用户、权限、存储过程等数据。
```
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
+--------------------+
```

4. 其次，我们再用sql语句查询一下所有的用户
```
select host,user from mysql.user
```
5. 如果正常的话，将会显示以下代码
```
+-------------------+------+
| host              | user |
+-------------------+------+
| 127.0.0.1         | root |
| ::1               | root |
| localhost         |      |
| localhost         | root |
+-------------------+------+
```

6. 最后，用sql语句修改（创建）密码
```
update mysql.user set password=password('test') where user='root';
flush privileges;
```

## 最后
我在使用过程中，由于php和mysql都安装在了本地，这时laravel连接数据库时要用套接字通讯，这时大家可以在laravel的数据库配置中设置[unix_socket](https://en.wikipedia.org/wiki/Unix_domain_socket)的办法来解决问题，其它的话Linux不同版本代码可能会有所不同，如出错网上有相关解决办法,就酱。
 \\(•ㅂ•)/♥  共勉~

#### 参考链接
[mysql安装](http://www.runoob.com/mysql/mysql-install.html)
[yum install mysql-server没有可用包](https://www.cnblogs.com/yowamushi/p/8043054.html)
