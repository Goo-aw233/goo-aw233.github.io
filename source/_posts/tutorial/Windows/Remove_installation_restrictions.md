---
title: 移除 Appx 的安装限制
date: 2023-01-12 19:54:10
categories: 
	- 教程
	- Windows
description: 通过修改 AppxManifest.xml 来移除 Appx 对 Windows 版本的安装限制
tags: 
	- Windows
	- 软件
---

类似于 Apple Music 这样，把安装的版本限制在 Windows 11 22621.0 以上
![要求版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions1.png)
而在低于 Windows 11 22621.0 的系统则会无法安装该软件
![报错](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions2.png)

## 下载包
首先在 Microsoft Store 里获取软件的链接
“分享链接”——“复制链接”
![获取链接](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions3.png)
随后在 https://store.rg-adguard.net 中粘贴链接并下载你需要的软件包，<font color=yellow>以及下面所提供的，与你系统相匹配的运行库（一般选带有 x64 的即可）</font>
![获取包](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions4.png)

## 修改包
使用 [7-Zip](https://7-zip.org)、[Bandizip](https://www.bandisoft.com/bandizip) 等解压缩软件打开软件包，并将其<font color=red>全部解压到空白文件夹内（因为不再将其打包成 Appx，故不能再移动文件夹）</font>

------

正常来说，下载好的 Appx 内还会有几个安装包
正常情况下需要再次解压最大的安装包到空白文件夹
注意需要辨别里面的包是 <code>ARM64</code>、<code>x64</code> 还是 <code>x86</code>，一般只需要 x64

------

![解压](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions5.png)
使用记事本或其它文本编辑工具打开文件夹内的 <code>AppxManifest.xml</code>
按下 <kbd>Ctrl</kbd>+<kbd>F</kbd> 打开“搜索”，并输入 <code>TargetDeviceFamily</code>，将所有结果里带引号 <code>"</code> 里的版本号更改为你的系统版本号并保存

<blockquote>
只需要更改 Name="Windows.Desktop" 那一行里 10.0 之后的数字
<br>查看系统版本号如下：
<br>按下 Windows 徽标键+R，打开“运行”，输入“winver”（不包括引号）并回车
<br>在第二行的括号内，“OS 内部版本”之后的那一串字符则为你的系统版本号
<br>如果你嫌事多可以直接改成 10.0.19041.0，前提是你的系统版本≥Windows 10 2004</br>
</blockquote>

**TIPS：然后将目录里 <code>AppxMetadata</code> 文件夹、<code>[Content_Types].xml</code>、<code>AppxBlockMap.xml</code> 和 <code>AppxSignature.p7x</code> 给删除**

![查找内容并更改](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions6.png)
在[设置](ms-settings:developers)中打开“开发人员模式”
![开发者模式](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions7.png)
按下 <kbd>Windows 徽标键</kbd>+<kbd>Q</kbd>，输入“PowerShell”，右键选择“以管理员身份运行”
![打开 PowerShell](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions8.png)
在 PowerShell 中输入以下命令
```PowerShell
cd "<AppxManifest.xml 所在路径>"
# 比如我的路径在 C:\Program Files\AM 则命令为
cd "C:\Program Files\AM"
```
![复制路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions9.png)
```PowerShell
Add-AppxPackage -Register .\AppxManifest.xml
```
![输入命令](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions10.png)
如果没有缺少相对应的软件运行库，则只需几秒钟即可完成安装
![安装完成](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions11.png)
一般来说 Windows 10 2004 以上都可以正常运行（毕竟大部分运行库最低要求都得 1809，且 2004 为 Windows 10 的最后一个内核大更新）
![运行 Apple Music](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/Remove_installation_restrictions/Remove_installation_restrictions12.png)