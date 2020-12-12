---
title: 利用ffmpeg制作视频床
toc: false
top: false
date: 2020-12-04 23:09:26
tags:
     - jsdelivr
     - GitHub
     - m3u8
categories: 食用教程
cover: https://cdn.jsdelivr.net/gh/Ysnsn/img@latest/2020/12/04/2f5c7f8ae45dfbeeaa19d3b092045770.png
description: 相信很多人都用过图床，大部分都是利用 Jsdeliver 当图床，从而得到一个免费的图床，并且自带 CDN 加速, 但是有很多人想存储视频这么办呢？
abbrlink: jsdelivr-m3u8
---

## 正文
首先你得了解 Jsdeliver，他只加载 20MB 以内的资源，如果你的视频正好控制这一范围的话，你就可以使用默认的内容了
但是由于 Jsdeliver 对视频资源的解析不友好，所以我们就得对视频资源做一定的处理。

用过 QQ 浏览器的都知道下载网页上的视频下来都是 M3U8 的视频格式，即使你不下载，只是看视频都会产生 M3U8 文件和 TS 文件。

## 什么是 M3U8、TS 文件？

- M3U8
M3U8 是指 UTF-8 编码格式的 M3U 文件 (M3U 使用 Latin-1 字符集编码)

M3U 文件是一个记录索引的纯文本文件，打开它时播放软件并不会播放它

而是根据它的索引找到对应的音视频文件的网络地址进行在线播放

- TS
ts 是日本高清摄像机拍摄下进行的封装格式，全称为 MPEG2-TS。ts 即”Transport Stream” 的缩写。

将一个视频文件 (MP4) 切片分为很多个 TS 文件，一个 TS 文件的视频时常可以自定义，比如切片为 5 秒

那么其他 ts 文件也是 5 秒，但是这个不是完全准确，也就是说会有误差，会产生 4-7 秒左右的 ts 视频文件

那他是这么工作的呢？(以下图片是本地运行过程)
![](https://cdn.jsdelivr.net/gh/Ysnsn/img@latest/2020/12/04/5a2a2316a20c202fa03fe9b7c45da5d0.png)

## ffmpeg 工具
什么是 ffmpeg 在这里我就不再赘述了，感兴趣的可以自行搜索

了解了 M3U8 和 TS，我该怎么把视频切片呢？
使用 ffmpeg 工具进行切片

官网：https://ffmpeg.org/download.html

下载解压后打开 bin 目录，在里面找到 ffmpeg.exe 复制到自己新建的一个文件夹里，再把想要切片的视频 Copy 进来

## 视频切片
> 当前目录下有
> 00.mp4
> ffmpeg.exe
打开 cmd，cd 进入到刚刚新建的文件夹，关于怎么操作我就不多 bb 了
既然都用上 Github，用 Jsdeliver 加速了，你电脑里一定装了 Git 工具
在当前目录打开 *Git Bash* 命令行
(cmd 不需要 *./* )
- 将 mp4 转成 ts 格式，1 对 1，转换后视频质量与大小无变化。(执行下方代码得到 Lete.ts)
````
./ffmpeg.exe -y -i 00.mp4 -vcodec copy -acodec copy -vbsf h264_mp4toannexb 00.ts
````
按时间隔分片，1 对 N，下面的 5 即每个分片5秒，自行修改
-  *segment_list*  00.m3u8 为切片后得到的 m3u8 文件
-  *segment_time*  5 %03d.ts 为切片后得到的 ts 文件名 5 代表每个 ts 文件 5 秒播放时常 (有误差，不完全 5 秒)
````
./ffmpeg -i 00.ts -c copy -map 0 -f segment -segment_list 00.m3u8 -segment_time 5 00%03d.ts
````

这时你的文件了会有如下图文件
![](https://cdn.jsdelivr.net/gh/Ysnsn/img@latest/2020/12/04/743802bb2bc81b8411a36b4c673839f4.png)

那么将剩下的东西 *push* 到自己的仓库吧

> 现在访问是 m3u8 是不可以播放视频的 (会自动下载对吧)
> 访问文件也是不行的 (乱码对吧)

## HLS 技术
什么是 HLS 技术？

HLS (HTTP Live Streaming) 是 Apple 的动态码率自适应技术。主要用于 PC 和 Apple 终端的音视频服务。
包括一个 m3u (8) 的索引文件，TS 媒体分片文件和 key 加密串文件。(摘抄自百度百科)

CDN：https://cdn.jsdelivr.net/npm/hls.js

## 视频播放

| 属性 | 值 | 说明 |
| :--: | ---- | ---- |
| autoplay | autoplay | 如果出现该属性，则视频在就绪后马上播放 |
|   controls   |   controls   |   如果出现该属性，则向用户显示控件，比如播放按钮   |
|   height   |   pixels   |   设置视频播放器的高度   |
|   loop   |   loop   |   如果出现该属性，则当媒介文件完成播放后再次开始播放   |
|   muted   |   muted   |   规定视频的音频输出应该被静音.   |
|   poster   |   URL   |   规定视频下载时显示的图像，或者在用户点击播放按钮前显示的图像。   |
|   preload   |   preload   |   如果出现该属性，则视频在页面加载时进行加载，并预备播放。如果使用 “autoplay”，则忽略该属性。   |
|   src   |   url   |  要播放的视频的 URL    |
|    width  |   pixels   |    设置视频播放器的宽度  |

````
<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>
<video id="video" preload muted loop autoplay style="height: 100%;width: 100%;object-fit: cover;">
</video>
<script>
  var video = document.getElementById('video');
  var videoSrc = 'https://cdn.jsdelivr.net/gh/Ysnsn/video-cdn/003.m3u8';
  if (Hls.isSupported()) {
    var hls = new Hls();
    hls.loadSource(videoSrc);
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED, function() {
      video.play();
    });
  }
</script>
````

效果图

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>
<video id="video" preload muted loop autoplay style="height: 100%;width: 100%;object-fit: cover;">
</video>
<script>
  var video = document.getElementById('video');
  var videoSrc = 'https://cdn.jsdelivr.net/gh/Ysnsn/video-cdn/003.m3u8';
  if (Hls.isSupported()) {
    var hls = new Hls();
    hls.loadSource(videoSrc);
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED, function() {
      video.play();
    });
  }
</script>

> Lete  https://blog.lete114.top/article/Jsdeliver-video.html
