---
title: butterfly重装所需
top: false
tags: butterfly
categories: 重新来过
cover: 'https://cdn.jsdelivr.net/gh/Ysnsn/picture/img/20200817225708.jpg'
description: 重装主题步骤及所需插件
abbrlink: 58458
date: 2020-08-19 16:45:03
---


### 主要步骤

>配置 Git 本地代理
<details>
<summary>点击展开👉 Git本地代理</summary>

Git 同时支持 Socket5 和 HTTP 代理，根据本地客户端具体情况选择一种配置就可以了

#### Socket5 代理
Git 默认的 Socket5 代理应设置为：(其中 server 是服务器地址，*port*是代理端口)
````
git config --global http.proxy socks5://server:port
git config --global https.proxy socks5://server:port
````


本地服务器的 IPV4 地址就是：127.0.0.1，端口填上面 Clash 中的 Socket5 代理端口

以我的本地代理端口为例，在 Git bash/Windows 终端下输入下面命令回车
````
$ git config --global http.proxy socks5://127.0.0.1:7891
$ git config --global https.proxy socks5://127.0.0.1:7891

````
Socket5 代理设置完成

#### HTTP 代理
Git 默认的 HTTP 代理应设置为：(其中 server 是服务器地址，port是代理端口)
````
$ git config --global http.proxy http://server:port
$ git config --global https.proxy http://server:port
````
本地服务器的 IPV4 地址就是：127.0.0.1，端口填上面 Clash 中的 HTTP 代理端口

以我的本地代理端口为例，在 Git bash/Windows 终端下输入下面命令回车
````
$ git config --global http.proxy http://127.0.0.1:7890
$ git config --global https.proxy https://127.0.0.1:7890

````
</details>


1. ✅Git 和 Node.js 的正确安装后你就可以在本地安装 Hexo 了，😉以下命令均在 Git Bash 里面进行。

2. 全局安装Hexo（半墙状态，需要代理&安装淘宝镜像cnpm）

   ```
   npm install -g cnpm --registry=https://registry.npm.taobao.org
   
   npm install -g hexo-cli 
   ```

3. 初始化`Hexo`{新建的博客文件夹下进行，如：`hexo`}

   ```
   hexo init hexo
   ```

4. 在 hexo 目录内右键打开 Git Bash，使用 NPM 安装必须的依赖：

   ```
   npm install
   ```

5. 关联 **USERname.github.io**仓库 、、

   ```
   git config --global user.name "username" # username是你的Github用户名，注意大小写保持一致
   
   git config --global user.email "your email address" # your email address填写你的Github注册用的邮箱
   
   ssh-keygen -t rsa -C "your email address"  # 生成SSH公钥，your email address同上填
   
   ```
   
   ```
ssh -T git@github.com
   ```
   
   此部分只是大致说明，具体请查看[官方文档](https://hexo.io/zh-cn/docs/)----(太懒了不想写了😪)

### 必须插件（自用）

1. Hexo主题下载如：butterfly

   ```
   git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
   ```

2. 主题渲染插件

   ```
   npm install hexo-renderer-pug hexo-renderer-stylus --save
   ```

3. Git 推送插件

   ```
   npm install hexo-deployer-git --save
   ```

4. 音乐播放器插件

   ```
   npm install hexo-tag-aplayer --save
   ```

5. 哔哩哔哩追番页面生成插件 

   ```
   npm install hexo-bilibili-bangumi --save
   ```

6. RSS 生成插件

   ```
   npm install hexo-generator-feed --save
   ```

7. 文章置顶插件

   ```
   npm uninstall hexo-generator-index --save
   
   npm install hexo-generator-index-pin-top --save
   ```

8. 本地搜索插件

   ```
   npm install hexo-generator-search --save
   ```

9. 字数统计插件

   ```
   npm install hexo-wordcount --save
   ```

10. 永久链接生成插件

    ```
    npm install hexo-abbrlink --save
    ```

11. 百度 Sitemap 生成插件

    ```
    npm install hexo-generator-baidu-sitemap@0.1.4 --save
    ```

12. 百度主动推送插件

    ```
    npm install hexo-baidu-url-submit --save
    ```

13. SiteMap 生成插件

    ```
    npm install hexo-generator-sitemap --save
    ```

### 最后

- 配置文件应加入以下内容

```
# RSS订阅支持
plugin:
- hexo-generator-feed

# Feed Atom
feed:
type: atom
path: atom.xml
limit: 20

abbrlink: 
    alg: crc16 #算法： 
    crc16(default) and crc32 rep: hex #进制： dec(default) and hex: dec #输出进制：十进制和十六进制，默认为10进制。丨dec为十进制，hex为十六进制
    

bangumi:
  enable: true
  path: bangumis/index.html
  vmid: 483622363
  title: '追番列表👀'
  quote: '生命不息，追番不止！🛴'
  show: 1
  loading:
  metaColor:
  color: "#ffc0cb"
  webp:
  progress: true
  
# 谷歌、百度站点地图生成
Plugins:
- hexo-generator-baidu-sitemap
- hexo-generator-sitemap

baidusitemap:
    path: baidusitemap.xml
sitemap:
    path: sitemap.xml
```

### 美化代码js css分享

1. 微博图片显示

   ```
   <meta name="referrer" content="no-referrer" />
   ```

2. 星星跟随鼠标

   ```
   <script src="https://cdn.jsdelivr.net/gh/sviptzk/HexoStaticFile@latest/Hexo/js/mouse_snow.min.js"></script>
   ```

3. comments-Valine博主代码修改

   ```
   https://cdn.jsdelivr.net/gh/HCLonely/Valine@latest/dist/Valine.min.js
   ```

4. 看板娘[把萌萌哒的看板娘抱回家 ](https://github.com/stevenjoezhang/live2d-widget)

   ```
   <script src="https://cdn.jsdelivr.net/gh/stevenjoezhang/live2d-widget@latest/autoload.js"></script>
   ```

5. 看板娘插件[传送门👉](https://github.com/fghrsh/live2d_demo)

6. 生成自己的sitemap文件
 ````
 npm install hexo-generator-sitemap --save
 npm install hexo-generator-baidu-sitemap --save
 ````


