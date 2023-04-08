---
title: Windows 7 开启安全启动
date: 2022-09-30 19:30:57
categories: 
	- 教程
	- Windows
tags: Windows
description: 给 Windows 7（ES 7）和 Server 2008 R2 启用安全启动
---

## 用前说明

### 补丁包
以下渠道请二选一，OneDrive 是多个打包好的，Microsoft® Update Catalog 则需要自己手动选择合适的分批次下载

#### OneDrive
[OneDrive 下载](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/EuMGGoJihddMnUJrdL_7cOAB5PT2X7AEGU86XuVgMycrgA?e=VhDp2g)

#### Microsoft® Update Catalog
[KB3020369](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3020369)
[KB3125574](https://www.catalog.update.microsoft.com/Search.aspx?q=KB3125574)
[服务堆栈更新](https://catalog.update.microsoft.com/Search.aspx?q=Servicing%20Stack)
[KB5017361](https://www.catalog.update.microsoft.com/Search.aspx?q=KB5017361)

<blockquote>
为什么要安装这么多补丁
</blockquote>

为什么要安装前两个补丁详见 [Microsoft Support](https://support.microsoft.com/topic/%E9%92%88%E5%AF%B9-windows-%E5%92%8C-wsus-%E7%9A%84-2019-sha-2-%E4%BB%A3%E7%A0%81%E7%AD%BE%E5%90%8D%E6%94%AF%E6%8C%81%E8%A6%81%E6%B1%82-64d1c82d-31ee-c273-3930-69a4cde8e64f)
而安装服务堆栈更新则是避免 WSUS.exe 报错
KB5017361 则才是支持安全启动的补丁

------

实际上的话让 Windows Update 安装更新列表里的更新就好了，不用费那么多事
目前为止还没查明少了哪个补丁会导致 KB5017361 无法安装，但如果整个系统只有以上几个补丁（不包括 KB5017361）时，安装完重启后会提示安装失败

------

## 安装补丁
<font size=4 color=red>补丁需要安装请按 1——2——4——3 的顺序进行安装</font>
![补丁列表](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SecureBoot/Win7SecureBoot1.png)
每当有一个补丁安装完成提示重启时请立即重启，否则将会有以下提示
![未安装 SHA-2 集成更新](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SecureBoot/Win7SecureBoot2.png)
![未安装服务堆栈更新](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SecureBoot/Win7SecureBoot3.png)
安装完成后需重启，然后就支持安全启动了

------

Workstation 的 Windows 7 可以通过修改 .vmx 来启用安全启动
找到名为 firmware = "efi" 的项删除，并添加以下代码（在原来代码行的基础上）
firmware = "efi"
uefi.secureBoot.enabled = "TRUE"

------

## 内容变化
KB5017361 更新并重签名了引导文件 bootmgr.efi,bootmgfw.efi 及内核 winload.efi 文件

<blockquote>
数字签名属性（旧）
</blockquote>

![bootmgr.efi 数字签名属性（旧）](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SecureBoot/Win7SecureBoot4.png)
![bootmgfw.efi 数字签名属性（旧）](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SecureBoot/Win7SecureBoot6.png)
![winload.efi 数字签名属性（旧）](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Win7SecureBoot/Win7SecureBoot8.png)

<blockquote>
数字签名属性（新）
</blockquote>

![bootmgr.efi 数字签名属性（新）](5)
![bootmgfw.efi 数字签名属性（新）](7)
![winload.efi 数字签名属性（新）](9)
