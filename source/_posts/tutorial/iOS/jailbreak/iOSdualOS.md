---
title: 老 iOS 装双系统
date: 2022-01-21 13:43:54
categories: 
    - 教程
    - iOS
    - 越狱
description: 在 32 位 iOS 设备下用 Coolbooter(CLI) 安装双系统
tags: iOS
cover: https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS_top.png
sticky: 98
---

## 用前说明
本教程分为 iOS 6- 和 iOS 7+ 两个部分，请选择合适自己的部分观看
TIPS:
该方法仅支持 32 位的 iOS 设备，且都需要越狱

### 64 位设备有哪些
iPhone5s、iPad5、iPad mini3、iPad Air、iPad Pro 及以上的设备均为 64 位设备

### 实验环境（仅限 32 位 iOS 设备）
iPhone 5、iPhone 4s
iOS6.1.3,iOS8.4.1
Cydia

------

iOS 6 以以下
需要在 Cydia 中添加以下越狱源
```https
coolbooter.com
```
然后安装如下插件
1.CoolBooterCLI
2.MobileTerminal（自带的 BigBoss 源中有，请不要使用别的 Terminal）
3.CoolBooter Untetherer（可选，结尾会提到用处）

------

iOS 7+
需要在 Cydia 中添加以下越狱源
```https
coolbooter.com
```
然后安装如下插件
1.CoolBooter
2.CoolBooter Untetherer（可选，结尾会提到用处）

## iOS6 装双系统
这部分有两种方法，但内容大同小异，第一种为在线安装，第二种为离线安装
如果是方法二，请安装以下内容
{% post_link tutorial/iOS/jailbreak/afc+appsync Apple File Conduit “2” %}
[爱思助手](https://www.i4.cn) （电脑）
[iOS 固件](https://ipsw.me) （在电脑上下载好）

### 下载系统
打开手机上的 MobileTerminal
输入 su
输入密码（默认为 alpine，但输入过程不会显示任何字符）

—-这里是方法二，方法一的玩家可以跳过—-
iPhone 连接电脑，在”文件管理”中找到以下路径（如果没有可以手动创建）
````
/var/cbooter
````
然后把你的固件导入到上面的路径即可
![固件路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS1.png)
—-分界线捏—-

在 MobileTerminal 中输入以下命令
````
coolbootercli <版本号> --datasize <要分配的磁盘大小> GB
如
coolbootercli 9.0.2 --datasize 12GB
````
TIPS：但如果你是在 iPhone4s 下载 iOS9.3 的话则会是下载 iOS9.3 (13E237) 的版本
如果是方法一就开始下载固件，下载完成后会和方法二一样开始校验、解压固件然后安装系统
![下载固件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS2.png)

如果是方法二则开始校验然后解压固件，然后安装系统
![解压固件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS3.png)
出现容量已满，点击确定即可
![弹窗提示](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS4.png)
然后手机等一会会自动重启

### 安装双系统（往后的过程建议看完再实践）
打开手机上的 MobileTerminal
输入 su
输入密码（默认为 alpine，但输入过程不会显示任何字符）
输入以下命令
````
coolbootercli -b
````
出现这个页面后立马锁屏（<font size=4 color=yellow>如果你没有及时锁屏，系统则会黑屏，这时候只需要长按电源键和 Home 键几秒后松开 Home 键即可</font>）
![按键锁屏](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS5.png)
待手机自动重启后就会开始跑代码
![跑代码](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS6.png)
手机重启后再重复以上步骤

等到手机再跑代码，然后就会进入系统安装界面
![Apple Logo](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS7.png)
等待一会就能见到熟悉的部署界面了
![开机激活](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS8.png)

然后根据自己的需求去部署系统这里不用过多解释
安装完成后即可正常使用，且一般会自动越狱
如果你需要安装越狱软件，需要以下教程
{% post_link tutorial/iOS/jailbreak/afc+appsync AFC+AppSync 安装方法 %}

### 重启后再次进入双系统
每次重启或关机后再开机（不包括注销/重启 SpringBoard）后会回到主系统
你需要再次重复某些步骤
打开手机上的 MobileTerminal
输入 su
输入密码（默认为 alpine，但输入过程不会显示任何字符）
然后输入如下命令
````
coolbootercli -b
````
出现如下界面后迅速锁屏，然后等待自动进入辅系统
![按键锁屏](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS5.png)

### 卸载双系统
如果你不想用双系统了可以将其卸载
打开手机上的 MobileTerminal
输入 su
输入密码（默认为 alpine，但输入过程不会显示任何字符）
然后输入如下命令
````
coolbootercli -u
````
几秒钟过后双系统即可成功卸载

## iOS7+ 装双系统
该功能没试过能否直接导入镜像，大伙可以自行研究研究

### 下载系统(1)
打开桌面上的 CoolBooter 应用
点击 Install
![选择安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS9.png)
然后选择你需要双系统的版本
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS10.png)
选择完成后点击右下角的 Storage，并在此页面选择完第二系统的容量
![选择容量](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS11.png)
完成后点击右下角的 Select，再点击左下角的 I'm ready! 即可开始下载系统

### 拓展功能
<font size=4 color=yellow>早期一点的 CoolBooter 会提供越狱功能，你可以选择 Yes 来给双系统越狱，现在的版本则是直接帮你越狱好的</font>
点击 I'm ready! 后会会出现这个页面，如果你不想更改原生的启动 Logo，点击 No 即可
![自定义开机 Logo](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS12.png)
如果你不想看启动时跑代码就选择 No
![取消跑码页](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS13.png)

### 下载系统(2)
耐心等待一会，软件即可开始下载双系统
![下载系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS14.png)
下载完成后开始解压并写入文件到硬盘
![解压固件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS15.png)
完成后会出现容量不足的提示，点击确定即可
![弹窗提示](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS16.png)
点击 Rebot，然后系统就会自动重启
![重启系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS17.png)
重启完成后再次打开 CoolBooter，点击 Boot
![启动双系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS18.png)
出现这个页面时按下电源按键，等待系统自动重启
![按键锁屏](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS19.png)
重启后手机会显示这个页面，耐心等待一下就好
![完成安装过程](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS20.png)

手机再度重启后打开 CoolBooter，点击 Boot
![启动双系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS18.png)
出现这个页面时按下电源按键，等待系统自动重启
![按键锁屏](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS19.png)
等待一下即可进入到系统部署界面，双系统安装完成
![开机激活](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSdualOS/iOSdualOS21.png)