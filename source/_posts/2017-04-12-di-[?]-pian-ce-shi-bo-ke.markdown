---
layout: post
title: "第一篇博客 - 使用 Octopress+GitHub Pages 搭建个人博客"
date: 2017-04-12 14:56:02 +0800
comments: true
categories: 
---


网上很多教程，可以自行搜索，下面是我的操作流程以及中途遇到的坑。
- 首先安装ruby，如果有需要更新ruby版本

![octopress](http://upload-images.jianshu.io/upload_images/2310905-fbdbeec46a229e3c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 如果没有rbenv，也可以安装，后面我安装的是RVM

![bundle](http://upload-images.jianshu.io/upload_images/2310905-c32e1758fe4f3d9c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![bundle install](http://upload-images.jianshu.io/upload_images/2310905-efd15245f8a97686.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![默认主题](http://upload-images.jianshu.io/upload_images/2310905-a4e7cb39052cb3c4.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 修改_config.yml文件，添加自己的信息

![_config.yml文件](http://upload-images.jianshu.io/upload_images/2310905-eccbd3676278917f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![修改后的文件](http://upload-images.jianshu.io/upload_images/2310905-950a32359d418d15.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 设置url，和git remote add xxx用途类似，都是和远程仓库关联起来。

![设置url](http://upload-images.jianshu.io/upload_images/2310905-3bfabeca93ef21b3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 创建测试博客

![第一篇测试博客](http://upload-images.jianshu.io/upload_images/2310905-e58d746d32472489.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 发布测试博客（这里出现了坑）

![ranke deploy](http://upload-images.jianshu.io/upload_images/2310905-36546a36d010af5a.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![rejected](http://upload-images.jianshu.io/upload_images/2310905-2ddc1bf3d6ba287f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![refusing](http://upload-images.jianshu.io/upload_images/2310905-294421497b91a8be.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

- 原因与解决方法如下
> 我在Github新建一个仓库，写了License，然后把本地一个写了很久仓库上传。
先pull，因为两个仓库不同，发现refusing to merge unrelated histories，无法pull
因为他们是两个不同的项目，要把两个不同的项目合并，git需要添加一句代码，在git pull，这句代码是在git 2.9.2版本发生的，最新的版本需要添加--allow-unrelated-histories
假如我们的源是origin，分支是master，那么我们 需要这样写git pull origin master ----allow-unrelated-histories需要知道，我们的源可以是本地的路径


![pull成功](http://upload-images.jianshu.io/upload_images/2310905-21433b96ef2e7045.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![git status](http://upload-images.jianshu.io/upload_images/2310905-94807cd8370ad170.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

使用git diff命令查看提交的内容
![git diff](http://upload-images.jianshu.io/upload_images/2310905-52841a83e122f6e0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![错误提示](http://upload-images.jianshu.io/upload_images/2310905-097086c28d2ad346.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)
- 1.[上面错误的解决方法1](http://www.tuicool.com/articles/EFfUNb)
- 2.[解决方法2](https://sanwen8.cn/p/1f1O4TQ.html)
- 3.如果不行可以参考[解决方法3:使用rvm切换ruby版本](http://stackoverflow.com/questions/13778858/octopress-errors-rake-preview-watch-or-generate)
我是使用方法3解决的! 原因是ruby的版本没有更新。

![ruby版本](http://upload-images.jianshu.io/upload_images/2310905-7d540185d2486b61.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)


![rake watch](http://upload-images.jianshu.io/upload_images/2310905-bd6aac9e5be6edf8.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)

#### 优化博客的访问速度

- 1、删除或注释配置 _config.yml 文件中有关 Twitter 的部分。
- 2、修改 source/_includes/custom/head.html 文件，删除 google 的自定义字体。注意，如果使用注释的方式会造成最终生成出来的 HTML 页面的 body 部分也被注释。
- 3、修改 source/_includes/head.html 文件中 jquery.min.js 的链接地址。

![优化](http://upload-images.jianshu.io/upload_images/2310905-cbc5c071197fbfb3.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

最后，成功！
![成功](http://upload-images.jianshu.io/upload_images/2310905-5e3e6073e95ad3f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/620)



#### Reference
[参考链接](http://blog.csdn.net/caiqinghua0201/article/details/10371409）
       
