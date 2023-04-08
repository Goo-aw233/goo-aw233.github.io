---
title: 无法打开"xxx"，因为无法验证此开发者
date: 2022-05-22 10:04:52
categories: 
	- 教程
	- macOS
tags:
	- macOS
description: 打开 Mac OS (X)/macOS 的开发者模式来允许安装未验证的开发者软件
cover: https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit-top_img.png
---

## OS X（10.11 及以前）
点击 Dock 栏的<code>系统偏好设置</code>
![设置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit1.png)
点击<code>安全性与隐私</code>
![安全性与隐私](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit2.png)
点击左下角的<code>🔒</code>，然后输入你的密码并回车
![输入密码](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit3.png)
点击<code>任何来源</code>，然后点击<code>允许任何来自任何来源</code>
![允许来源](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit4.png)
完成后重新点击左下角的<code>🔓</code>即可

## macOS（10.12 及以后）
点击 Dock 栏的<code>Launcher Pad（或者叫启动台）</code>
![启动台](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit5.png)
然后打开<code>其它</code>文件夹，并选择里面的<code>终端</code>
![其它文件夹](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit6.png)
![终端](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit7.png)
打开终端后输入命令然后回车
````shell
sudo spctl --master-disable
````
出现 <code>Password:🔑</code> 的标志时输入密码<font size=3 color=yellow>（默认不显示）</font>
![输入密码](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit8.png)
这样就成功了
![成功](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/macOSswit/macOSswit9.png)