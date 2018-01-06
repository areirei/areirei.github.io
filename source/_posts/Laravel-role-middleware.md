---
title: laravel-中间件过虑权限
date: 2018-01-02 17:36:44
tags: laravel,role,middleware
desc: laravel,entrust,role,middleware
---
laravel有很多非常棒的权限管理包，平时都是用权限包的方法过虑权限，但在项目中，我发现用中间件的方法来过虑权限也很不错，也能解藕，今天用的是基于角色的权限管理[Entrust](https://github.com/Zizaco/entrust),关于相关的使用就不过多阐述了，其它还有类似[Laravel-permission](https://github.com/spatie/laravel-permission),[bouncer](https://github.com/JosephSilber/bouncer)等等都非常不错！<!-- more -->

## laravel 权限过虑
其实官方已经有现成的方式进行权限过虑，现在只是提供另一个方式实现权限过虑，laravel的请求在进入逻辑处理之前会通过http中间件进行处理，而我们在原有的基础上，新增一个中间件handle住这个事件
1. 新建中间件
![middleware_path](https://raw.githubusercontent.com/areirei/fileStore/master/pic/power_path.png)
2. 修改内容
![middleware_code](https://raw.githubusercontent.com/areirei/fileStore/master/pic/power_file.png)
3. 同时在`App\Http\Kernel.php`中加入门面
```
'power' => \App\Http\Middleware\Power::class,
```
4. 在路由中过虑
其中`uses`是注册路由时的参数，自动生成映射到控制器方法的uri,我们添加一个`permission`参数（参数名任意，中间件那里修改即可），用于路由过虑
```
Route::group(['middleware' => ['auth','power']], function () {
    Route::get('/user/list',['uses'=>'UserController@userLists','permission'=>'user-list']);
    //something...
});
```
<div class="tip">
原本的权限管理就有很多非常好的方法供调用，此文只是提供另一个思路做权限管理，希望能抛砖引玉，共勉
</div>