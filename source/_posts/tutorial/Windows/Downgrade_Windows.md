---
title: 降级 Windows
date: 2023-02-01 23:10:24
categories: 
	- 教程
	- Windows
tags: Windows
description: 通过替换镜像内的文件使 setup 正常降级系统
---

替换 <code>setuphost.exe</code> 之前，Setup 无法正常保留文件降级系统
![无法保留文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Downgrade_Windows/Downgrade_Windows1.png)

使用 UltraISO（“网站”——“资源列表”），将新版本镜像内 <code>sources</code> 文件夹下的 <code>setuphost.exe</code> 文件，替换到旧版本镜像，并保存
![替换文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Downgrade_Windows/Downgrade_Windows2.png)

不知道镜像从哪下请看 {% post_link tutorial/Windows/UUP '使用 UUP 构建 Windows 镜像' %}

------

**如果无法保存**
(没有截图，凑合看吧（)
将旧版本镜像内所有内容解压，点击 UltraISO 上方“启动”——“保存引导文件...”，随意存放到一个位置
<br>将新版本镜像内 <code>sources</code> 文件夹下的 <code>setuphost.exe</code> 文件复制出来替换
<br>用 UltraISO 新建镜像，将旧版本镜像内所有文件复制进去，点击 UltraISO 上方“启动”——“加载引导文件...”，并选择刚刚保存的引导文件，最后点击保存即可

---

替换完成后就可以保留文件降级 Windows 了
![准备就绪](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Downgrade_Windows/Downgrade_Windows3.png)
![安装 1](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Downgrade_Windows/Downgrade_Windows4.png)
![安装 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Downgrade_Windows/Downgrade_Windows5.png)

最后就可以正常使用（可能会出现一些奇奇怪怪的 Bug）
![效果](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Downgrade_Windows/Downgrade_Windows6.png)