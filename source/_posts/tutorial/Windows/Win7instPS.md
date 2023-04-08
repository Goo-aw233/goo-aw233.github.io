---
title: 给 Windows 7 升级 PowerShell
date: 2022-09-18 12:55:53
categories: 
	- 教程
	- Windows
tags: Windows
description: 在 Windows 7 SP1 和 Windows Server 2008 R2 SP1/Home Server 2011 中安装新版 PowerShell
keywords: Windows 7,Win7,PowerShell,PS1,Windows,cmd
---

## 用前说明
该教程仅限于 x86_64 的系统/CPU

## 下载必要组件
从 [Microsoft Learn](https://learn.microsoft.com/powershell/scripting/windows-powershell/install/installing-windows-powershell) 中选择 Windows 7 SP1 和 Windows Server 2008 R2 SP1 字样的安装程序，并选择一个版本点进去（以 WMF 5.1 为例）
![升级现有 Windows PowerShell](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS1.png)
在新标签页中点击“Download”
![下载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS2.png)
然后选择 <code>Win7AndW2K8R2-KB3191566-x64.zip</code>
![正确的包](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS3.png)

## 安装
打开下载好的 <code>Win7AndW2K8R2-KB3191566-x64.zip</code>，把 <code>Win7AndW2K8R2-KB3191566-x64.msu</code> 解压出来并安装
![安装 KB3191566](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS4.png)
完成后点击“立即重新启动”
![重启](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS5.png)
重启后 PowerShell 版本就升级了，在 PowerShell 中输入
````PowerShell
$PSVersionTable
````
即可到查看 PowerShell 版本是新版本
![PowerShell 版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS6.png)

## 后记
或者你也可以直接在 [GitHub](https://github.com/PowerShell/PowerShell/releases) 上下载最新的 PowerShell
![PowerShell Preview](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7instPS/Win7instPS7.png)
能不能用是另一回事（小声