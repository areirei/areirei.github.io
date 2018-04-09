---
title: Laravel-测试入门
date: 2018-04-09 10:13:54
tags: laravel,test,testing,phpunit,php
---

[Laravel](https://laravel.com/docs/5.6/testing)建立在考虑测试的基础上，其中工程化的一大特点就是可测试性。事实上，支持使用[PHPUnit](http://phpunit.readthedocs.io/zh_CN/latest/index.html)进行测试的功能已经包含在内，并且已经为您的应用程序设置了一个文件。该框架还附带了方便的帮助程序方法，使您能够表达测试您的应用程序。<!-- more -->
默认情况下，您的应用程序的`tests`目录包含两个目录：`Feature`和`Unit`。**单元测试**是关注代码中非常小的，孤立部分的测试。实际上，大多数单元测试可能只关注单一方法。**功能测试**可能会测试代码的大部分内容，包括几个对象如何相互交互，甚至是完整的HTTP请求到JSON端点。
<div class="tip">PHPUnit是最早和最知名的PHP单元测试包之一。它主要是为单元测试而设计的，这意味着尽可能在最小的组件上测试代码，但它也非常灵活，可以用于单元测试。</div>

## 创建和运行测试
要创建一个新的测试用例，请使用Artisan命令：`make:test`
```
// Create a test in the Feature directory...
php artisan make:test UserTest

// Create a test in the Unit directory...
php artisan make:test UserTest --unit
```

测试生成后，您可以像通常使用PHPUnit一样定义测试方法。
```
<?php

namespace Tests\Feature;

use Tests\TestCase;

class UserTest extends TestCase
{
    /**
     * A basic test example.
     */
    public function testExample()
    {
        //访问根路由时应该看到'Laravel 5'
        $this->visit('/')
            ->see('Laravel 5');
    }
}
```

要运行测试，请从终端执行命令：
```
phpunit
```

运行成功的话应该会显示如下：
```
PHPUnit 7.1.1 by Sebastian Bergmann and contributors.

...

Time: 103 ms, Memory: 12.75Mb

OK (2 tests, 3 assertions)
```

<div class="tip">假如在运行`phpunit`命令之时不成功，发现是没有命令的话可以在系统中添加全局（环境）变量或目录`./vendor/bin`，也有可能会发生phpUnit版本过低测试不成功，请留意</div>

## 结言

您应该注意到本教程中编写的测试中的一个共同主题：它们都非常简单。这是学习如何使用基本测试断言和帮助程序并尝试尽可能使用它们的好处之一。测试越简单，测试越容易理解和维护。
有兴趣的话您还可以在[PHPUnit 文档](http://phpunit.readthedocs.io/zh_CN/latest/index.html)中找到更多信息，就酱。
 \\(•ㅂ•)/♥  共勉~

#### 参考链接
[Laravel 测试入门](https://laravel.com/docs/5.6/testing)
[PHPUnit 文档](http://phpunit.readthedocs.io/zh_CN/latest/index.html)