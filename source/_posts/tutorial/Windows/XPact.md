---
title: Windows XP 不激活无法进入桌面
date: 2022-05-08 01:08:45
categories: 
	- 教程
	- Windows
description: 在安全模式下修复 Windows XP 没激活时无法进入桌面
tags: Windows
top_img: https://static.itellyou.cn/images/windows_xp/pic1.webp
cover: https://static.itellyou.cn/images/windows_xp/pic1.webp
---

## 进入安全模式
强制重启两次，在模式选择界面选择“安全模式”
![](https://s2.loli.net/2022/07/31/QAJ6EHnvBKi9go7.png)
然后选择“Administrator”（如果没有就选择自己的用户名）
![](https://s2.loli.net/2022/07/31/nScLv8GN5rjJ3Kb.png)
点击“是”即可
![](https://s2.loli.net/2022/07/31/wRcldGCgWzXULFx.png)

## 重置激活
在安全模式下打开“开始菜单”，点击旁边的“运行(R)...”
![](https://s2.loli.net/2022/07/31/PT9RhKrYuLpxWgk.png)
然后在里面输入 <code>cmd</code> 并回车
![](https://s2.loli.net/2022/07/31/RBkJpqDmQPgoAOs.png)
然后在 cmd 里输入以下命令（区分大小写），然后回车（区分大小写）
````cmd
rundll32.exe syssetup,SetupOobeBnk
````
完成后重启电脑
![](https://s2.loli.net/2022/07/31/9vwMBi5xZaNzlbj.png)
然后就可以成功进入系统了
不过会重置回30天后必须激活
![](https://s2.loli.net/2022/07/31/qBfEcjUvXPbTdIV.png)