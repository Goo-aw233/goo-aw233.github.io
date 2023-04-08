---
title: 备份 Windows 10/11 的 UWP 应用
date: 2022-04-04 13:58:45
categories: 
	- 教程
	- Windows
tags: 
	- 软件
	- Windows
description: 用 WSAppBak 把 UWP 软件打包成 APPX
---

## 用前说明

### 实验环境（仅限 Windows 10 及更高版本）
[WSAppBak](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Ep3mNuzhlktHn3j5OlKAAcMBhj1mf-t41_3sUo2El8b7dg?e=R0NiLK)

## 提取 APPX
先运行你要提取的软件，然后打开“任务管理器”并点开下方的“详细信息(D)”
展开软件项，右击主程序，选择“打开文件所在的位置(O)”
![获取安装路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak1.png)

------

### 如果权限不足
就像这样
![无权访问文件夹](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak2.png)
点击继续
出现拒绝访问文件夹，点击“安全选项卡”
![安全选项卡](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak3.png)
然后点击“高级(V)”
![获取权限](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak4.png)
然后点击上方的“更改(C)”
![更改权限](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak5.png)
然后输入你电脑的用户名，完成后点击“确定”
![更改所有者](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak6.png)
然后再点击“确定”
![确定更改](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak7.png)
把所有资源管理器窗口退出后出现在“任务管理器”选择“打开文件所在位置”
再次出现弹窗点击“确定”即可
![打开位置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak1.png)
然后就可以正常访问了
![安装路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak8.png)

------

### 正常情况
在新打开的窗口中会自动选中文件夹，双击点开它
![安装路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak9.png)
然后右键单击地址栏的空白处，选择“复制地址(C)”
![复制地址](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak10.png)
打开“WSAppBak”，单击右键将地址粘贴进去然后回车
接着再输入（粘贴）要输出的文件夹，再回车
![粘贴路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak11.png)
等待一下就开始跑代码
完成后会出现弹窗，让你<font color=yellow>自定义密码，但你可以直接点击“OK”来跳过密码</font>
![自定义密码](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak12.png)
空白密码则会再询问你，点击“是(Y)”即可
![确认空密码](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak13.png)
等待一会，出现“Press any Key to exit.... :)”的时候按任意键即可退出
![按任意键退出](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak14.png)

## 信任证书并安装 APPX

### 正常情况
找到打包好的文件，左键单击选择它，然后右键选择“属性(R)”
![属性](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak15.png)
在弹出的窗口中点击“数字签名”，选中证书双击，在新窗口点击“查看证书(V)”，然后在最后弹出的窗口点击“安装证书(I)”
![信任证书](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak16.png)
选择“本地计算机(L)”，然后点击“下一步(N)”
![选择位置](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak17.png)
出现 UAC 弹窗点击是
![信任 UAC](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak17.1.png)
选择“将所有的证书都放入下列存储(P)”，点击“浏览(L)”，选择“受信任的根证书颁发机构”，点击“确定”，然后“下一步”
![选择存放目录](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak18.png)
在最后的窗口点击“完成(F)”
![完成](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak19.png)
然后就导入成功了
![成功](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak20.png)
最后双击打开 APPX 安装包即可安装软件
![安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak21.png)
----
### 如果你是 LTS 或没有 AppInstall 的 Windows
在信任完证书后，将 APPX 安装包拖到“WSAppPkgIns”上即可安装
![安装 Appx](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak22.png)
<font color=green>当然你也可以用 Add-AppxPackage 安装，<del>那样会显得你很懂</del></font>
如果缺少运行库或版本不符合的话可能会无法正常安装（命令行安装不会自动补全运行库）
![报错](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/appxbak/appxbak22.png)