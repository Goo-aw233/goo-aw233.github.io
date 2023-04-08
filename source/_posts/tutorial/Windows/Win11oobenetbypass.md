---
title: Windows 11 激活跳过联网
date: 2022-08-05 10:24:57
categories: 
	- 教程
	- Windows
tags: Windows
description: 使用命令行跳过 Windows 11 开箱体验的联网过程或使用离线账户
---

在 Windows 进入开箱体验（OOBE）阶段时同时按下 <kbd>Shift</kbd> 和 <kbd>F10</kbd> 来打开 CMD 窗口
并在窗口输入以下内容并回车
````cmd
OOBE\BypassNRO.cmd
````
![是英文不是数字](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass1.png)
完成后系统会自动重启
重启的期间需要<code>网线移除</code>
重启之后就会有“我没有 Internet 连接”的选项
![前](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass2.png)
![后](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass3.png)

这样就可以不联网或使用离线账户了
![](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass4.png)

如果没有 BypassNRO 这个文件的话可以先输入 <code>explorer</code> 并回车，在弹出的窗口中选择 C 盘
![资源管理器](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass5.png)
在根目录下新建个文本文档，重命名为 pass.cmd
![创建脚本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass6.png)
右键它，选择“编辑”
![编辑文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win11oobenetbypass/Win11oobenetbypass7.png)
并在 cmd 里输入以下内容
````cmd
@echo off
reg add HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE /v BypassNRO /t REG_DWORD /d 1 /f
shutdown /r /t 0
````
保存后直接运行即可