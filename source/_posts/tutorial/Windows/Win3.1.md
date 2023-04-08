---
title: 虚拟机安装 Windows 3.1
date: 2022-05-15 20:55:32
categories: 
	- 教程
	- Windows
tags:
	- Windows
	- VMware Workstation
description: 用 MS-DOS 7.10 在 Workstation 在虚拟机里安装 Windows 3.1
top_img: https://winworldpc.com/res/img/screenshots/eaf36386209604f84929572ff2b13effe1af00b2624962e63458ba9fd58baf73.png
cover: https://winworldpc.com/res/img/screenshots/eaf36386209604f84929572ff2b13effe1af00b2624962e63458ba9fd58baf73.png
---

## 用前说明

### 实验环境
[Windows 3.1、引导文件、MS-DOS](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/EvRje-rRIBROkUT7UVfK224B4hY0HnLKgxFQcH2ghAx8Fw?e=eURsV8)
（Windows 3.1 源自 [ITELLYOU MSDN](https://msdn.itellyou.cn)
如果你真的够懒的话可以直接下里面的 Windows 3.1.iso
你也可以自己创建一个 MS-DOS，教程在下文）
UltraISO（在资源列表里有）
VMware Workstation（其它虚拟机也可以，部分内容有所不同）

## 创建镜像
<font size=3 color=green>如果你选择直接下 Windows 3.1.iso 的话可以掠过该步骤</font>
先将所有文件解压出来，选择路径，点击“Extract”
![](https://s2.loli.net/2022/07/31/rXaHNWsRI9AjoD3.png)
打开“UltraISO”，在里面创建一个名为 <code>Win3x</code> 的文件夹，并打开它
![](https://s2.loli.net/2022/07/31/ZHR3tLnGPbfOo47.png)
打开 <code>windows.31</code> 下的“SIMPCHIN”文件夹，把所有文件复制进去
![](https://s2.loli.net/2022/07/31/6huKi24twzgVDGe.png)
点击上面的“启动(B)”——“加载引导文件”，选择 <code>boot.bif</code> 文件
![](https://s2.loli.net/2022/07/31/zTImstPlQr9B42F.png)
![](https://s2.loli.net/2022/07/31/5d8GRbelZJ9rjiB.png)
然后改改镜像显示名称（可不做）
最后点击“保存”，随便起个名就好
![](https://s2.loli.net/2022/07/31/GQqx8CJhXIL6aUj.png)

## 安装 Windows 3.1
{% post_link tutorial/DOS/MS-DOS7.10 先创建一个 MS-DOS 的虚拟机 %}（或下载一个）
然后启动它
启动后点击“虚拟机设置”
选择 CD/DVD，把已连接(C)勾上，选择使用 ISO 映像文件(M)，然后点击浏览，选择创建好的镜像
![](https://s2.loli.net/2022/07/31/vYVB9lUCWpEfzI6.png)
点击确定

返回虚拟机后输入以下命令（最好区分大小写，不一定是 A：，也可能是 D：或者其它盘符）
````dos
A:
cd Win3x
setup.exe
````
然后回车
![](https://s2.loli.net/2022/07/31/gBFKcx29WJbRhCV.png)
这样就进入了 Windows 3.1 的安装界面
![](https://s2.loli.net/2022/07/31/8R9EqCjcAOZmM3b.png)
连续几次回车即可（这里就不放图了）

输入你的名字然后点击“继续(O)”
![](https://s2.loli.net/2022/07/31/2qQCifpZel81dAz.png)
选择“无连接的打印机”，点击右边的“安装(I)”
![](https://s2.loli.net/2022/07/31/qUXN6kKyvuoWOn5.png)
选择“MS-DOS Editor”，点击确定
![](https://s2.loli.net/2022/07/31/Cn8OXw9NhKPMItv.png)
教程可看可不看
![](https://s2.loli.net/2022/07/31/4gGZpoHhrLIX19w.png)
然后将光驱取消连接
![](https://s2.loli.net/2022/07/31/JUWBlDaX98fy6VG.png)
选择“重新引导(R)”
![](https://s2.loli.net/2022/07/31/fmtxrn7FUKgQBW3.png)

重启后输入以下命令
````dos
cd WINDOWS
WIN
````
![](https://s2.loli.net/2022/07/31/2u4wr6iBXezWxmn.png)
这样 Windows 3.1 就安装完成了
![](https://s2.loli.net/2022/07/31/7F1Nhf49vjaYZop.png)

## 以后使用
每次开机时都需要输入
````dos
cd WINDOWS
WIN
````
然后才会进入系统（没研究出其他 dalao 怎么自动引导的）
至于怎么装 Tool 还没研究，到时候再说罢（