---
title: 解决 Windows Vista 和 7 问题合集（1）
date: 2022-05-16 19:20:47
categories: 
	- 教程
	- Windows
description: 给 Windows Vista/7 安装 Service Pack 和解决 Windows Vista/7/Server 2008 R2/Home Server 2011 无法获取更新
tags: Windows
cover: https://s2.loli.net/2022/08/14/98FyIC53NZrV7Gq.png
---

## 用前说明

### 实验环境
Windows Vista
Windows 7
Windows Server 2008 (R2)
Windows Home Server 2011
[补丁](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Em5nztbLCAxEj8OSLo8dTtoBdAxnGJKpmjFTdLoqCAGXLQ)
（章节 I 请选择 <code>SP</code> 文件夹内的内容，章节 II 请选择 <code>Update Package</code> 文件夹的内容，x64 为 64 位，x86 为 32 位）
![](https://s2.loli.net/2022/08/14/Uh8eV5HDg4nNkYM.png)

## 章节 I（给 Windows Vista/7 安装 Service Pack）
为了节省资源，Vista 和 7 的教程合二为一，内容上大同小异
<font size=4 color=yellow>如果你不是虚拟机，则需要用虚拟光驱工具或者解压工具，并直接观看 [安装补丁](#安装补丁) 章节</font>
### 在虚拟机中插入补丁
点击虚拟机设置
![](https://s2.loli.net/2022/07/31/Wki8ueYRaBp5nq3.png)
在虚拟机设置中选择 CD/DVD，然后点击右边的使用 ISO 映像文件，并点击浏览，然后选择 ISO（这里就不放 Vista 的例图了）
![](https://s2.loli.net/2022/08/14/oukUf7PL9Z4jt2D.png)
选择完成后点击确认并返回到虚拟机

### 安装补丁
插入补丁后点击 Windows 徽标键>计算机
![](https://s2.loli.net/2022/07/31/SgeCAwcjHYqQKoX.png)
双击打开 CD 驱动器
![](https://s2.loli.net/2022/08/14/yt6jTAGYHPeLOWQ.png)
直接运行镜像内提供的 <code>exe 安装包</code>即可
![Windows 7 Setup](https://s2.loli.net/2022/08/14/FDn6ubQ3HAR9vCO.png)

------

<font size=4>Windows Vista 则需要先安装 SP1 才可以安装 SP2
![Windows Vista SP1 Setup](https://s2.loli.net/2022/08/14/HiuckQMhBDo9UEq.png)
![Windows Vista SP2 Setup](https://s2.loli.net/2022/08/14/df2RVgo3kPlrNEM.png)

------

然后就完成了
![Windows Vista SP2](https://s2.loli.net/2022/08/14/keTFK3yjLzgwWcd.png)
![Windows 7 SP1](https://s2.loli.net/2022/08/14/9BbW8T2cLJFMl4w.png)

## 章节 II（解决无法获取更新）

