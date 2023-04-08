---
title: 创建无人值守文件
date: 2022-07-11 19:38:00
categories: 
	- 教程
	- Windows
tags: 
	- 软件
	- Windows
description: 利用 Windows SIM 创建自己的 Windows 无人值守文件
---

## 用前说明
参考文献：
[1 Microsoft Learn](https://learn.microsoft.com/windows-hardware/customize/desktop/unattend)
<font size=3 color=yellow>本文应按照文字部分为主，图片部分为辅</font>
### 使用环境
[Windows ADK](https://docs.microsoft.com/zh-cn/windows-hardware/get-started/adk-install)
压缩软件
Windows 系统镜像（[Windows 10 下载](https://www.microsoft.com/software-download/windows10) | [Windows 11 下载](https://www.microsoft.com/software-download/windows11) | [Windows 预览版](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewiso)）
UltraISO（在“资源”——“资源列表”中）

## 安装 Windows System Image Manager
在上面的网站中下载 Windows ADK（需要选择与你系统相符的版本）
![](https://s1.ax1x.com/2022/07/11/jcNYWQ.png)
打开安装包，选择第一个选项并继续
![](https://s1.ax1x.com/2022/07/11/jcNtzj.png)
在这个页面只勾选“部署工具”，然后继续
![](https://s1.ax1x.com/2022/07/11/jcNGFS.png)
完成后打开“开始菜单”——“Windows Kits”，打开“Windows 系统映像管理器”
![](https://s1.ax1x.com/2022/07/11/jcNJJg.png)

## 提取 install.wim
用压缩软件提取出 install.wim
目录在 <code>sources\install.wim</code>
![](https://s1.ax1x.com/2022/07/11/jcN3o8.png)

## 创建无人值守文件
在软件左上角选择“文件(F)"——“选择 Windows 映像(I)”
![](https://s1.ax1x.com/2022/07/11/jcNUQs.png)
选择好 install.wim 并点击“打开(O)”

------

如果出现是否需要创建编录文件时，点击“是”即可
![](https://s1.ax1x.com/2022/07/11/jcNayn.png)
然后等待三分钟左右即可

------

在“应答文件”的框内右键，选择“新建应答文件(N)... Ctrl+N”
![](https://s1.ax1x.com/2022/07/11/jcNdLq.png)

PS：为了更直观，每个大项将单独成为一个子章节

### ①
在“Windows 映像”——“Components”文件夹下找到名为 <code>amd64_Microsoft-Windows-International-Core-WinPE_xx.x.xxxxx.x_neutral</code> 的项，并右键，选择“添加设置以传送 1 Windows PE(1)”，<code>amd64_Microsoft-Windows-Setup_xx.x.xxxxx.x_neutral</code> 也是如此
![](https://s1.ax1x.com/2022/07/11/jcNBwV.png)
在“应答文件”的框中单击选择名为 <code>amd64_Microsoft-Windows-International-Core-WinPE_neutral</code> 的项，并在右边“个属性”框中修改以下设置
![](https://s1.ax1x.com/2022/07/11/jcN0e0.png)
其中 <code>zh-CN</code> 是语言，你也可以设置为 <code>en-US</code> 或其它，“LayerDriver”是多少个键盘种类，默认 1 即可
![](https://s1.ax1x.com/2022/07/11/jcN0e0.png)
然后展开子项，选择“SetupUILanguage”，在右边的“个属性”框中，设置为 <code>zh-CN</code>（同样你可以也改为别的），“WillShouUI”这里不做解释，默认即可
![](https://s1.ax1x.com/2022/07/11/jcNDoT.png)

### ②
在“应答文件”的框中单击选择名为 <code>amd64_Microsoft-Windows-Setup_neutral</code> 的项，并在右边“个属性”框中修改以下设置
![](https://s1.ax1x.com/2022/07/11/jcNsFU.png)
其中 “EnableFirewall” 是启动 PE 下的防火墙，“EnableNetwork” 是启动 PE 下的网络连接，“Restart” 是安装完成后 PE 会自动重启，“UseConfigurationSet” 是安装 Windows 的过程中自动寻找适用的驱动（不是 OOBE 界面）
然后展开子项，选择“UserData”，将“AcceptEula”修改为 <code>true</code>（<font size=3 color=yellow>FullName 不需要填写，写到文章结尾的时候才发现的问题（（</font>）
![](https://s1.ax1x.com/2022/07/11/jcNyYF.png)

### ③
在“Windows 映像”——“Components”文件夹下找到名为 <code>amd64_Microsoft-Windows-Security-SPP-UX_xx.x.xxxxx.x_neutral</code> 的项，并右键，选择“添加设置以传送 4 specialize(4)”
![](https://s1.ax1x.com/2022/07/11/jcN6W4.png)
在“应答文件”的框中单击选择名为 <code>amd64_Microsoft-Windows-Security-SPP-UX_neutral</code> 的项，并在右边“个属性”框中修改以下设置
![](https://s1.ax1x.com/2022/07/11/jcNgSJ.png)
其中“SkipAutoActivation”是否自动跳过激活页面

### ④
在“Windows 映像”——“Components”文件夹下找到名为 <code>amd64_Microsoft-Windows-International-Core_xx.x.xxxxx.x_neutral</code> 的项，并右键，选择“添加设置以传送 5 oobeSystem(5)”，<code>amd64_Microsoft-Windows-Shell-Setup_xx.x.xxxxx.x_neutral</code> 也是如此
![](https://s1.ax1x.com/2022/07/11/jcyq5n.png)
在“应答文件”的框中单击选择名为 <code>amd64_Microsoft-Windows-International-Core_neutral</code> 的项，并在右边“个属性”框中修改以下设置（同样你可以也改为别的）
![](https://s1.ax1x.com/2022/07/11/jcyHEj.png)

在“应答文件”的框中单击选择名为 <code>amd64_Microsoft-Windows-Shell-Setup_neutral</code> 的项，并在右边“个属性”框中修改以下设置
![](https://s1.ax1x.com/2022/07/11/jcybUs.png)
其中“BluetoothTaskbarIconEnabled”是否在任务栏显示蓝牙图标，“DisableAutoDaylightTimeSet”设定系统时间为当地时区，“RegisteredOwner”是你要起的用户名（应该为 Administrator），“ShowWindowsLive”保持留空，“TimeZone”设定时区为中国（UTC+8）

展开子项，选择“AutoLogon”，并在右边“个属性”框中修改以下设置
![](https://s1.ax1x.com/2022/07/11/jcyOCq.png)
其中“Enabled”是否自动登录，“LogonCount”设置指定帐户的使用次数，“Username”设置指定用于自动登录的用户帐户名（Administrator）
选择“Password”子项，在右边“个属性”的“Value”值右键，选择“写入空字符串(S)”，“UserAccounts”——“AdministratorPassword”的项也是如此
![](https://s1.ax1x.com/2022/07/11/jcyTbQ.png)

点击“OOBE”子项，并在右边“个属性”框中修改以下设置
![](https://s1.ax1x.com/2022/07/11/jcyX80.png)
其中，“HideEULAPage”是隐藏许可条款，“HideLocalAccountScreen”是隐藏管理员密码屏幕，“HideOEMRegistrationScreen”是隐藏 OEM 注册页，“HideOnlineAccountScreens”隐藏登录页，“HideWirelessSetupInOOBE”隐藏 Windows 欢迎屏幕，“UnattendEnableRetailDemo”禁用零售演示模式

### ⑤
完成以上工作后，只留下这些项，其它多余的需要按 Delete 键来删除它们
![](https://s1.ax1x.com/2022/07/11/jcyj2V.png)
然后同时按下 <kbd>Ctrl</kbd>与<kbd>S</kbd> 键，重命名为 <code>Autounattend</code> 并保存它

最后点击“工具(I)”——“验证应答文件(V)”
![](https://s1.ax1x.com/2022/07/11/jcyvvT.png)
如果下面没有报错就表明正常使用
![](https://s1.ax1x.com/2022/07/11/jcyzKU.png)

## 使用无人值守文件
使用“UltraISO”打开系统镜像，并把“Autounattend.xml”文件放到根目录下
![](https://s1.ax1x.com/2022/07/11/jc6SrF.png)