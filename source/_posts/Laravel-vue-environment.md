---
title: Laravel结合vue之项目内部署
date: 2018-03-20 17:09:02
tags: laravel,vue,environment,construction
desc: 本教程介绍在Laravel中部署vue
---

本教程介绍在Laravel中部署vue，在Laravel包含了一些基本脚手架，以便使用Vue库更容易开始编写现代JavaScript 。Vue为使用组件构建强大的JavaScript应用程序提供了富有表现力的API。我们可以使用Laravel Mix轻松地将JavaScript组件编译成一个可以浏览器的JavaScript文件。<!-- more -->

# 创建laravel
首先，你要有一个[composer](https://getcomposer.org/download/),然后，你便有了一个[laravel](https://laravel.com/docs/5.6)。
(运行命令`composer create-project --prefer-dist laravel/laravel blog`创建一个新的laravel项目)。

# Hello world!
1. 打开命令行，进入你的项目内`cd blog`
2. 在开始前，先下载项目默认依赖，由于各种你懂得原因，npm作为国外的node仓库安装工具，操作的时候可能会发生速度慢等各种问题，一般推荐用taobao源进行加速,下面代码同样加上后缀即可
```
npm install  --registry=https://registry.npm.taobao.org
```

3. 下载vue路由管理
```
npm install vue-router --save-dev
```

4. 在`/resources/assets/js/components`中新建一个`HelloComponent.vue`自定义组件文件。
```
<template>
    <div>
        <h1>Hello World!</h1>
    </div>
</template>

<script>
    export default{
        data(){
            return {

            }
        }
    }
</script>
```

5. 在`/resources/assets/js`下新建文件夹`router`,并在里面新建`hello.js`,并通过嵌套路由配置将`hello`路由映射到刚刚新创建的`HellowComponent`组件当中。
```
import Vue from 'vue'
import VueRouter from 'vue-router'
Vue.use(VueRouter)

export default new VueRouter({
    saveScrollPosition: true,
    routes: [
        {
            name: "hello",
            path: '/',
            component: resolve =>void(require(['../components/HelloComponent.vue'], resolve))
        },
    ]
})
```
6. 在当前laravel项目中`/resources/assets/js`下新建`hello.vue`,做为主界面，嵌套路由视图。
```
<template>
    <div>
        <h1>Hello</h1>
        <router-view></router-view>
    </div>
</template>

<script>
    export default{
        data(){
            return {

            }
        }
    }
</script>
```
7. 接着在`/resources/assets/js`下新建`hello.js`
```
require('./bootstrap');

window.Vue = require('vue');

import Vue from 'vue'
import App from './hello.vue'
import router from './router/hello.js'
const app = new Vue({
    el: '#app',
    router,
    render: h=>h(App)
});
```

8. 在`/resources/views`下新建`hello.blade.php `
```
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <meta name="csrf-token" content="{{ csrf_token() }}">
    <title>Hello</title>
</head>
<body>
    <div id="app"></div>
    <script src="{{ mix('js/manifest.js') }}"></script>
    <script src="{{ mix('js/vendor.js') }}"></script>
    <script src="{{ mix('js/hello.js') }}"></script>
</body>
</html>
```

9. 在`/resources/routes/web.php`中新增路由
```
Route::view('/hello','/hello');
```

10. 修改`webpack.mix.js`
```
mix.js('resources/assets/js/app.js', 'public/js')
   .js('resources/assets/js/hello.js', 'public/js')
   .extract(['vue', "vue-router", "axios"])
   .sass('resources/assets/sass/app.scss', 'public/css');
```

11. 保存后在命令行中本项目目录下执行`npm run watch`,进行重新编译

12. 可以在命令行中本项目目录下输入`php artisan serve`,访问`http://127.0.0.1:8000/hello`即可看到效果

<div class="tip">laravel5.5起新增了`Route::view`和`Route::redirect`方法，5.4及以下的路由可以写成这样`Route::get('/hello', function () {return view('hello');});`</div>

# 最后
有时候运行npm时会提示`Write EIO`错误，可能是因为编码的问题造成，这种时候可用管理员身份运行命令行文件，或者运行`chcp 850`设置活动代码页编号，介绍在laravel中部署vue的教程基本结束，如果您有兴趣了解更多关于编写Vue组件的信息,你可以阅读[Vue文档](https://vuejs.org/v2/guide/),就酱。
 \(•ㅂ•)/♥  共勉~