---
layout: post
#标题配置
title:  vue.js提示框插件
#时间配置
date:   2018-05-10 15:30:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: vue.js
---

* content
{:toc}


### 综述
在项目中，代替浏览器原生的alert、confirm和prompt

 >名称：vuejs-dialog
 >
 >用途：简洁美观的对话框
 >
 >官网：[地址](https://godofbrowser.github.io/vuejs-dialog/)
 >
 >github:[地址](https://github.com/godofbrowser/vuejs-dialog)
 >

### 预览

![提示框]({{ '/styles/images/vue-dialog/alert.png' | prepend: site.baseurl}})

![确认框]({{ '/styles/images/vue-dialog/comfirm.png' | prepend: site.baseurl}})

#### 备注

> 基于promise，如果要在IE9上使用，请引入相关profill
>
~~~
<script src = "https://cdn.polyfill.io/v2/polyfill.min.js?features=es6"></script>
~~~

### 安装

#### npm安装
~~~
npm install vuejs-dialog
~~~

#### 浏览器
~~~
<script type="text/javascript" src="./path/to/vuejs-dialog.min.js"></script>
~~~

### 引入

#### 单页面
~~~
import Vue from "vue"
import VuejsDialog from "vuejs-dialog"

Vue.use(VuejsDialog)
~~~

#### 浏览器
~~~
<script type="text/javascript" src="./path/to/vue.min.js"></script>
<script type="text/javascript" src="./path/to/vuejs-dialog.min.js"></script>
<script>
Vue.use(VuejsDialog.default)
</script>
~~~

### API

#### confirm对话框
~~~
this.$dialog.confirm('Please confirm to continue')
	.then(function () {
      // 点击确定执行
		console.log('Clicked on proceed')
	})
	.catch(function () {
      // 点击取消执行
		console.log('Clicked on cancel')
	});
~~~

#### alert对话框
~~~
this.$dialog.alert('Please confirm to continue')
	.then(function () {
      // 点击确定执行
		console.log('Clicked on proceed')
	})
~~~

### 选项

~~~
let options = {
    html: false, // 内容可以包含html标记
    loader: false, // 显示载入动画
    reverse: false, // 按钮左右反转
    okText: 'Continue',  // 本地化确认按钮文字提示内容
    cancelText: 'Close',  //本地化关闭按钮文字提示内容
    animation: 'zoom', // 动画方式， 三选一: "zoom", "bounce", "fade"
    type: 'basic', // 确认类型，点击确认（basic）， 'soft'(软确认), 'hard'（硬确认)
    verification: 'continue', // 硬确认时, 作为确认文字，需要用户手工输入
    verificationHelp: 'Type "[+:verification]" below to confirm', // 硬确认时，提示用户输入的文字
    clicksCount: 3, // 软确认时，点击几次确认按钮完成最终的确认
    backdropClose: false // 点背景遮罩是否退出
};
~~~

### 技巧

### 本地化
~~~
message = '测试工作';
options = {
    okText: '确定',  // 本地化确认按钮文字提示内容
    cancelText: '取消',  //本地化关闭按钮文字提示内容
}
this.$dialog.alert(message, options);
~~~
![本地化对话框]({{ '/styles/images/vue-dialog/local.png' | prepend: site.baseurl}})


### 显示标题与内容
~~~
message = {
   title: '友情提示',
   body: '测试工作'
}
this.$dialog.alert(message);
~~~

![title]({{ '/styles/images/vue-dialog/title.png' | prepend: site.baseurl}})
