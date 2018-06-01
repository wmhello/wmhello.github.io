---
layout: post
#标题配置
title:  前端工程化第2篇--browser-sync的安装与使用
#时间配置
date:   2018-06-01 15:00:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: 前端工程化
---

* content
{:toc}


> Browser-sync是一款能让浏览器实时、快速响应您的文件更改（html、js、css、sass、less等）并自动刷新页面的ndoejs插件，借助该插件，可以提升编码体验，提高开发效率。

### browser-sync的安装
~~~
npm install -g browser-sync
~~~

### browser-sync的使用例子
#### 静态网站的使用
~~~
browser-sync start --server --files "css/*.css, *.html, js/*.js"
~~~
>解析:项目css目录下任何css文件改动，js目录下的任何js文件改动和项目下任何html改动就自动刷新页面  

~~~
browser-sync start --server --files "**/*.css, **/*.html"
~~~

>解析: 项目下任意目录的css文件改动，任意目录的html文件改动都会自动刷新页面  

#### 动态网站的使用  
>如果开发环境有web服务器，我们可以配置成代理模式来使用  

~~~
browser-sync start --proxy "Browsersync.cn/home/index" "css/*.css"
~~~

>解析：项目css目录下的任何文件改动，就会自动刷新域名为“Browsersync.cn/home/index”的页面
