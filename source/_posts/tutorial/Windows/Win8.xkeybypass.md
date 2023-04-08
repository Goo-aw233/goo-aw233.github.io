---
title: 跳过 Windows 8.x 安装输入密钥
date: 2022-05-14 13:23:34
categories: 
	- 教程
	- Windows
tags: Windows
description: 修改 ISO 添加 ei.cfg 以跳过 Windows 8.x 在安装时输入密钥的过程
top_img: https://c.s-microsoft.com/zh-cn/CMSImages/windows8-laptop.png?version=baa869f1-5f37-dd0a-3498-dd5e7692a9f7
cover: https://c.s-microsoft.com/zh-cn/CMSImages/windows8-laptop.png?version=baa869f1-5f37-dd0a-3498-dd5e7692a9f7
---

## 创建文件
创建一个名为 <code>ei.cfg</code> 的文件并在里面输入以下内容
````
[EditionID]
Professional
[Channel]
Volume
[VL]
1
````
（注释如图)
![](https://s2.loli.net/2022/07/31/TsBKymNFhfCWOX7.png)

## 加载文件
使用 UltraISO（如果没有可以到资源列表里找） 打开 Windows 8.x 的镜像
打开 sources 文件夹，把 <code>ei.cfg</code> 拖进去
保存即可
![](https://s2.loli.net/2022/07/31/8j7CAgDxbzTE1io.png)
效果：![](https://s2.loli.net/2022/07/31/MOm1rsNTjkwctGA.png)