---
layout: post
#标题配置
title:  前端工程化第3篇--browser-sync插件与gulp的简单配合使用
#时间配置
date:   2018-06-01 15:30:00 +0800
#大类配置
categories: 技术人生
#小类配置
tag: 前端工程化
---

* content
{:toc}


>Browser-sync插件能让浏览器实时、快速响应您的文件更改并自动刷新页面。  
>gulp用自动化构建工具增强你的工作流程,使用它，我们主要是为了进行css或者js的压缩或者打包等工作

### gulp的安装
#### 全局安装
~~~
npm install -g gulp
~~~

#### 局部安装
~~~
npm install --save-dev gulp
~~~

### browser-sync与gulp的配合使用
#### 安装插件
~~~
npm install --save-dev gulp
npm install --save-dev browser-sync
npm install --save-dev gulp-sass
~~~

#### 编写脚本(gulpfile.js)  

~~~
// 加载插件
var gulp        = require('gulp');
var browserSync = require('browser-sync').create();
var sass        = require('gulp-sass');
var reload      = browserSync.reload;
// 定义文件路径
var src = {
    scss: 'app/scss/*.scss',
    css:  'app/css',
    html: 'app/*.html'
};
// 监视静态资源
gulp.task('serve', ['sass'], function() {

    browserSync.init({
        server: "./app"
    });
    gulp.watch(src.scss, ['sass']);
    gulp.watch(src.html).on('change', reload);
});
// 编写sass文件转换的任何
gulp.task('sass', function() {
    return gulp.src(src.scss)
        .pipe(sass().on('error', sass.logError))
        .pipe(gulp.dest(src.css))
        .pipe(reload({stream: true}));
});
// 启动后，执行默认的serve任务
gulp.task('default', ['serve']);
~~~
>解析： 脚本中监测sass文件，发现sass文件改动，会自动生成对应的css文件，并自动刷新页面  
> 项目目录下的任意html文件改变，也会自动刷新  

#### 添加运行脚本到package.json文件
~~~
"script" : {
  "start": "gulp"
}
~~~
>解析: 运行"npm run start"命令启动gulp
