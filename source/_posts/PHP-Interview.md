---
title: 2018春招PHP面试总结
date: 2018-04-20 15:44:06
tags: PHP,Interview
---

这次的面试，不仅仅希望能开启一个新的征程，了解世界，也是一个发现自身不足的一个过程，借由此确定将来的发展（学习）方向。<!-- more -->

## 面试准备
[一份能让面试官了解你的简历](https://www.zhihu.com/question/21187514/answer/147065558)，一份对于自己的自信，就出发吧
![Mind-map](https://raw.githubusercontent.com/areirei/fileStore/master/pic/php-interview-map.png)
## PHP
php是世界上最好的语言！
#### 基础
1. [session和cookie的区别](https://www.zhihu.com/question/19786827)
```
    Session是在服务端保存的一个数据结构，用来跟踪用户的状态，这个数据可以保存在集群、数据库、文件中

    Cookie是客户端保存用户信息的一种机制，用来记录用户的一些信息，也是实现Session的一种方式。
```
1. [PHP7](https://blog.csdn.net/u011957758/article/details/73320083)用了吗，了解哪些新特性
```
    PHP7在性能方面实现跨越式的提升，新的操作符，统一变量语法等等

    参考[PHP7的文章](https://blog.csdn.net/u011957758/article/details/73320083)
```
1. [魔术变量](http://php.net/manual/zh/language.constants.predefined.php)
```
    问了__dir__代表的含意,这个是回答文件所在的目录

    参考[PHP 手册之魔术常量](http://php.net/manual/zh/language.constants.predefined.php)
```
1. [魔术方法](http://www.php.net/manual/zh/language.oop5.magic.php)
```
    这算是经常会问到的一个题目了，常用的都记得，忽然问到__invoke()就懵了
    __construct()， __destruct()， __call()， __callStatic()， __get()， __set()， __isset()， __unset()， __sleep()， __wakeup()， __toString()， __invoke()， __set_state()， __clone() 和 __debugInfo() 

    参考[PHP 手册之魔术方法](http://www.php.net/manual/zh/language.oop5.magic.php)
```

#### 数据结构和算法
1. [栈数据结构](http://www.jb51.net/article/130272.htm)
```
    只要能用代码实现出栈数据结构即可

    参考[栈数据结构文章](http://www.jb51.net/article/130272.htm)
```
2. [冒泡排序](http://www.jb51.net/article/24497.htm)
```
    只要能用代码实现出冒泡排序即可

    参考[冒泡排序文章](http://www.jb51.net/article/24497.htm)
```
3. [完全二叉树和满二叉树的区别](https://blog.csdn.net/HaoDaWang/article/details/78065162)
```
    只有最下面的两层结点度能够小于2，并且最下面一层的结点都集中在该层最左边的若干位置的二叉树才为完全二叉树
    而一棵深度为h且有 2^h-1个结点的二叉树即为满二叉树

    参考[完美二叉树, 完全二叉树和完满二叉树](https://blog.csdn.net/HaoDaWang/article/details/78065162)
```

#### 架构相关
1. [Laravel和ThinkPHP有什么区别，对于laravel有什么要吐槽的](https://blog.csdn.net/qq1690194137/article/details/79794944)
```
    我从路由，中间件到控制器，数据访问,视图等层面上介绍了不同
    吐槽的话可能相对于一些项目，laravel有点‘重’

    参考[tp3.2和tp5,以及laravel的区别](https://blog.csdn.net/qq1690194137/article/details/79794944)
```
2. [有用composer发布过自己的包吗](基于 Composer 的 PHP 模块化开发)
```
    我回答没有，只是了解过
    面试官就说他们的框架是自己在Discuz的基础上二次开发的框架，在他优秀的基础上把composer依赖管理也都引进blabla

    参考[基于 Composer 的 PHP 模块化开发](https://zhuanlan.zhihu.com/p/27943241)
```
3. [谈谈对于MVC的理解](https://baike.sogou.com/v25227.htm)
```
    结合项目说明模板，视图，控制器之间的关系和基本的构成

    参考[MVC](https://baike.sogou.com/v25227.htm)
```

#### 防护
1. XSS 跨站脚本攻击
2. DDOS 流量攻击
3. CSRF 跨站请求伪造攻击
4. SQL注入
```
    在前端表单用户输入进行控制或限制
    有后端传参数和数据时进行过滤等等

    参考[常见的 CSRF、XSS、sql注入、DDOS流量攻击](https://blog.csdn.net/echo_laodong/article/details/79254552)
```

#### 项目
1. 在项目中如何解决并发的问题
```
    我的解决办法先是前端控制有效请求，例如一分钟才正常请求一次
    接着后端同样过虑无效请求，接着接操作放进队列中实现

    有个面试官问，你这个队列是阻塞的吗，如果真的同时两个用户购买，两个用户等待完成，他们还是用同一个线程完成，有没有考虑用其它方式实现
    我说无，他就说可以用锁的机制，第二个等待第一个完成，一个接一个

    参考[php高并发解决的一点思路](https://blog.csdn.net/mkbug/article/details/71455725)
    相关的还有swoole扩展,可以了解下
```
2. 微信支付具体实现流程
```
    1. H5页面发起支付请求，请求生成支付订单
    2. 调用统一下单API，生成预付单
    3. 生成JSAPI页面调用的支付参数并签名
    4. 微信浏览器自动调起支付JSAPI接口支付
    5. 确认支付
    6. 异步通知商户支付结果，商户收到通知返回确认信息
    7. 返回支付结果,展示支付信息给用户

    参考[微信支付时序图](https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=7_4)
```
3. 简单实现登录注册功能
```
    各个框架考虑的方面不一样，这就按自己的理解写出相应的代码就好
```
4. 如何设计一个商城
```
    我是先给自己限定了一个B2C的商城，然后从数据表开始，接着简单介绍前端和后端实现逻辑

    参考[PHP网上商城网站的设计与实现](http://www.docin.com/p-190062065.html)
```

## MYSQL
mysql优化基本是重中之重了，尤其考验技术
#### 基础
1. [InnoDB和MyISAM有什么区别](https://blog.csdn.net/xifeijian/article/details/20316775)
```
    InnoDB提供事务处理，行级锁，支持外键，支持多种行格式
    MyISAM只支持表级锁，全文索引，堆表

    参考[MyISAM与InnoDB区别](https://blog.csdn.net/xifeijian/article/details/20316775)
```
2. 事务有哪几个特性
```
    原子性、一致性、隔离性、持久性
```
3. 事务的隔离级别
```
    未提交读、已提交读、可重复读、可串行化

    参考[Innodb中的事务隔离级别和锁的关系](https://tech.meituan.com/innodb-lock.html)
```
4. 有个表字段的O_Id，OrderDate，OrderPrice，Customer这几个，我们希望查找订单总金额少于 2000 的客户
```
    SELECT Customer,SUM(OrderPrice) FROM Orders
    GROUP BY Customer
    HAVING SUM(OrderPrice)<2000
```
5. 查询学生表的数据，大于六十的为及格，反之不及格
```
    select 分数,类别=Case
    WHEN 分数>=60 THEN '及格'
    ELSE '不及格'
    END
    from 成绩表
```
6. 查询没有学完所有课程的学生学号、姓名
```
    SELECT a.SNO ,a.SNAME  
    FROM student a  
    WHERE a.`SNO` NOT IN  
        ( SELECT b.`SNO` FROM SC b  
        GROUP BY b.`SNO` HAVING COUNT(*) =  
            ( SELECT COUNT(*)  FROM course)
        );  
```
#### 优化
1. "select * from student where name='red'","select * from student where name='blue'"，优化语句
```
    select name from student where name='red'
    union
    select name from student where name='blue'

    如果用or条件, myisam表能用到索引， innodb不行。 
    innodb用UNION替换OR (适用于索引列) 
```
2. 你一般都会怎么优化数据库
```
    查询缓存、EXPLAIN、(联合)索引、使用固定长度静态表
    
    这问题都能写一本书了,参考[MySQL性能优化的最佳21条经验](https://blog.csdn.net/kaka1121/article/details/53395587)
```

## 服务器
#### 防护
服务器怎么做防护
```
    仅开放有限端口，限制登录IP，限制登录帐号

    也是可以定一本书的问题，可以根据项目回答，参考[服务器防护知识点汇总](https://blog.csdn.net/Sasoritattoo/article/details/9324149)
```
#### 协议
Get和Post有什么区别
```
    Get的参数包含在URL，GET请求会被浏览器主动cache，是url编码，有字符限制参数为ASCII字符
    Post 通过request body传递参数,且有多种编码方式
```
#### NginX
设置nginx时php脚本请求是让什么处理
```
    默认配置的是转发到FastCGI处理
```
#### Redis
1. 你用redis来缓存什么数据
```
    跟据项目来说自己缓存的一些经常要用到的数据
```
2. Redis怎么做持久化，配置哪种刷新频率
```
    配置aof持久化，用默认的每秒刷新aof文件

    参考[redis 的两种持久化方式及原理](https://blog.csdn.net/yinxiangbing/article/details/48627997)
```
3. Redis是多线程吗
```
    单线程（我竟然回答是多线程，233）

    参考[Redis单进程](http://www.cnblogs.com/syyong/p/6231326.html)
```
4. Redis怎么配置一主多从，要多久
```
    可以用Redis官方集群方案，具体没有实践过，可能要花几周时间来完成

    参考[Redis集群方案](https://www.zhihu.com/question/21419897)
```
#### 代码管理
有用过git吗？当两个人提交了错误代码后，怎么解决
```
    用过git提交代码，发生这种情况可以先将远程的代码git pull到本地，然后将冲突的代码或Git标记内容修改正确，然后重新提交代码

    参考[git使用经验](https://zhuanlan.zhihu.com/p/22666153)
```
## 其它
#### 为什么离职
```
    机智回答,稍微提了一下公司或自身的事<del>钱少事多家远</del>
```
#### 你理想的团队
```
    对技术热情，积极解决问题，共同合作

    参考[某种理想的团队](https://zhuanlan.zhihu.com/p/19968752)
```
#### 职业规划
```
    前端深入，后端深入，数据优化分析采集，服务器渗透blabla
```
#### 想问的问题
```
    一般都会问公司有什么项目，技术架构，有无盈利等
```

<div class="tip">不同公司技术栈不同，关心的点也不同，有点就会在队列的问题上问具体阻塞时的解决方案，有的更多关注项目效率，有的还会关注服务器搭建，有无自己搭建框架和对于流行框架的了解，过程中也许就能找到自己想要的发展方向</div>

## 后记
5天9家7offer，感觉还行，面试时大多公司都会根据简历上的项目进行详细的提问，.
面试时能看出技术上的广度（经历项目或技能多少），和技术的深度（数据优化，框架理解制作，服务器攻防渗透），希望大家也能够随着项目的发展，不断实践学习技术,就酱。
    \\(•ㅂ•)/♥  共勉~
