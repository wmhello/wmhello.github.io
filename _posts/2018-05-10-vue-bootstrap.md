---
layout: post
#标题配置
title:  bootstrap(vue.js版本)使用指南
#时间配置
date:   2018-05-10 16:10:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: vue.js
---

* content
{:toc}


### 综述

在项目中，创建bootstrap页面

>名称：uiv
>
>用途：构建bootstrap页面
>
>官网：[地址](https://uiv.wxsm.space/getting-started)
>
>github:[地址](https://github.com/wxsms/uiv)

### 注意事项
> 该库不依赖于jquery 但必须结合bootstrap.css才能使用

### 安装

#### npm安装
~~~
npm install uiv --save
~~~

#### 浏览器安装

必须下载源码来自己编译成为可以在浏览器使用的js插件(主要是本地化)

>1、下载源代码到本地(`git clone https://github.com/wxsms/uiv.git`)
>
>2、本地化（默认是英文，改为中文）
>
>修改src\local\index.js
>
>修改 import defaultLang from './lang/en-US' 的导入地址为'./lang/zh-CN'
>
>3、安装依赖
>
>先安装webpack（npm install webpack）
>
>再安装其他依赖(npm install)
>
>4、编译
>
>npm run dist:umd
>
>5、使用
>
>拷贝dist目录下的uiv.min.js即可以使用
