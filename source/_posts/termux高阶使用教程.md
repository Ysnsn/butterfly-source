---
title: termux高阶使用教程
toc: true
top: false
date: 2021-02-02 15:37:07
tags:
	- 食用教程
	- termux
	- 终端
categories: 食用教程
cover: https://cdn.jsdelivr.net/gh/Ysnsn/img@latest/2021/02/02/f9243ef08bfc195c710328fcedc74609.png
description: Termux 高级终端安装使用配置教程-----来自国光
abbrlink: termux
---

<script src="https://cdn.jsdelivr.net/npm/hls.js"></script>
<video id="video" preload loop style="height: 100%;width: 100%;object-fit: cover;">
</video>
<script>
  var video = document.getElementById('video');
  var videoSrc = 'https://cdn.jsdelivr.net/gh/Ysnsn/video-cdn/2021/3/00.m3u8';
  if (Hls.isSupported()) {
    var hls = new Hls();
    hls.loadSource(videoSrc);
    hls.attachMedia(video);
    hls.on(Hls.Events.MANIFEST_PARSED, function() {
      video.play();
    });
  }
</script>

> 本文摘自 *国光* https://www.sqlsec.com/2018/05/termux.html  

![img](https://image.3001.net/images/20180501/15251875958364.png)


Termux 高级终端安装使用配置教程，刚写这篇文章的时候，当时国内 Termux 相关的文章和资料相对来说还是比较少的，就花了几天写了这一篇文章，没想到居然火了，受宠若惊。所以这篇文章国光就打算定期更新了，想打造成 termux 的中文文档，希望本文可以帮助到更多对 Termux 感兴趣的朋友，发挥 Android 平台更大的 DIY 空间。





# 版权声明

17 年开始接触到 Termux，就发现它有很多值得挖掘的潜力，于是抽空在 18 年的某一个法定的整整花了三天假期开才写完第一版文章，然后文章陆陆续续更新到现在，期间有一次误操作不小心把博客所有的评论都删了，否则这篇文章的评论数会更多。现在本文的截图数量达到了150张左右了，文字数目已经数万多了。自己花了很长时间写出来的原创文章，抄袭白嫖党直接Ctrl+C Ctrl+V只要几秒钟。原创很辛苦，抄袭的成本却很低，维权的成本又很高，虽然国内目前的抄袭风气很严重，但是我相信尊重原创，保护原创从现在做起从大家做起，tomorrow is another day! 如果大面转载引用的话 希望标明文章出处:

**Termux 高级终端安装使用配置教程**

https://www.sqlsec.com/2018/05/termux.html

# 学习资源

考虑到手机用户体验和离线观看教程的需求，国光打包了几种风格的 PDF版本，并且已经插入好目录，阅读体验会比较友好。

**黑色背景的 PDF** : [Termux入门指南（Vue 黑）](https://sqlsec.lanzous.com/ibuzvna)

**白色背景的 PDF** : [Termux入门指南（Github 白）](https://sqlsec.lanzous.com/ibuztyj)

**macOS light风格** : [Termux入门指南（macOS 白）](https://sqlsec.lanzous.com/ibuzuxe)

**Gothic风格** : [Termux入门指南（简约线条）](https://sqlsec.lanzous.com/ibuztch)

早期我的信息安全交流群里面陆陆续续加了很多 Temux 玩家，然而那是一个信息安全交流群，Termux 的提问经常没有人回答，所以后来我就把博客所有的加群链接给去了。现在国光我单独建立了 1 个Temux 群，加群链接藏在本文当中，是一个彩蛋，缘妙不可言，随缘入群吧。好了话不多说，教程开始了，希望本文可以帮助到大家。

# Termux 简介

**文档相关**

- [Termux 官网](https://termux.com/)
- [Github 项目地址](https://github.com/termux/termux-app)
- [官方英文 WiKi 文档](https://wiki.termux.com/wiki/Main_Page)

**下载地址**

- [Google Play 下载地址](https://play.google.com/store/apps/details?id=com.termux)
- [F-Droid 下载地址](https://f-droid.org/packages/com.termux/)
- [酷安 下载地址](https://www.coolapk.com/apk/com.termux)

> Google Play 下载的版本比酷安要新，而且插件这块安装也很方便，有能力的朋友建议首先考虑下载Google PLay版本的，然后考虑 F-Droid版本，最后再考虑可怜兮兮的酷安版本。

Termux 是一个 Android 下一个高级的终端模拟器,开源且不需要 root，支持 apt 管理软件包，十分方便安装软件包，完美支持 Python、 PHP、 Ruby、 Nodejs、 MySQL等。随着智能设备的普及和性能的不断提升，如今的手机、平板等的硬件标准已达到了初级桌面计算机的硬件标准，用心去打造 DIY 的话完全可以把手机变成一个强大的极客工具。

**初始化**

第一次启动Termux的时候需要从远程服务器加载数据，然而可能会遇到这种问题：

Verilog

```verilog
Ubable to install
Termux was unable to install the bootstrap packages.
Check your network connection and try again.
```

这里的Termux官方远程的服务器地址是: http://termux.net/bootstrap/

![img](https://image.3001.net/images/20200418/15871943464391.png)

目前解决方法有两种：

1. VPN 全局代理 （成功率很高）
2. 如果你是 WiFi 的话尝试切换到运营商流量 （有一定成功率）
3. ① Google Play ② F-Droid ③ 酷安 根据这个顺序重复1、2操作

# 基本操作

基本操作还是要学习一下的，可以事半功倍。

## 缩放文本

可以使用缩放手势来调整其字体大小。 对就是 双指放大缩小照片那样操作。



![img](https://image.3001.net/images/20200418/15872024914185.png)



## 长按屏幕

长按屏幕会调出显示菜单项（包括复制、粘贴、更多），方便我们进行复制或者粘贴

![img](https://image.3001.net/images/20200418/15872022768181.png)



`More` 菜单的说明如下：





Bash

```bash
长按屏幕
├── COPY:    # 复制
├── PASTE:   # 粘贴
├── More:    # 更多
   ├── Select URL:             # 提取屏幕所有网址
   └── Share transcipt:        # 分享命令脚本
   └── Reset:                  # 重置
   └── Kill process:           # 杀掉当前会话进程
   └── Style:                  # 风格配色 需要自行安装
   └── Keep screen on:         # 保持屏幕常亮
   └── Help:                   # 帮助文档
```

## 会话管理

显示隐藏式导航栏，可以新建、切换、重命名会话session和调用弹出输入法

![img](https://image.3001.net/images/20200418/15872022029549.png)



同时在Android的通知栏中也可以看到当前Termux运行的会话数：



![img](https://image.3001.net/images/20200418/15872026639062.png)



## 常用按键

常用键是PC端常用的按键如: ESC键、Tab键、CTR键、ALT键，有了这些按键后可以提高我们日常操作的效率，所以Termux后面的版本默认都是显示这个扩展功能按键的。 (18年的时候默认是不显示的)



![img](https://image.3001.net/images/20200418/15872018464605.png)



打开和隐藏这个扩展功能按键目前有下面两种方法：

**方法一**

从左向右滑动,显示隐藏式导航栏,长按左下角的`KEYBOARD`

**方法二**

使用`Termux`快捷键:`音量+`+`Q`键 或者 `音量+`+`K`键

当然这个常用按键在 Termux 后面的版本也支持自定义的，详情见本文的「进阶配置」-「定制常用按键」这一小节。

# 基础知识

这些基础知识简单了解一下就可以了，Linux 用的多了 就会慢慢熟悉理解了。

## 快捷键表

`Ctrl`键是终端用户常用的按键，但大多数触摸键盘都没有这个按键，因此 Termux 使用`音量减小按钮`来模拟`Ctrl`键。
例如，在触摸键盘上按`音量减小`+ `L`就相当于是键盘上按`Ctrl + L`的效果一样，达到清屏的效果。

- `Ctrl + A` -> 将光标移动到行首
- `Ctrl + C` -> 中止当前进程
- `Ctrl + D` -> 注销终端会话
- `Ctrl + E` -> 将光标移动到行尾
- `Ctrl + K` -> 从光标删除到行尾
- `Ctrl + U` -> 从光标删除到行首
- `Ctrl + L` -> 清除终端
- `Ctrl + Z` -> 挂起（发送SIGTSTP到）当前进程
- `Ctrl + alt + C` -> 打开新会话（仅适用于 黑客键盘）

`音量加键`也可以作为产生特定输入的`特殊键`.

- `音量加 + E` -> Esc键
- `音量加 + T` -> Tab键
- `音量加 + 1` -> F1（`音量增加 + 2` → F2…以此类推）
- `音量加 + 0` -> F10
- `音量加 + B` -> Alt + B，使用readline时返回一个单词
- `音量加 + F` -> Alt + F，使用readline时转发一个单词
- `音量加 + X` -> Alt+X
- `音量加 + W` -> 向上箭头键
- `音量加 + A` -> 向左箭头键
- `音量加 + S` -> 向下箭头键
- `音量加 + D` -> 向右箭头键
- `音量加 + L` -> | （管道字符）
- `音量加 + H` -> 〜（波浪号字符）
- `音量加 + U` -> _ (下划线字符)
- `音量加 + P` -> 上一页
- `音量加 + N` -> 下一页
- `音量加 + .` -> Ctrl + \（SIGQUIT）
- `音量加 + V` -> 显示音量控制
- `音量加 + Q` -> 切换显示的功能键视
- `音量加 + K` -> 切换显示的功能键视图

快捷键用的熟悉的话也可以极大提高操作的效率。

## 基本命令

Termux 除了支持 `apt` 命令外，还在此基础上封装了`pkg`命令，`pkg` 命令向下兼容 `apt` 命令。`apt`命令大家应该都比较熟悉了，这里直接简单的介绍下`pkg`命令:





Bash

```bash
pkg search <query>              # 搜索包
pkg install <package>           # 安装包
pkg uninstall <package>         # 卸载包
pkg reinstall <package>         # 重新安装包
pkg update                      # 更新源
pkg upgrade                     # 升级软件包
pkg list-all                    # 列出可供安装的所有包
pkg list-installed              # 列出已经安装的包
pkg show <package>              # 显示某个包的详细信息
pkg files <package>             # 显示某个包的相关文件夹路径
```

> 国光建议大家使用 pkg 命令，因为 pkg 命令每次安装的时候自动执行 apt update 命令，很是方便

## 软件安装

除了通过上述的 `pkg` 命令安装软件以外，如果我们有 `.deb` 软件包文件，也可以使用 `dpkg` 进行安装。





Bash

```bash
dpkg -i ./package.de         # 安装 deb 包
dpkg --remove [package name] # 卸载软件包
dpkg -l                      # 查看已安装的包
man dpkg                     # 查看详细文档
```

## 目录结构





Bash

```bash
echo $HOME
/data/data/com.termux/files/home

echo $PREFIX
/data/data/com.termux/files/usr

echo $TMPPREFIX
/data/data/com.termux/files/usr/tmp/zsh
```

长期使用 Linux 的朋友可能会发现，这个HOME路径看上去和我们电脑端的不太一样，这是为了方便 Termux 提供的特殊的环境变量。

![img](https://image.3001.net/images/20180502/15252398558622.png)



## 端口查看

### Android 10 以下版本

Andorid 10 以下的版本是可以正常使用netstat 命令的，这样可以方便的查看端口开放信息





Bash

```bash
# 查看所有端口
netstat -an

# 查看3306端口的开放情况
netstat -an|grep 3306
```



![img](https://image.3001.net/images/20200420/15873514956494.jpg)



### Android 10 版本

Andorid 10 版本的Termux 下无法正常使用 netstat -an 命令，国光的解决方法是安装一个 nmap，然后扫描本地端口（弯道超车）：





Bash

```bash
# 安装nmap端口扫描神器
pkg install nmap

# 扫描本地端口
nmap 127.0.0.1
```

使用 nmap 操作 纯属无奈之举，但是又不是不能用（源于：罗永浩名言 :-)）



![img](https://image.3001.net/images/20200420/15873522318400.jpg)



# 进阶配置

要想使用体验好，进阶配置少不了。（单押）

## 更换国内源

使用`pkg update` 更新一下的时候发现默认的官方源网速有点慢，在这个喧嚣浮躁的时代，我们难以静下心等待，这个时候就得更换成国内的`Termux`清华大学源了，加快软件包下载速度。

### 方法一：自动替换（推荐）

可以使用如下命令自动替换官方源为 TUNA 镜像源

> `pkg update` 卡住的话多按几次回车 不要傻乎乎的等





Bash

```bash
sed -i 's@^\(deb.*stable main\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main@' $PREFIX/etc/apt/sources.list

sed -i 's@^\(deb.*games stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable@' $PREFIX/etc/apt/sources.list.d/game.list

sed -i 's@^\(deb.*science stable\)$@#\1\ndeb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable@' $PREFIX/etc/apt/sources.list.d/science.list

pkg update
```

更换源几秒钟就可以执行完`pkg update`了，心里顿时乐开了花。

### 方法二：手动修改

请使用内置或安装在 Termux 里的文本编辑器，例如 `vi` / `vim` / `nano` 等直接编辑源文件，**不要使用 RE 管理器等其他具有 ROOT 权限的外部 APP** 来修改 Termux 的文件

编辑 `$PREFIX/etc/apt/sources.list` 修改为如下内容





Bash

```bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux/termux-packages-24 stable main
```

编辑 `$PREFIX/etc/apt/sources.list.d/science.list` 修改为如下内容





Bash

```bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux/science-packages-24 science stable
```

编辑 `$PREFIX/etc/apt/sources.list.d/game.list` 修改为如下内容





Bash

```bash
# The termux repository mirror from TUNA:
deb https://mirrors.tuna.tsinghua.edu.cn/termux/game-packages-24 games stable
```

**安装基础工具**

更换源之后来赶紧来下载安装一些基本工具吧，这些工具基本上是 Linux 系统自带的，因为 Termux 为了体积不过大，默认是没有带这些工具的，执行下面的命令来安装:





Bash

```bash
pkg update
pkg install vim curl wget git tree -y
```

## 终端配色方案

**脚本项目地址**：https://github.com/Cabbagec/termux-ohmyzsh/

该脚本主要使用了`zsh`来替代`bash`作为默认 shell，并且支持色彩和字体样式，同时也激活了外置存储，可以直接访问SD卡下的目录。主题默认为 agnoster，颜色样式默认为 Tango，字体默认为 Ubuntu。

> 执行下面这个命令确保已经安装好了 curl 命令





Bash

```bash
sh -c "$(curl -fsSL https://github.com/Cabbagec/termux-ohmyzsh/raw/master/install.sh)"  
```

如果因为不可抗力的原因，出现`port 443: Connection refused`网络超时的情况，那么执行下面国光迁移到国内的地址的命令即可：





Bash

```bash
sh -c "$(curl -fsSL https://html.sqlsec.com/termux-install.sh)"  
```

Android6.0 以上会弹框确认是否授权访问文件,点击`始终允许`授权后 Termux 可以方便的访问SD卡文件。



![img](https://image.3001.net/images/20200418/1587207468173.png)



手机 App 默认只能访问自己的数据，如果要访问手机的存储，需要请求权限，如果你刚刚不小心点了拒绝的话，那么可以执行以下命令来重新获取访问权限:





Bash

```bash
termux-setup-storage
```

脚本允许后先后有如下两个选项:





Bash

```bash
Enter a number, leave blank to not to change: 14
Enter a number, leave blank to not to change: 6
```

分别选择`色彩样式`和`字体样式`，重启Termux app后生效配置。不满意刚刚的效果，想要继续更改配色方案的话，可以根据下面命令来更改对应的色彩配色方案：

**设置色彩样式**：

输入`chcolor`命令更换色彩样式，或者：`~/.termux/colors.sh`命令

**设置字体**

运行`chfont`更换字体，或者：`~/.termux/fonts.sh`命令

## 创建目录软连接

执行过上面的一键配置脚本后，并且授予 Termux 文件访问权限的话，会在家目录生成`storage`目录，并且生成若干目录，软连接都指向外置存储卡的相应目录:

![img](https://image.3001.net/images/20200418/15872083523807.png)



**创建QQ文件夹软连接**

手机上一般经常使用手机QQ来接收文件,这里为了方便文件传输,直接在`storage`目录下创建软链接.
**QQ**





Bash

```bash
ln -s /data/data/com.termux/files/home/storage/shared/tencent/QQfile_recv QQ
```

**TIM**





Bash

```bash
ln -s /data/data/com.termux/files/home/storage/shared/tencent/TIMfile_recv TIM
```



![img](https://image.3001.net/images/20200418/15872085834532.png)



这样可以直接在`home`目录下去访问QQ文件夹，大大提升了工作效率。

## 定制常用按键

在 Termux v0.66 的版本之后我们可以通过 `~/.termux/termux.properties` 文件来定制我们的常用功能按键，默认是不存在这个文件的，我们得自己配置创建一下这个文件。

下面做尝试简单配置一下这个文件:





Bash

```bash
# 新建并编辑配置文件
vim ~/.termux/termux.properties
```

内容为：





Bash

```bash
extra-keys = [ \
 ['ESC','|','/','HOME','UP','END','PGUP','DEL'], \
 ['TAB','CTRL','ALT','LEFT','DOWN','RIGHT','PGDN','BKSP'] \
]
```

> 如果无法创建这个文件，那么得首先新建一下这个目录 mkdir ~/.termux

修改完成保存文件后，重启 Termux app生效配置：



![img](https://image.3001.net/images/20200420/15873594933774.jpg)



可以直接输入特殊的字符串，例如上面的例子中的`|`就是一个字符串，此外 Termux 还有封装了一些特殊按键，入上面例子中的`ESC`就是 Termux 自带的按键，完整的特殊按键表如下：

| 按键       | 说明           |
| :--------- | :------------- |
| `CTRL`     | **`特殊按键`** |
| `ALT`      | **`特殊按键`** |
| `FN`       | **`特殊按键`** |
| ESC        | 退出键         |
| TAB        | 表格键         |
| HOME       | 原位键         |
| END        | 结尾键         |
| PGUP       | 上翻页键       |
| PGDN       | 下翻页键       |
| INS        | 插入键         |
| DEL        | 删除键         |
| BKSP       | 退格键         |
| UP         | 方向键 上      |
| LEFT       | 方向键 左      |
| RIGHT      | 方向键 右      |
| DOWN       | 方向键 下      |
| ENTER      | 回车键         |
| BACKSLASH  | 反斜杠 `\`     |
| QUOTE      | 双引号键       |
| APOSTROPHE | 单引号键       |
| F1~F12     | F1-F12按键     |

上面列出的三个**特殊键**中的每一个最多只能在附加键定义中列出一次，超过次数将会报错。

下面是国光我自用的按键表：





Bash

```bash
extra-keys = [ \
 ['ESC','|','/','`','UP','QUOTE','APOSTROPHE'], \
 ['TAB','CTRL','~','LEFT','DOWN','RIGHT','ENTER'] \
]
```



![img](https://image.3001.net/images/20200420/15873610423256.jpg)



## zsh 主题配色

编辑家目录下的`.zshrc`配置文件





Bash

```bash
$ vim .zshrc
```

第一行可以看到,默认的主题是`agnoster`主题:



![img](https://image.3001.net/images/20200418/15872087339756.png)



实际上这个主题也蛮酷的，如果你还想更换其他主题的话，那么在`.oh-my-zsh/themes`目录下放着`oh-my-zsh`所有的主题配置文件，只要将默认的 agnoster 更换为其他的主题文件名即可。
下面是国光认为还不错的几款主题



![agnoster](https://image.3001.net/images/20200418/15872089685912.png)

**agnoster**





![ys](https://image.3001.net/images/20200418/15872091524140.png)

**ys**





![robbyrussell](https://image.3001.net/images/20200418/15872092946550.png)

**robbyrussell**



主题比较多，国光这里就不列举了，感兴趣大家可以一个个尝试去看看。 当然如果你是个变态的话，可以尝试`random` 主题,每打开一个会话配色主题都是随机的.

```
ZSH_THEME="random"
```

## zsh 插件推荐

zsh 之所以受欢迎除了好看的配色以为，另一个原因就是强大的插件了。下面国光列举一款比较实用的插件的安装方法，更多强大的插件等待大家自己去探索。

### autosuggestions

根据用户的平时使用习惯，终端会自动提示接下来可能要输入的命令，这个实际使用效率还是比较高的：





Bash

```bash
# 拷贝到 plugins 目录下
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```

在 `~/.zshrc` 中配置：





Ini

```ini
plugins=(其他的插件 zsh-autosuggestions)
```



![img](https://image.3001.net/images/20200418/15872114762117.png)



输入`zsh`命令生效配置:



![效果图](https://image.3001.net/images/20200419/15872692273991.png)

**效果图**



可以看到国光我只敲了一个`v`后面的命令就自动提示补全了，这时候只要按`右方向键`，在 Termux 里面的快捷键是 `音量加 + D`，就可以直接补全命令了。

## 修改启动问候语

默认的启动问候语如下:



![img](https://image.3001.net/images/20200418/15872126727686.jpg)

这个启动问候语在前期对于初学者有一定的帮助，但是随着你们 Termux 的熟悉，这个默认的问候语就会显得比较臃肿。编辑问候语文件可以直接修改启动显示的问候语:







Bash

```bash
vim $PREFIX/etc/motd
```

修改完的效果如下:



![本文版本归国光所有 转载注明出处哦](https://image.3001.net/images/20200418/1587213178823.jpg)

**本文版本归国光所有 转载注明出处哦**



这样启动新的会话的时候看上去就会简洁很多。什么你也想要这个效果？ 呐 下面是国光自己生成的，可以直接复制粘贴:





Ini

```ini
  _____                              
 |_   _|__ _ __ _ __ ___  _   ___  __
   | |/ _ \ '__| '_ ` _ \| | | \ \/ /
   | |  __/ |  | | | | | | |_| |>  < 
   |_|\___|_|  |_| |_| |_|\__,_/_/\_\
```

## 超级管理员身份