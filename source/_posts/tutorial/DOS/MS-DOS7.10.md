---
title: 安装 MS-DOS 7.10
date: 2022-05-08 19:17:45
categories: 
	- 教程
	- DOS
tags:
	- DOS
	- VMware Workstation
description: 使用软盘，给 Workstation 虚拟机安装 MS-DOS 7.10
cover: https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-top_img.png
---

## 用前说明

### 实验环境
[MS-DOS 7.10 CD（选择 Server 2 或 Server 1 都可以](https://winworldpc.com/download/40c2bd6b-6618-c39a-11c3-a4e284a2c3a5)
VMware Workstation（其它虚拟机也可以，部分内容有所不同）

## 创建虚拟机
选择系统版本中选择“其它”>“MS-DOS”
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-1.png)
CPU 1p1c，RAM 64MiB 即可
![配置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-2.png)
硬盘选择“储存为单文件”，大小 2-4GiB 即可
![硬盘](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-3.png)
然后开启虚拟机

## 安装 MS-DOS 7.1
在该页面输入“1”然后回车
![安装系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-4.png)
在接下来的几个页面选择“Next”即可
![协议 1](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-5.png)
![协议 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-6.png)
![协议 3](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-7.png)
在这里选择“Continue”
![继续安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-8.png)
选择"Create a FAT32/16/12 Primary Partition"
![创建分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-9.png)
完成后点击“Rebot now”
![重启](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-10.png)

在这个页面的时候选择虚拟机关机
![关机虚拟机](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-11.png)
关机后选择“虚拟机”>“电源”>“开机时进入固件”
![进入 BIOS](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-12.png)
进入 BIOS 后用 <kbd>→</kbd> 选择到“Boot”，再将光标移动到“CD-ROM Drive”上
按下 <kbd>+</kbd> 使得该选项向上移动，然后按下 <kbd>F10</kbd> 选择“Yes”保存重启
![更改设置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-13.png)
![保存设置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-14.png)

在重启后该页面输入“1”然后回车
![安装系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-4.png)
在接下来的几个页面选择“Next”即可
![协议 1](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-5.png)
![协议 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-6.png)
![协议 3](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-7.png)
在这里选择“**Skip**”
![跳过](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-8.png)
点击“Yes”
![覆写 MBR](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-15.png)
默认路径即可，继续选择“Next”
![安装路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-16.png)
继续“Yes”
![创建文件夹](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-17.png)
在这里把“Install Add-Ons”前面的“x”给去掉
![取消安装 Install Add-Ons](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-18.png)
然后继续“Next”

如果你不想安装“AccessDos”可以选择“No”
![是否安装 AccessDos](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-19.png)
点击“OK”
![确认选项](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-20.png)
点击“Yes”
![开启 DOS 启动 Logo](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-21.png)
这个是启动日志，你不想要可以选择“No”
![日志记录](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-22.png)
开启长文件名支持，可以选择“Yes”
![长名称支持](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-23.png)
默认的“Enable UMB memory”即可
![不知道有什么用的](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-24.png)
你不确定要选什么的话就选择“Load both”
![不知道有什么用 x2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-25.png)
第二个是电源管理，第五个不知道，第六个是加快硬盘读写，我选择默认，然后继续“Continue”
![额外程序](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-26.png)
代码页，选择倒数第二个后点“Continue”
![代码页](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-27.png)
终于结束了（喜），点击“OK”，然后点击“Yes”来重启系统
![结束](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-28.png)
![重启](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-29.png)

重启之后输入“1”（默认输入）即可启动 MS-DOS
![正常启动](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-30.png)
这样就成了
![系统页面](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS7.10/MS-DOS7.10-31.png)