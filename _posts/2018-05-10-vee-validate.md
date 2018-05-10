---
layout: post
#标题配置
title:  vue.js表单验证插件的使用
#时间配置
date:   2018-05-10 12:30:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: vue.js
---

* content
{:toc}


### 综述
>名称：vee-validate
>
>用途：简单的 Vue.js 表单验证插件
>
>官网：[地址](http://vee-validate.logaretm.com/)
>
>github:[地址](https://github.com/baianat/vee-validate)

### 特别提示
>配合laravel使用特别好使  因为验证规则和laravel后端的验证规则一样
>
>插件既可以应用于SPA也可以应用于多页面，通用性强

![效果图]({{ '/styles/images/vee-validate/changPassword.jpg' | prepend: site.baseurl}})


### 安装
#### 单页安装
~~~
npm install vee-validate --save
~~~
#### 浏览器安装
~~~
  <!-- unpkg -->
  <script src="https://unpkg.com/vee-validate@2.0.0-rc.7"></script>
~~~

### 引入项目
#### 单页引入
~~~
import Vue from 'vue';
import VeeValidate from 'vee-validate';

Vue.use(VeeValidate);
~~~

#### 浏览器引入
~~~
  <script src="path/to/vue.js"></script>
 <script src="https://unpkg.com/vee-validate@2.0.0-rc.7"></script>
  <script>
    Vue.use(VeeValidate); // good to go.
  </script>
~~~

### 基础使用
~~~
<div class="column is-12">
    <label class="label" for="email">Email</label>
    <p :class="{ 'control': true }">
        <input v-validate="'required|email'" :class="{'input': true, 'is-danger': errors.has('email') }" name="email" type="text" placeholder="Email">
        <span v-show="errors.has('email')" class="help is-danger">{{ errors.first('email') }}</span>
    </p>
</div>
~~~
#### 代码解析
* * * * *
> v-validate="'required|email'"
> v-validate            是由该插件提供的指令 作用于html上
> "'required|email'"  字段验证的规则，注意双引号之内必须有单引号，多个规则之间用|连接
> errors.has('email')   判断emai字段值是否验证通过  email内容指向input的name属性 必须设置成一样  这意味着要用该插件，input上的name属性必须设置
> errors.first('email')  email字段验证不通过时显示相关联的提示信息
#### 验证规则
[地址](http://vee-validate.logaretm.com/validation.html#available-rules)

### 进一步学习
#### 本地化
    使用本地化功能可以让错误提示换成中文

##### 单页中使用

##### 浏览器中使用
~~~
var dict = {
 zh_CN: {
  messages: {
   required: function(field){
     return '请输入' + field ;
   },
   confirmed: function(field) {
     return '两次输入的密码不一致';
   }
 },
 attributes: {
   OldPassword: '旧密码',
   NewPassword: '新密码',
   ConfirmNewPassword: '确认密码',
 }
 }
};
VeeValidate.Validator.localize('zh_CN', dict.zh_CN);
Vue.use(VeeValidate);
var app = new Vue({
// 省略
});
~~~
##### 代码解析

* * * * *

> VeeValidate（浏览器引入js后建立了一个全局对象）
> dict  翻译的内容，其中attributes对象表示字段，messages对象表示提示信息
##### [本地化进一步参考](http://vee-validate.logaretm.com/localization.html#translation)

#### 常用方法
#####  出错渲染

字段验证不通过时渲染提示信息时使用

>errors.first('field') 显示字段field的第一个出错信息
>
>errors.collect('field') 显示字段field的所有出错信息
>
>errors.has('field') 判断fileds字段是否检验有误
>
>erros.all() 显示所有的出错信息
>
>errors.any() 判断是否有错误

#### 手动检验

常用于数据提交（写在vue的方法内部）
>this.$validator.validate('field');  校验单个字段
>
>this.$validator.validateAll();   表单整体校验
>

   代码片段
~~~
       this.$validator.validateAll().then(function(result) {
          if (result) {
           //成功操作
          } else {
           // 失败操作
          }
       })
~~~
##### 检验信息清除

常用于校验成功后清除错误的提示信息
> this.errors.clear();  

##### [API进一步学习](http://vee-validate.logaretm.com/api.html#directive)

### 参考文档
>官网:[地址](https://github.com/baianat/vee-validate)
> 
>他人项目: [Vue 全家桶 + 前端实现登录拦截、登出、校验、购物车等功能](https://github.com/G-Bruin/vue-vuex-VeeValidate-vueResource-github)
