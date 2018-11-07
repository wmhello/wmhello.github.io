---
layout: post
#标题配置
title:  linux下手动安装nodejs
#时间配置
date:   2018-11-07 21:43:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: linux
---

* content
{:toc}

>版本：ubuntu server 16.04

>问题：直接使用apt-get安装后，发现指定的版本是v4.26，版本太低，需要手工下载后安装

### 步骤：

#### 1、下载node源码
~~~
sudo wget https://npm.taobao.org/mirrors/node/latest-v9.x/node-v9.11.1-linux-x64.tar.xz
~~~
#### 2、解压
~~~
tar -xJf node-v9.11.1-linux-x64.tar.xz
~~~
#### 3、移动到指定的目录
~~~
sudo mv node-v9.11.1-linux-x64 /opt/
~~~
#### 4、删除原来的链接
~~~
cd /usr/bin
sudo rm node
sudo rm npm
~~~
#### 5、安装npm和node命令到系统
~~~
sudo ln -s /opt/node-v9.11.1-linux-x64/bin/node /usr/bin/node
sudo ln -s /opt/node-v9.11.1-linux-x64/bin/npm /usr/bin/npm

~~~
