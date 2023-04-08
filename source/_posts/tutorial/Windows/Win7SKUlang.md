---
title: 给 Windows 安装镜像添加语言
date: 2022-09-25 08:40:21
categories: 
	- 教程
	- Windows
tags: Windows
description: 使用 UltraISO 给 Windows 原版镜像添加多国语言
keywords: Windows 7,Win7,Windows,系统镜像,语言
---

## 用前说明
以下文本中，系统/语言包镜像指以 ISO 为后缀的文件；映像是指 install.wim
参考文献：[Microsoft Learn](https://learn.microsoft.com/windows-hardware/manufacture/desktop/add-language-packs-to-windows)
因为先做试验再写文章的原因，文章中部分图片与命令与文本中所打出来的内容不同，请以文本为主

## 创建文件夹并提取所需文件
在 D 盘根目录下创建名为 <code>test</code>的文件夹，然后再在里面创建四个文件夹：<code>mount</code>,<code>Scratch</code>,<code>Image</code>,<code>packages</code>，并在 <code>packages</code> 文件夹下创建名为 <code>zh-cn</code> 的文件夹
用压缩软件打开系统镜像，找到 <code>sources</code> 文件夹下的 install.wim，将其复制到 <code>Image</code> 文件夹下
然后再用压缩软件打开语言包镜像，把你所需要的语言文件复制到 <code>packages\语言名称</code> 下的文件夹
![所需文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SKUlang/Win7SKUlang1.png)

## 装载/卸载映像
右键开始菜单，选择 Windows 终端（管理员）/Windows PowerShell（管理员），二选一即可，因人而异

在 PowerShell 中输入以下内容来挂载映像
````PowerShell
Dism /Mount-Image /ImageFile:D:\test\Image\install.wim /index:1 /MountDir:D:\test\mount
````
进度条跑完后代表挂载映像成功了
![挂载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SKUlang/Win7SKUlang2.png)

在 PowerShell 中输入以下内容来给挂载的映像添加语言包
````PowerShell
Dism /Image:D:\test\mount /ScratchDir:D:\test\Scratch /Add-Package /PackagePath:D:\test\packages\zh-cn\lp.cab

若你要添加多个语言包，就添加多个 /PackagePath:<路径\文件名.cab> 命令标签
如下
Dism /Image:D:\test\mount /ScratchDir:D:\Scratch /Add-Package /PackagePath:D:\test\packages\zh-cn\lp.cab /PackagePath:D:\test\packages\en-uk\lp.cab
````
进度条跑完后代表添加成功了
![添加语言包](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SKUlang/Win7SKUlang3.png)

在 PowerShell 中输入以下内容来给挂载的映像设置默认语言
````PowerShell
Dism /Image:D:\test\mount /Set-SKUIntlDefaults:zh-cn
````
出现“操作成功完成。”代表设置成功
![设置成功](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SKUlang/Win7SKUlang4.png)

在 PowerShell 中输入以下内容来卸载挂载的映像
````PowerShell
Dism /Unmount-Image /MountDir:D:\test\mount /Commit
````
出现“操作成功完成。”代表卸载成功
![卸载成功](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SKUlang/Win7SKUlang5.png)

## 整合镜像
使用 UltraISO（在“资源”——“资源列表”内有）打开你要修改的镜像，并定位到 <code>sources</code> 文件夹
将 install.wim 文件替换进去，并保存（若提示无法保存则直接点击旁边的“另存为”）
![文件替换](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SKUlang/Win7SKUlang6.png)