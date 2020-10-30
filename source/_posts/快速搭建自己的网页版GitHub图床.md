---
title: 快速搭建自己的网页版GitHub图床（真香）
toc: true
top: false
tags:
  - GitHub
  - 虚拟主机
  - jsdelivr
categories: 食用教程
cover: 'https://cdn.jsdelivr.net/gh/Ysnsn/picture@master/111/20200822112522.jpg'
description: 因为本博客需要才找到这么一个简单稳定图床 jsdelivr+github
abbrlink: 40781
date: 2020-08-24 09:03:49
---
## 🥢前言
1. 由于本博客需要一个较稳定且快速的图床来存储自己的博客图片，所以才有了下面
2. 白嫖Github的存储空间，通过jsdelivr全球加速(含有国内节点)。实现图床的目的。
3. 白嫖Gitee的存储空间， 实现图床的目的。存储和访问节点都在国内，请在遵循国内相关法律的前提下使用。 文件在1M以上需要访客登录才能访问。1M以下，相当稳。

## 参考
1.  https://github.com/yumusb/autoPicCdn
2.  https://plushine.cn/38834.html

## 🍬准备工作
1. 脑子和手
2. 一个域名
3. 一台虚拟主机（国外的，域名可以免备案）
4. 一个GitHub账号或着gitee

## 🍖开工

1. 下载项目地址 https://github.com/yumusb/autoPicCdn

2. 配置up.php中的相关字段
````
define("TYPE","GITHUB");//选择github
define("USER","pic-cdn");//你的GitHub/Gitee的用户名
define("REPO","cdn2");//必须是上面用户名下的 公开仓库
define("MAIL","yumusb@foxmail.com");//邮箱无所谓，随便写
define("TOKEN","YourToken");
````
3. https://github.com/settings/tokens  去这个页面生成一个有写权限的token（repo：Full control of private repositories 和write:packages前打勾）

4. 文件配置好之后就可以上传到自己的虚拟主机了  参见 https://ysnsn.cn/2817.html  或者推荐  https://plushine.cn/38834.html
5. 绑定域名之后就可以通过域名访问，自己测试下能不能上传成功 
> php版本选择 7.2

## 🍳gitee跟GitHub差不多一样完事，真香

