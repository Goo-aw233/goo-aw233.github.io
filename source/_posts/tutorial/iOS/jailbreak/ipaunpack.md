---
title: IPA 砸壳
date: 2022-01-06 12:56:12
categories: 
    - 教程
    - iOS
    - 越狱
tags:
	- Windows
	- iOS
	- 软件
description: 在 Windows 和 iOS 上使用 Clutch 砸壳 IPA
cover: 
---

## 用前说明
<font size=4 color=red>如果是正版软件，则需要卡 ID 或登录后才能砸壳，如爱思等共享正版在自动下载对应的助手后将不受影响</font>
### 实验环境&需要的工具（尚未测试过其他版本 iOS 是否有效）
iOS6.1.3
Cydia
1.OpenSSH
2.iFile
3.[爱思助手](https://www.i4.cn)
4.[Clutch](https://github.com/KJCracks/Clutch/releases/tag/2.0.4)
(5.如果你是手机操作则需要再下载 MobileTerminal)

## 准备工作
下载好序言所提到的四(五)个工具

### 安装 Clutch
在电脑下载好 Clutch2.0.4 后将其命名为 clutch (没有扩展名和版本号且区分大小写)
随后用爱思助手将其放入以下目录
````
/usr/bin
````
![文件目录存放](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack1.png)
然后在 iFile 找到相同的目录下的 clutch
并在属性的用户、组、全局中都赋予读、写、执行权限
![文件属性选择](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack2.png)
![文件属性](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack3.png)
做完后点击完成

### 开启 SSH 通道
如果你不使用电脑来操作可以忽略这个步骤
![开启 SSH 通道](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack4.png)

### 开始砸壳

#### 这里给手机看的
在手机上打开 Terminal
输入 su
然后输入密码(默认为 alpine 输入密码时不显示任何字符)
![获取 Root 权限](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack5.png)
#### 这里是给电脑看的
开启 SSH 通道后点击下载 SSH 客户端
![选择 SSH 客户端](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack6.png)

<font size=4>——分界线(以下内容手机电脑都一样操作)——</font>

在 SSH 客户端中输入如图所示的命令
（意为授予 clutch 权限，重新砸壳的时候无需再次运行这两个命令，直接从 <code>clutch -i</code> 开始即可）
````
cd /usr/bin
chmod +x clutch
````
![命令](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack7.png)
然后输入
````
clutch -i
````
即可列出所有已经安装的软件(如果是 MobileTerminal 运行需要在屏幕右边才能滑动)
![列表](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack8.png)
找到你要砸壳的软件前面的序号
在客户端输入命令
````
用法:clutch -d <软件序号>
如:clutch -d 37
````
![正在砸壳](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack9.png)
稍等一下,软件越大,所需的时间就越长

完成后就是这样的
![最终效果](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack10.png)

砸壳完成的ipa则会放在
````
/var/mobile/Documents/Dumped
````
![存放目录](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipaunpack/ipaunpack11.png)
用爱思提取出来后安装即可