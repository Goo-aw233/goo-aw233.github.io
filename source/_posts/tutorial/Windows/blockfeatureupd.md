---
title: 屏蔽 Windows 各种更新
date: 2022-11-05 10:44:57
categories: 
	- 教程
	- Windows
tags: Windows
description: 使用 wushowhide.diagcab 阻止 Windows 安装各种更新
cover: https://www.sordum.org/wp-content/uploads/2019/09/wub.png
---

## 用前说明
[wushowhide.diagcab 直链下载](http://download.microsoft.com/download/F/2/2/F22D5FDB-59CD-4275-8C95-1BE17BF70B21/wushowhide.diagcab)

## 屏蔽更新
直接运行 wushowhide.diagcab，并点击“下一步(N)”
![下一步](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd1.png)
等待几分钟，疑难解答程序会自动搜索可用更新
![查找更新](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd2.png)
查找完成后点击“Hide updates”，并勾选你需要屏蔽的更新，并点击“下一步(N)”
（如果没有需要屏蔽的更新可以重启电脑后再次尝试；如果你反悔了想重新获取那个更新就点击“Show hidden updates”）
![Hide updates](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd3.png)
![选择更新](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd4.png)
最后稍等片刻，即可成功屏蔽更新，重启计算机即可
![疑难解答已完成](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd5.png)
在[设置](ms-settings:windowsupdate)里就不会获取到被屏蔽的更新了
（<font size=4 color=red>请不要清理 <code>C:\Windows\SoftwareDistribution</code> 下除 <code>Downloads</code> 的文件（夹），否则需要重新运行 wushowhide.diagcab</font>；如果依旧无效，请看[附录](#附录)）
![更新](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd6.png)

## 附录
按下 <kbd>Windows 徽标键</kbd>+<kbd>R</kbd>，输入 <code>services.msc</code> 并回车
找到名为“Windows Update”或“Windows 更新”的服务，点击旁边的“停止”
![Windows 更新服务](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd7.png)
然后再找到 <code>C:\Windows\SoftwareDistribution</code>，并把里面所有文件（夹）删除
![SoftwareDistribution](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockfeatureupd/blockfeatureupd8.png)
最后到[设置](ms-settings:windowsupdate)里重新获取更新后再运行 wushowhide.diagcab 即可