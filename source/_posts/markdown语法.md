---
title: markdown语法
top: false
tags:
  - Markdown
  - 基本
cover: >-
  http://imageproxy.chaoxing.com/0x0,q15,jpeg,sv3q6pFiurnSnP7_VsCbAG0pSDxMz0mqVDhUM_uMenjs/http://p.ananas.chaoxing.com/star3/origin/fba7d3fadab6021a0609aed0a97defd3.png
description: markdown语法初识
abbrlink: markdown
date: 2020-07-20 10:11:06
categories: Markdown
---

## **如果有一个好的markdown编辑器下面的基本就不用看了**      [推荐typora](https://typora.io/)

### 一、标题

- 在想要设置为标题的文字前面加#来表示
- 一个#是一级标题，二个#是二级标题，以此类推。支持六级标题。

- 注：标准语法一般在#后跟个空格再写文字.

示例：
```
# 这是一级标题
## 这是二级标题
### 这是三级标题
#### 这是四级标题
##### 这是五级标题
###### 这是六级标题
```
### 二、字体
#### 加粗
- 要加粗的文字左右分别用两个*号包起来

#### 斜体
- 要倾斜的文字左右分别用一个*号包起来

#### 斜体加粗
- 要倾斜和加粗的文字左右分别用三个*号包起来

#### 删除线
- 要加删除线的文字左右分别用两个~~号包起来

示例：
```
**这是加粗的文字**
*这是倾斜的文字*`
***这是斜体加粗的文字***
~~这是加删除线的文字~~
```
### 三、引用
- 在引用的文字前加>即可。引用也可以嵌套，如加两个>>三个>>>
n个...
貌似可以一直加下去，但没神马卵用

示例：
```
>这是引用的内容
>>这是引用的内容
>>
>>>>>>>>>>这是引用的内容
```

### 四、分割线
- 三个或者三个以上的 - 或者 * 都可以。

示例：
```
---
----
***
*****
```

### 五、图片
- 语法：

![图片alt](图片地址 ''图片title'')

图片alt就是显示在图片下面的文字，相当于对图片内容的解释。
图片title是图片的标题，当鼠标移到图片上时显示的内容。title可加可不加

### 六、超链接
- 语法：

[超链接名](超链接地址 "超链接title")
title可加可不加
示例：

[百度](http://baidu.com)

<a href="超链接地址" target="_blank">超链接名</a>

示例
<a href="https://www.jianshu.com/u/1f5ac0cf6a8b" target="_blank">简书</a>

### 七、列表
- 无序列表
- 语法：
- 无序列表用 - + * 任何一种都可以

	- 列表内容
	+ 列表内容
	* 列表内容

注意：- + * 跟内容之间都要有一个空格


语法：
数字加点

1. 列表内容
2. 列表内容
3. 列表内容

注意：序号跟内容之间要有空格

上一级和下一级之间敲三个空格即可

一级无序列表内容

二级无序列表内容
二级无序列表内容
二级无序列表内容
一级无序列表内容

二级有序列表内容
二级有序列表内容
二级有序列表内容
一级有序列表内容

二级无序列表内容
二级无序列表内容
二级无序列表内容
一级有序列表内容

二级有序列表内容
二级有序列表内容
二级有序列表内容
### 八、表格
- 语法：

表头|表头|表头
---|:--:|---:
内容|内容|内容
内容|内容|内容

第二行分割表头和内容。
- 有一个就行，为了对齐，多加了几个
文字默认居左
-两边加：表示文字居中
-右边加：表示文字居右
注：原生的语法两边都要用 | 包起来。此处省略
示例：

姓名|技能|排行
--|:--:|--:
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟


姓名	技能	排行
刘备	哭	大哥
关羽	打	二哥
张飞	骂	三弟
### 九、代码
- 语法：
- 单行代码: 代码之间分别用一个反引号包起来

    `代码内容`
代码块：代码之间分别用三个反引号包起来，且两边的反引号单独占一行

(```)
  代码...
  代码...
  代码...
(```)

示例：

单行代码

`create database hero;`
代码块

(```)
    function fun(){
         echo "这是一句非常牛逼的代码";
    }
    fun();
(```)
效果如下：

单行代码

create database hero;

代码块

function fun(){
  echo "这是一句非常牛逼的代码";
}
fun();

#### 十、流程图

```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&```

```
#### 插入视频&音频

<video id="video" controls="" preload="none" poster="">
      <source id="mp4" src="https://saekiraku.oss-cn-beijing.aliyuncs.com/github/vscode-rainbow-fart/showoff-1.mp4" type="video/mp4">
      </video>


```
<video id="video" controls="" preload="none" poster="">
      <source id="mp4" src="https://saekiraku.oss-cn-beijing.aliyuncs.com/github/vscode-rainbow-fart/showoff-1.mp4" type="video/mp4">
      </video>
```



<audio id="audio" controls="" preload="none">
      <source id="mp3" src="http://qiniu.cloud.fandong.me/Music_iP%E8%B5%B5%E9%9C%B2%20-%20%E7%A6%BB%E6%AD%8C%20%28Live%29.mp3">
      </audio>
```
<audio id="audio" controls="" preload="none">
      <source id="mp3" src="http://qiniu.cloud.fandong.me/Music_iP%E8%B5%B5%E9%9C%B2%20-%20%E7%A6%BB%E6%AD%8C%20%28Live%29.mp3">
      </audio>
```

