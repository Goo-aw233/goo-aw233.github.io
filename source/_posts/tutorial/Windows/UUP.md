---
title: 使用 UUP 构建 Windows 镜像
date: 2022-05-03 03:24:54
categories: 
 - 教程
 - Windows
description: 使用 UUPDump、uup.rg-adguard 构建正式版/预览版系统镜像
tags: Windows
cover: https://uup.rg-adguard.net/img/win10_1700.png
sticky: 94
---

## UUPDump
### 正文

[UUPDump](https://uupdump.net/?lang=zh-cn)
[UUPDump 中文站](https://www.uupdump.cn)

白色矩形框中可以输入你想要查找的 Windows 版本，如 22621，22H2 或者 Windows 11
红色矩形框内可以快速选择你要下载的渠道，顺序依次为：正式版、预发布版（Release Preview）、Beta、Dev，稳定性依次递减，功能选择性依次递增
草绿色矩形框内选择的是组合更新，或者其它的更新等

列表内对应的注释如下：
<li><font color=green>带有 Insider Preview 字样的是预览版，不带则是正式版；排序越往上，版本越新</font></li>
<li><font color=yellow>x64 适用于普通计算机；arm64 则适用于 Surface Pro X、Raspberry Pi、Apple M 等 ARM64 设备</font></li>
<li><font color=green>①：Cumulative Update 为组合更新，会有功能与安全上的更新<br>②：Feature update 是质量更新，仅有安全上的更新<br>③：Update Stack Package 为服务堆栈更新，目前仅面向预览通道，会有功能、安全以及系统文件等的更新<br>④：Update for Windows Feature Experience Pack 为功能体验包，一说是 UI 更新等，是普通的补丁更新<br>⑤：Update for Windows 为普通的补丁更新</br></font></li>

![UUPDump](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP1.png)

在列表内点击所需更新的名称以继续
![列表](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP2.png)

左侧白色矩形框内选择语言，点击下一步
右侧黄色矩形框的作用请转到[附录](#文件查找)
![选择语言](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP3.png)

左侧红色矩形框选择你要下载的版本，一般<font color=green>只选择</font> Windows Pro 即可（除非你需要家庭版（中文版）才选择 Windows Home 或 Windows Home China）
右侧“虚拟升级版本”指明了对应的版本需要勾选什么
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP4.png)

左侧白色矩形框中选择第二或第三个都可以<br>选择第二个默认只输出专业版、家庭版（中文版）、和 Team 版（需要在上一页勾选才出现）<br>选择第三个则会出现草绿色矩形框所显示的内容，根据自己的选择勾选或取消自己需要或不需要的版本</br>
<font color=red>酒红色矩形框内是构建该镜像时要求的 Windows 版本，低于最低要求会构建出一个错误的镜像</font>
![选择内容](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP5.png)
大红色矩形框内选择转换选项
第一个是集成更新（必勾选，否则构建出的版本会是初始版本（比如 22621.1，而不是带有功能更新的 22623 这种）
BEFORE 是安装补丁前的 Windows 版本，AFTER 是安装后的版本
第二个是清理集成更新后产生的缓存文件（或许包括 WinSxS）
第三个是集成 .NET Framework 3.5
第四个是将 .wim 镜像转换为 .esd
![集成更新](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP5.1.png)

点击“创建下载包”后就会下载一个压缩包，需要将里面所有文件（夹）解压到一个空白的文件夹
![解压下载包](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP6.png)

双击打开 <code>uup_download_windows.cmd</code>，然后就会开始下载并构建 Windows 镜像
![下载镜像](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP7.png)
等到 cmd 界面变蓝时则代表开始集成 MetroUI APP、补丁和构建镜像
![集成 MetroUI APP](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP8.png)
![集成补丁](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP9.png)
![构建镜像](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP10.png)
完成后按 <kbd>0</kbd> 即可退出，然后构建出的镜像就在下载包文件夹的根目录
![退出构建，镜像位置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP11.png)

### 文件查找
输入你要查找的文件名，可以是内置在系统里的 MetroUI APP 或者 .cab 等其它文件
![文件查找](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP12.png)

## uup.rg-adguard
[uup.rg-adguard](https://uup.rg-adguard.net)
第一个框选择渠道类型
<del>解释如图例，Windows 11 的正式版与预览版包含在 <code>Windows (Insider version)</code></del> Windows 11 的正式版已迁移到 <code>Windows (Final version)</code>
![渠道类型](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP13.png)
第二个选择 Windows 的版本
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP14.png)
第三个选择系统语言
![选择语言](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP15.png)
第四个选择系统版本
![选择版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP16.png)
第五个里选择第一个项，然后点击右边的 <code>multi_creatingISO...</code> 来下载创建脚本
![下载脚本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP17.png)
点击三个点，选择“保留”——“显示详细信息”——“仍然保留”
![保留](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP18.png)
![仍然保留](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP19.png)
最后打开脚本即可开始下载

中文对应如下，输入开头的字母并回车即可开启或关闭该功能，完成后按 <kbd>Enter</kbd> 继续下一步
ON 为选择，OFF 为反选
![脚本内中文翻译](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP20.png)

------

输入阿拉伯字符并回车即可选择要加载的语言，DEF 为默认选择，ON 为选择，OFF 为反选，完成后按 <kbd>Enter</kbd> 继续下一步
![选择语言](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP21.png)

------

等待一会，开始下载并构建镜像
![下载文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP22.png)
![构建镜像](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP23.png)

完成后按任意键退出，然后构建出的镜像与下载脚本在同目录
![完成](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/UUP/UUP24.png)