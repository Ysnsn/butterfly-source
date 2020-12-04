---
title: jsdelivr的正确使用方法
toc: false
top: false
tags: jsdelivr
categories: 食用教程
cover: 'https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/11120200821181132.jpg'
description: 'jsDelivr是一个比较好的CDN平台，官方号称jsDelivr – Open Source CDN free, fast, and reliable'
abbrlink: GitHub-jsdelivr
date: 2020-08-21 18:08:29
---
## 前言




> CDN的全称是Content Delivery Network，即内容分发网络。CDN是构建在网络之上的内容分发网络，依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。CDN的关键技术主要有内容存储和分发技术。——百度百科

> 放在Github的资源在国内加载速度比较慢，因此需要使用CDN加速来优化网站打开速度，jsDelivr + Github便是免费且好用的CDN，非常适合博客网站使用。

## 食用方法

1. 新建Github仓库
2. 上传资源（图片）
3. 使用jsdelivr直接访问仓库里的图片连接如下
   ```
   https://cdn.jsdelivr.net/gh/GitHub用户名/新建的仓库名/**图片**.jpg
   ```
4. 完事，图床做好了
## 发现问题
1. 当你的release包大于50MB，那么jsdelivr会给你报错并且不给你提供加速服务，例如下面这条链接
   https://cdn.jsdelivr.net/gh/Ysnsn/picture/111/03613.jpg
   打开就会出现
   ```
   Package size exceeded the configured limit of 50 MB
   ```
2. 感觉上面的使用方法有点复杂, 

## 解决方法
一. 当你的release版本号写为master时，只需要第一次发布release即可，后面直接用master分支的文件，也没有50MB的文件包大小限制按照官方的格式，就是

```
https://cdn.jsdelivr.net/gh/<username>/<repo-name>@<version>/<path>
```

例如，下面就可以访问了
```
https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/111/03613.jpg
```
1. 打开你的图床仓库，选择creat a new release
![](https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/11120200821183855.png)
2. 按照下图填写1处填写 **master** 不要写错，2处可不写 3处填写描述（随便）最后点击绿色方框提交
![](https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/11120200821183843.png)
3. 问题解决（此时就能访问  https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/111/03613.jpg  ）

二. 通过picgo配合GitHub 来使图片快速上传，配置picgo如下
![](https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/11120200821185814.png)
token获取路径
![](https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/11120200821190108.png)
下面的小方格可以全部选上（如果不知道是啥意思时）
![](https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/11120200821190239.png)
![](https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/111/20200822083609.png)

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>
<video id="video" preload loop style="height: 100%;width: 100%;object-fit: cover;">
</video>
<script>
  var video = document.getElementById('video');
  var videoSrc = 'https://cdn.jsdelivr.net/gh/Ysnsn/video-cdn/002.m3u8';
  if (Hls.isSupported()) {
    var hls = new Hls();
    hls.loadSource(videoSrc);
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED, function() {
      video.play();
    });
  }
</script>