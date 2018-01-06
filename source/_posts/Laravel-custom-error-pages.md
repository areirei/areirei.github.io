---
title: Laravel-定制500错误页
date: 2017-09-11 21:54:50
tags: laravel,errors
desc: Laravel定制500错误页,Laravel-custom-error-pages
---
laravel中想要定义一个错误页面和调用错误页面很简单,在`resources/views/errors`文件夹中写入`404.blade.php`(请求错误代码+‘blade.php’)文件即可,因为在Laravel 5 中，所有异常处理都集中处理了，这是HTTP 异常的默认行为。<!-- more -->

## 500错误
唯独500错误，或者说其它不属于于正常请求错误代码类型的错误（例如代码错误）使用`resources/views/errors/500.blade.php`无效，在使用`$e->getStatusCode()`后依旧无法正常获取HTTP异常的解决办法就是在默认的异常处理中`app/Exceptions/Handler.php`
```    /**
     * 默认的异常处理方法
     *
     * @param  \Illuminate\Http\Request  $request
     * @param  \Exception  $e
     * @return \Illuminate\Http\Response
     */
    public function render($request, Exception $e)
    {
        if (!$this->isHttpException($e)) $e = new \Symfony\Component\HttpKernel\Exception\HttpException(500);
        return parent::render($request, $e);
    }
    ```

<div class="tip">
    ps:记得debug模式改成false  
</div>
希望这个方法对你也有用，就酱 (๑•̀ㅂ•́)و✧

## 参考链接
[Laravel Errors & Logging](https://laravel.com/docs/5.4/errors#render-method)
