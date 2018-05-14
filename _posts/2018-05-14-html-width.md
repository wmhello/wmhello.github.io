---
layout: post
#标题配置
title:  DOM元素的宽高操作
#时间配置
date:   2018-05-14 23:05:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: javascript
---

* content
{:toc}


### DOM中元素的宽高(只读)

#### 页面宽高(整个页面)
~~~
document.documentElement.scrollWidth
document.documentElement.scrollHeight
~~~

#### 页面可视区域的宽高
~~~
document.documentElement.clientWidth
document.documentElement.clientHeight
~~~

#### 页面某个元素真实的宽高
~~~
document.getElementById('div1').offsetWidth
document.getElementById('div1').offsetHeight
~~~

#### 页面中某个元素真实的位置
~~~
document.getElementById("div").offsetLeft
document.getElementById("div").offsetTop
~~~
