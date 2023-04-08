---
title: 给电脑重装 Windows
date: 2022-06-19 22:32:39
categories: 
	- 教程
	- Windows
tags: Windows
description: 用 PE 给你电脑重装一个全新、干净、原版的 Microsoft Windows
cover: https://s2.loli.net/2022/08/15/AperUTcuJ18Da62.png
sticky: 95
---

## 用前说明
本教程仅适用于支持 UEFI 的机子
数据无价，请谨慎操作

### 实验环境
[FirPE](https://firpe.cn) （微 PE 也是可以的，但请不要使用垃圾 PE，如果你无法分辨就请使用 FirPE）
[Ventory](https://github.com/ventoy/Ventoy/releases)
Windows 镜像
{% post_link tutorial/Windows/UUP 其它 Windows 下载 %}
[Windows 10 官网](https://aka.ms/DownloadWindows10)
[Windows 11 官网](https://aka.ms/DownloadWindows11)

## 制作 PE
去到下载带有 Windows 字样的 Ventory 文件，并全部解压
解压后运行名为“Ventory2Disk”的软件，并插入你的 U 盘，<font size=4 color=red>备份好 U 盘内所有文件后点击软件内的“安装”按钮</font>（数据无价）
![](https://s2.loli.net/2022/08/15/kpzX3OlUu4TZNmW.png)

------

如果你不需要考虑兼容性的话可以点击“配置选项”——“分区类型”——“GPT”
（无需电脑支持 UEFI，但兼容性会差一些）
![](https://s2.loli.net/2022/08/15/8ysUi31IrlAZdYw.png)

------

完成后去到 [FirPE 官网](https://firpe.cn/page-247)下载安装包
（如果你的硬件不符合 Windows 11 的最低标准，请使用 [Windows 10 版本的 FirPE](https://firpe.horatio.cn/FirPE/1.7.1)）
完成后打开安装包，点击软件右下角的“生成 ISO”
![](https://s2.loli.net/2022/08/15/rHhNdaDZwBLcKPj.png)
在你的 U 盘下新建个名为“PE”（不带引号）的文件夹，并选择把 ISO 放进“PE”文件夹
![](https://s2.loli.net/2022/08/15/udDZc2ogrVaIw8A.png)
等这个提示出现后就完成了
![](https://s2.loli.net/2022/08/15/SQjcuL4FNUdOZp3.png)

------

### 如果你想添加多个 PE
在其它 PE 的安装程序中选择生成 ISO，然后一起放到“PE”文件夹即可
![](https://s2.loli.net/2022/08/15/T5S2uxg17lqEBDQ.png)

------

## 进入 PE
重启电脑，等待黑屏之后按下启动热键进入启动菜单选择
（具体按键因人而异，可以自己搜一下“主板型号\笔记本型号+如何进入启动菜单”或者“主板型号\笔记本型号+如何设置 U 盘启动”）
或者启动时主板 LOGO 下方是否有说明从哪个键可以进入启动菜单
![](https://s2.loli.net/2022/08/15/lLWMoSAmUpE7FVj.png)
选择带 UEFI 字样的 U 盘启动项并回车
如果你不知道怎么更改为 UEFI 启动的话可以自行搜索（格式为“主板厂家名+主板型号+怎么切换 UEFI 启动”或“笔记本型号+怎么切换 UEFI 启动”）
![](https://s2.loli.net/2022/08/15/QiBDJda7UIGznF3.jpg)

------

如果你看到这个提示则需要关闭安全启动，你得自行搜索（格式为“主板厂家名+主板型号+怎么关闭安全启动”或“笔记本型号+怎么关闭安全启动”）
或者看 [Ventory 的教程](https://www.ventoy.net/cn/doc_secure.html)
![](https://s2.loli.net/2022/08/15/ISU3mt5KbwxQjn9.png)

------

在这里选择你做好的 PE 镜像并回车
![](https://s2.loli.net/2022/08/15/cWwiqRYCF5VKMu1.png)
这里的选项随意即可，如果你的显示屏分辨率低就选第二个选项
![](https://s2.loli.net/2022/08/15/qJCywD29NpvWaQo.png)

## 安装系统

### 硬盘分区
点击桌面上的“分区工具 DiskGenius”

------

如果你已经是 GUID 格式硬盘且拥有 MSR/ESP 分区则请跳过该步骤
右击 C 盘分区，点击“拆分分区(C)”
![](https://s2.loli.net/2022/08/15/9sBdqkPrTzeiyA8.png)
将“分区后部的空间：”改为 428MiB，将后面的选项改为“保持空闲”并点击开始
![](https://s2.loli.net/2022/08/15/b3UVuNYRwHdr4QS.png)
有弹窗点击“是”即可
然后右击<font color=red>硬盘</font>，选择“转换分区表类型为 GUID 格式”
![](https://s2.loli.net/2022/08/15/QFpqxElJKXZLsa4.png)
右击新拆分的分区，选择“建立 MSR/ESP 分区”
![](https://s2.loli.net/2022/08/15/FKDxTOqtHpnyWAc.png)
设置保持默认，然后点击确定
![](https://s2.loli.net/2022/08/15/eaIQuGAz358w4Zq.png)
最后点击左上角的“保存更改”
![](https://s2.loli.net/2022/08/15/n8mvhk7YuxHdZ6r.png)
所有弹窗点击“是”即可

------

然后格式化 C 盘
![](https://s2.loli.net/2022/08/15/zlbXJUoVeKrDtj4.png)
![](https://s2.loli.net/2022/08/15/OkIZQ8pNGq2cwgL.png)
所有弹窗点击“是”即可

### 安装系统
点击桌面上的“Dism++”，如果出现报错点击确定即可
![](https://s2.loli.net/2022/07/31/WpUdJbVT3L9nxkH.png)
点击上方的“恢复功能(R)”>“系统还原”
![](https://s2.loli.net/2022/07/31/ZAcasNzxLpt8owQ.png)
在弹出的窗口中点击第一个“浏览”
![](https://s2.loli.net/2022/07/31/DQwvWSLUT5crqYm.png)
选择你已经下载好的系统镜像
![](https://s2.loli.net/2022/08/15/6ajViUKAneSMJGo.png)
点击第二个预览，选择到需要安装到的分区即可，并勾选“添加引导”，目标镜像可自己选择系统版本（如果你想让系统更小，可以勾选“Compact”）
完成后点击“确定”即可开始安装 Microsoft Windows
![](https://s2.loli.net/2022/07/31/d7gQtRfTxo9aLJi.png)
出现以下对话框时点击“确定”即可
![](https://s2.loli.net/2022/07/31/d7gQtRfTxo9aLJi.png)
等待几分钟后 当 Dism++ 出现“C: 映像已经还原成功”则代表系统安装成功，这时可以拔掉 U 盘并重启系统

## 小工具
这些工具可以让你的 Microsoft Windows 更好用
[微软电脑管家（依赖 Microsoft Defender）](https://pcmanager.microsoft.com) | [使用帮助文档](http://t.cn/A6i8xnAx)
[重启资源管理器](https://www.sordum.org/files/downloads.php?st-restart-explorer)（双击“Rexplorer.exe”或“Rexplorer_x64.exe”即可重启）
[软件卸载工具 Geek](https://geekuninstaller.com/geek.zip)
----
以下这些可选择“Menu ...”>“Languages”>“Chinese (Simplified)”来更改语言
[经典 Windows 11 右键菜单](https://www.sordum.org/files/downloads.php?win11-classic-context-menu)
[关闭自带杀毒功能](https://www.sordum.org/files/downloads.php?st-defender-control)（如果有密码，则就是 sordum）
[关闭系统更新](https://www.sordum.org/files/downloads.php?st-windows-update-blocker)（不推荐，因为大部分系统组件会因此无法使用，所以请在必要时才关闭）
## 声明
<font size=1>
封面来源：Wikipedia
<br>由微软公司 - 原始出版物：https://www.microsoft.com/windows/windows-11
<br>直接来源：https://en.wikipedia.org/wiki/File:Windows_11_Desktop.png
<br>合理使用：https://zh.wikipedia.org/w/index.php?curid=7668092</br>
</font>