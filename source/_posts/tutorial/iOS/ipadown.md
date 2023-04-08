---
title: 抓包旧版本 IPA
date: 2022-03-26 21:38:45
categories: 
	- 教程
	- Windows
tags:
	- Windows
	- iOS
	- 软件
description: 使用“iOS 旧版应用下载”软件抓取旧版本的 IPA 安装包
---

## 用前说明

### 实验环境（其他环境一样可以）
[iOS 旧版应用下载](https://www.52pojie.cn/thread-1284776-1-1.html)
[.Net 4.8 Runtime（必装，否则软件会未响应）](https://dotnet.microsoft.com/en-us/download/dotnet-framework/thank-you/net48-offline-installer)

-----iTunes 选择合适自己的即可-----

[iTunes 12.6.5.3 x64](https://secure-appldnld.apple.com/itunes12/091-87819-20180912-69177170-B085-11E8-B6AB-C1D03409AD2A6/iTunes64Setup.exe)
[iTunes 12.6.5.3 x86](https://secure-appldnld.apple.com/itunes12/091-87820-20180912-69177170-B085-11E8-B6AB-C1D03409AD2A5/iTunesSetup.exe)

------

## 抓包的普通用法

### 在 iTunes 中打开商店页面
点击软件左上角的“音乐”按钮，并选择“编辑菜单”
![菜单编辑](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown1.png)
然后勾选上“应用”，点击“完成”，再切换到应用页
![勾选应用](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown2.png)

完成后在账户里登录自己的 Apple 账户

然后点击 App Store 按钮，在右上角搜索或点击下面的已购项目来下载软件
![搜索软件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown3.png)

### 在软件中搜索你要下的软件
在软件搜索框搜索软件名称，并更改到相对应的地区和软件适用设备
然后右击软件选择“查看历史版本”
![查看历史版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown4.png)
在新页面选择你要下载的版本，右键选择“下载此版本 APP”
TIPS：如果你觉得版本排序太乱，或者搜索不到的话可以把右上角的“备用接口”复选框取消掉后再次点击“搜索”按钮
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown5.png)
等软件跳转到新窗口时，转回到 iTunes 下载对应的游戏即可
![下载应用](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown6.png)

------

如果速度一直是 0KB 的话
先暂停软件和 iTunes 的下载
然后再重新在 iTunes 的下载页中点击“继续下载”即可
![下载速度为 0](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown7.png)

------

下载完成后点击安装管理>打开 APP 目录即可找到你下载的软件
![查找应用位置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown8.png)

## 进阶用法

### 抓已经撤包的版本
就像这种提示
![撤包提示](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown9.png)

在安装管理中选择要抓的软件，右键选择“伪装旧版 APP”
![伪装旧版](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown10.png)
然后点击“打开 APP 目录”，并在 iTunes 中选择"资料库"
![资料库](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown11.png)
找到伪装旧版的 APP，然后直接拖入到 iTunes 中
![链接到 iTunes](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown12.png)
在弹出的窗口中选择“替换(R)”
![替换文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown13.png)
在软件中选择要下载的版本并截取，然后转到 iTunes 的更新页
![截取](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown14.png)
选中软件右键，点击更新应用即可下载到撤包的版本
![更新下载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/ipadown/ipadown15.png)

### 抓软件搜索不到但已购项目有的软件（仅适用于有安装包的情况下）
施工.jpg