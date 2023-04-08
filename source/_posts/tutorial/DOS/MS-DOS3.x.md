---
title: 安装 MS-DOS 3.x
date: 2022-08-09 12:22:03
categories: 
	- 教程
	- DOS
tags:
	- DOS
	- VMware Workstation
description: 使用软盘，给 Workstation 虚拟机安装 MS-DOS 3.x
---

## 用前说明
较为早期的 Windows（如 Windows 1.x、2.x 需要 MS-DOS 2.x-3.x，或 IBM PC-DOS）

### 实验环境
[MS-DOS 3.x](https://winworldpc.com/product/ms-dos/3x) （这里我用的是 MS-DOS 3.30，选择第一个下载即可）
VMware Workstation（其它虚拟机也可以，部分内容有所不同）

## 创建虚拟机
选择系统版本中选择“其它”>“MS-DOS”
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-1.png)
CPU、内存和硬盘大小默认设置即可，并选择“将虚拟磁盘储存为单个文件”
![硬盘文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-2.png)
完成后点击“虚拟机设置”，把 CD/DVD 移除（可不做），然后添加软盘，并选择连接到 <code>DISK01.img</code>
![选择软盘镜像](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-3.png)
然后启动虚拟机

## 安装 MS-DOS 3.x
在这里输入正确的时间（如果你不想调整可以连续按两次回车）
![输入时间](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-4.png)
输入
````DOS
fdisk
````
然后就会进入到硬盘格式化页面，再在以下两个页面输入 <code>1</code>
![创建分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-5.png)
![创建主分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-6.png)
输入 <code>Y</code> 并按下<kbd>Enter</kbd>
![格式化分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-7.png)
在这个页面按任意键重启，但不要<font color=yellow size=3>取出软盘镜像</font>
![按任意键重启](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-8.png)

然后再次输入正确的时间（如果你不想调整可以连续按两次回车）
![输入时间](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-4.png)
然后输入
````DOS
format C: /v /s
````
然后按下<kbd>Enter</kbd>
输入 <code>Y</code>，最后按下 <kbd>Enter</code>
![格式化分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-9.png)
再输入
````
sys C:
````
按下<kbd>Enter</kbd>（这样做的作用是将 MS-DOS 从软盘传输到 C：，从而允许 C：可启动）
![设置活跃分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-10.png)

输入
````DOS
copy A:\*.* C:
````
然后按下 <kbd>Enter</kbd>，这样就会将软盘所有的内容复制了过去
![复制文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-11.png)
接下来，把 <code>DISK01.img</code> 换成 <code>DISK02.img</code>
![更换软盘镜像](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-12.png)
重复上面的内容
````DOS
copy A:\*.* C:
````
然后按下<kbd>Enter</kbd>，取出软盘镜像并重启
![复制文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-3.png)

至此，MS-DOS 3.x 的安装工作就完成了，重启后即可自动进入 MS-DOS 3.x
![主界面](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/MS-DOS3.x/MS-DOS3.x-14.png)