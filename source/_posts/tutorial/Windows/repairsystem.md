---
title: 修复 Windows 系统组件
date: 2022-07-06 20:15:35
categories: 
	- 教程
	- Windows
tags: Windows
cover: https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem_top.png
top_img: https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem_top.png
description: 使用 SFC&DISM 命令和（或）镜像修复 Microsoft Windows
---

## 用前说明
本教程节选改编自 [Microsoft Learn](https://learn.microsoft.com/troubleshoot/windows-server/deployment/fix-windows-update-errors)

### 实验环境
系统版本≥Windows 7 SP1 或 Windows Server 2008
- （不是 SP1？{% post_link tutorial/Windows/NT6upd 点这里看升级教程 %}）

PowerShell
----以下根据你的系统版本来选择----
[Windows 11](https://aka.ms/DownloadWindows11)
[Windows 10](https://aka.ms/DownloadWindows10)
[Windows 8.1](https://www.microsoft.com/zh-cn/software-download/windows8ISO)
[Windows 预览版](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewiso)

## SFC&DISM 命令修复
------

该部分不适用于 Windows 7 SP1 或 Windows Server 2008，请转到[Microsoft Learn](https://learn.microsoft.com/troubleshoot/windows-server/deployment/fix-windows-update-errors)

------

在任意页面按下 Windows 徽标键+X 打开，单击 Windows PowerShell（管理员）（Windows 10）或 Windows 终端（管理员）（Windows 11）
系统版本≤Windows 8.1 或 Windows Server 2012 则需要按下 Windows 徽标键+Q 打开搜索框 ，搜索 PowerShell，并右键以管理员身份运行

### 检查映像是否可修复
扫描映像以检查损坏，此操作将需要几分钟时间
```PowerShell
DISM.exe /Online /Cleanup-Image /ScanHealth
```

检查映像以查看是否检测到任何损坏
```PowerShell
DISM.exe /Online /Cleanup-Image /CheckHealth
```
使用 /CheckHealth 参数时，DISM 工具将报告映像是正常、可修复还是不可修复，如果映像不可修复，则应丢弃映像并重新开始；如果映像是可修复的，则可以使用 /RestoreHealth 参数来修复映像

### 修复损坏的映像
DISM 将通过 Windows Update 来提供修复损坏所需的文件
```PowerShell
DISM.exe /Online /Cleanup-Image /Restorehealth
```

------

如果 Windows Update 功能已损坏或无法启动，请更换修复源
```PowerShell
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:<install.wim 所在路径> /LimitAccess
```
其中，<文件路径>是 install.wim 映像所在的位置
（如何提取 install.wim 请看附录）
比如我将 install.wim 放在了桌面上的 Image 文件夹（使用了相对路径），或者 D 盘的 Image 文件夹，则命令就是
```PowerShell
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:%USERPRIFOLE%\Desktop\Image /LimitAccess
```
或
```PowerShell
DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:D:\Image /LimitAccess
```
完成命令操作可能需要几分钟时间

完成后继续使用 SFC 命令修复镜像
```PowerShell
sfc /SCANNOW
```

### 若只能在 WinRE 下修复
如果你在 WinRE 且进不去系统，发现使用 <code>DISM.exe /Online /Cleanup-Image /RestoreHealth /Source:<文件路径> /LimitAccess</code> 提示“DISM 不支持使用 /Online 选项为 Windows PE 提供服务。”
![WinRE 报错](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem2.png)
所以需要以下的命令
```CMD
DISM.exe /Image:<系统盘盘符> /Cleanup-Image /RestoreHealth /Source:<install.wim 所在路径>
```
若我的系统盘盘符为 C:，且 install.wim 存放在 D 盘的 Image 文件夹，则命令为
```CMD
DISM.exe /Image:C: /Cleanup-Image /RestoreHealth /Source:D:\Image
```
![PE 下修复 Windows](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem1.png)

## 镜像修复
使用镜像根目录下的 Setup 程序对系统进行修复（升级）（所需时间≥45 分钟，好处是可以不升级系统版本的情况下完整地修复系统）
![Setup](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem3.png)
![同意许可协议](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem4.png)
![准备安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem5.png)
![开始安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem6.png)
![正在安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem7.png)
稍等片刻，电脑将重启多次，完成后即可正常使用

## 附录

### 如何提取 install.wim
先用压缩软件解压 ISO 镜像到一个空白文件夹
然后在 sources 文件夹下找到 install.wim 即可
![](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem8.png)
![](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/repairsystem/repairsystem9.png)