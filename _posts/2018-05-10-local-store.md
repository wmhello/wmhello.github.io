---
layout: post
#标题配置
title:  数据存储(localStorage)的使用
#时间配置
date:   2018-05-10 16:00:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: vue.js
---

* content
{:toc}


### 综述

在项目中，存储数据到本地浏览器，主要用于购物车、跨页面信息存储等

>名称：store
>
>用途：存储数据到本地浏览器
>
>大小: 2.6kb
>
>官网：[地址](https://github.com/marcuswestin/store.js)
>
>github:[地址](https://github.com/marcuswestin/store.js)

### 安装

#### npm安装
~~~
npm install store -save
~~~

#### 浏览器安装
~~~
<script src="path/to/my/store.legacy.min.js"></script>
~~~

#### cdn

~~~
<script src="https://cdn.bootcss.com/store.js/1.3.20/store.min.js"></script>
~~~

### API

~~~
// 存储变量到user键
store.set('user', { name:'Marcus' })

//获取内容
store.get('user')

// 删除键
store.remove('user')

// 清除所有的键
store.clearAll()

// 循环显示所有的键值对
store.eachEach(function(key, value) {
	console.log(key, '==', value)
})
~~~
