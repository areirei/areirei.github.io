---
title: Laravel 小型架构的Model分层
date: 2017-12-14 13:58:45
tags: laravel,Eloquent
desc: laravel,model query scope
---

# Laravel 小型架构的MVC分层
在刚开始使用laravel的过程中，我们需要将代码分层
 - Model 数据层
 - View 视图层
 - Controller 控制层
<!-- more -->
在这个基础上我们在用控制层获取数据的时候，就可以用上Laravel的Eloquent中的本地作用域，将数据处理和业务逻辑都集中在Model层，让控制层只做调度的功能;

# Eloquent Query Scopes
首先在模型文件中新增一个方法
```
<?php

namespace App;

use Illuminate\Database\Eloquent\Model;

class User extends Model
{
    /**
     * Scope a query to only include popular users.
     *
     * @param \Illuminate\Database\Eloquent\Builder $query
     * @return \Illuminate\Database\Eloquent\Builder
     */
    public function scopePopular($query)
    {
        return $query->where('votes', '>', 100);
    }
```
<div class="tip">
    创建方法时名称前面一写要有**scope**，使用方法的时候就不用加上prefix了。
</div>
然后在控制器文件中这样使用
```
$users = App\User::popular()->active()->orderBy('created_at')->get();
```
这样，在获取数据的时候你就可以同时进行其它处理
当然，你也可以这样使用
```
 public function scopePopular($query,$data)
    {
        if(isset($data['id']){
            return $query->where('id',$data['id'])->update($data);
        }else{
            return $query->create($data);
        }
    }
```
通过传进来的第二个参数，进行其它业务或数据的处理，controller又可以重复使用方法，控制层也能只做基本控制。
<div class="tip">
    创建方法时的第一个参数必须是builder，其它参数则紧接其后添加即可。
</div>

More info: [query-scopes](https://laravel.com/docs/5.5/eloquent#query-scopes)