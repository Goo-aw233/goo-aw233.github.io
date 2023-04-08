---
title: 创建个简单的安装程序
date: 2022-08-11 20:29:32
categories: 
	- 教程
	- Windows
tags: 
	- 软件
	- Windows
description: 使用 NSIS+VNISedit 来创建一个简单的安装程序
---

## 用前说明

### 实验环境
[NSIS 3.06.1.0 第三方汉化](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Eu8_UIxMcxJBqHP-nyVlADYBl2VSbo7diEFPEjXsCBc9hA?e=UCEElu)

## 编写脚本

### 创建脚本
点击<code>编译脚本 VNISedit</code>
![](https://s2.loli.net/2022/08/11/QuioL1thne5H76O.png)
在欢迎页中选择<code>使用脚本向导创建新的脚本文件(S)</code>
![](https://s2.loli.net/2022/08/11/pjwWDR7TCzSogVE.png)

### 更改信息
在<code>应用程序名称(A)</code>填写程序名称，<code>应用程序版本(V)</code>填写版本号，<code>应用程序出版人(P)</code>填写你的名字（或其它名称或不填），<code>应用程序网站(W)</code>填写网站主页（可不填），<code>应用程序标志(L)</code>可改可不改（体现在安装程序时左下角的名称）
![](https://s2.loli.net/2022/08/11/93nR8osuldxSqTr.png)
![应用程序标志](https://s2.loli.net/2022/08/11/DUbpw7fYetiOm3H.png)
点击<code>安装程序图标(I)</code>旁边的<code>...</code>来选择安装程序图标（需为 ico 后缀），<code>安装程序文件(P)</code>为安装程序默认名称，<code>安装程序语言(L)</code>就不多说，默认 SimpChinese（简中），<code>压缩算法(O)</code>没什么问题可以默认 LZMA
![](https://s2.loli.net/2022/08/11/GuzkRcJl4yrU5q7.png)

<code>快闪屏幕和背景窗口</code>不知道有啥用，干脆跳过

<code>应用程序默认目录(A)</code>是程序默认安装的目录，一般安装在 <code>C:\Program Files (x86)</code>（如果是 32 位系统则是 <code>C:\Program Files</code>），<code>授权文件(L)</code>为许可说明，如果你不填写则<font color=red>必须留空</font>；如果要填写则需要将 [TXT 编码格式转换为 ANSI](https://jingyan.baidu.com/article/2fb0ba4052455b41f2ec5f9b.html) （RTF 则不受影响）
![](https://s2.loli.net/2022/08/11/xIEkawFurjfVHJ5.png)

### 更改程序设置
在<code>应用程序文件</code>选择软件分支
先把默认的两个删去，然后点击<code>文件</code>上方的分支按钮，选择软件的目录，然后勾选<code>包含子目录</code>和<code>单独添加每一个文件</code>
![](https://s2.loli.net/2022/08/11/KlnMXdIySmArtcD.png)
如果你只要添加某一个文件则直接点<code>文件</code>上方的文件按钮然后选择软件

然后在左边双击<code>MainSection</code>然后选择更改它的名字
![](https://s2.loli.net/2022/08/11/PIbi1lsGFYa4TA5.png)
如果你要添加别的分支则点击第一个文件图标，然后输入名字，然后重复刚才的步骤添加文件
分支可不添加描述，如果你想让用户自定义安装组件就勾选<code>允许用户选择要安装的组件(A)</code>
![](https://s2.loli.net/2022/08/11/h3lbqpQMmEWnNv2.png)

### 更改快捷方式等
在<code>应用程序‘开始菜单’文件夹名称(S)</code>更改在开始菜单显示的名称
第一个复选框是可以让用户自定义开始菜单文件夹名称，第二个复选框是在开始菜单里添加程序主页的网页快捷方式，第三个复选框是在开始菜单添加卸载软件的快捷方式
最下面一行，<code>快捷方式</code>中</code>$ICONS_GROUP</code>和<code>$DESKTOP</code>对应的是开始菜单和桌面，<code>目的文件</code>对应的是你要对哪个文件创建快捷方式
![](https://s2.loli.net/2022/08/11/nU3wulZqEVsN7Gh.png)
<code>安装程序之后运行</code>是安装程序结束后要选择运行哪个文件，如果不需要可留空，参数与自述同上
![](https://s2.loli.net/2022/08/11/XNHpc3FRu4thOGr.png)

### 卸载程序
<code>解除安装提示(U)</code>和<code>解除安装消息(M)</code>自己更改，点击<code>解除安装程序图标</code>旁边的<code>...</code>来选择卸载程序图标（需为 ico 后缀），卸载方式选择<code>简易方式(A)</code>即可（一般不会有残留）
![](https://s2.loli.net/2022/08/11/4RqbihQF3GY7zjU.png)

### 完成
完成后点击<code>保存脚本(S)</code>、<code>转换文件路径到相对路径(C)</code>和<code>编译脚本(O)</code>
![makesetup12.png](https://s2.loli.net/2022/08/11/Hrd1G2LxiX3Rjpv.png)
（如果需要自己修改脚本参数则不勾选<code>编译脚本(O)</code>，需要编译时点击上面的<code>NSIS(N)</code>><code>编译脚本(C) Ctrl+F9</code>）
![](https://s2.loli.net/2022/08/11/eAKPCpgu1MwcGNt.png)
完成后会在脚本保存的目录下生成安装程序
![](https://s2.loli.net/2022/08/11/gXP9c7MYINVJqsA.png)
这样就可以了
![](https://s2.loli.net/2022/08/11/mEkhBDYA9iacQOZ.png)