---
layout: post
#标题配置
title:  使用github发布服务自动部署应用
#时间配置
date:   2018-05-12 16:30:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: github
---

* content
{:toc}


### 整体流程

>1、在服务器上生成部署公钥
>
>2、在github上对项目做部署配置
>
>3、配置域名，初次拉取代码到服务器
>
>4、编写脚本，保存至服务器
>
>5、测试脚本，发布项目
>

### 需求
> 把github上的项目自动发布到指定的服务器，即自动部署

### 环境与设备说明
> 1、远程服务器一台（代码自动部署到此服务器）
>
> 2、github项目（我们的代码存到github）
>
> 3、开发计算机（本地开发）
>
> 4、域名管理
>

### 生成发布公钥
> 位置：服务器

1、在服务器上安装git，省略

2、git安装完毕后，在git的cmd窗口执行命令
~~~
ssh -keygen
~~~
后面直接回车，不要输入密码，这样使用公钥的时候就无需密码了

3、生成的公钥默认存放在用户目录下的.ssh目录，默认名称为id_ras和id_ras.pub,其中id_ras.pub为公钥文件，也就是要上传到github上的文件

### github项目配置
>位置: github

1、选择添加公钥
![添加公钥]({{'/styles/images/auto-deploy/1.jpg' | prepend: site.baseurl}})

2、进入添加公钥界面，填写标题和内容，标题随意，内容为第一步生成的公钥的内容，保存后添加成功
![填写页面]({{'/styles/images/auto-deploy/9.png' | prepend: site.baseurl}})
因为是危险操作，需要输入用户github的密码来确认
添加成功
![证书添加成功]({{'/styles/images/auto-deploy/12.png' | prepend: site.baseurl}})

3、配置webhook，填写自动部署所需要的脚本和secret
![新建webhook]({{'/styles/images/auto-deploy/8.png' | prepend: site.baseurl}})
详细设置
![webhook的详细设置]({{'/styles/images/auto-deploy/3.png' | prepend: site.baseurl}})
配置完成后，点击add webhook, github项目的配置即完成。
![webhook配置成功]({{'/styles/images/auto-deploy/7.png' | prepend: site.baseurl}})

### 配置域名，拉取代码到服务器
>位置：服务器

1、添加域名，指向服务器
![域名管理]({{'/styles/images/auto-deploy/11.png' | prepend: site.baseurl}})
2、在服务器上拉取项目
~~~
git clone https://github.com/wmhello/apidemo
~~~
3、本地web服务器配置后，域名指向项目（不同的框架可以按不同的要求来配置）
4、服务器代码部署成功后，通过域名可以访问网站
![ 服务器部署]({{'/styles/images/auto-deploy/4.png' | prepend: site.baseurl}})


### 编写脚本
>位置:服务器

  编写脚本，存放至配置webhook时指定的存放位置，并注意名称一定要相符
 ~~~
 <?php
// 与webhook配置相同，为了安全，请设置此参数
$secret = "wmhello";
// 项目路径
$path = "d:/www/apidemo";
// 校验发送位置，正确的情况下自动拉取代码，实现自动部署
$signature = $_SERVER['HTTP_X_HUB_SIGNATURE'];
if ($signature) {
  $hash = "sha1=".hash_hmac('sha1', file_get_contents("php://input"), $secret);
  if (strcmp($signature, $hash) == 0) {
    echo shell_exec("cd \ && cd {$path} && git pull 2>&1");
    exit();
  }
}
http_response_code(404);
?>
 ~~~

### 测试自动发布
>位置:开发机  服务器

在本地计算机增加代码后，提交到github仓库，代码自动同步到服务器，实现了自动发布的功能
