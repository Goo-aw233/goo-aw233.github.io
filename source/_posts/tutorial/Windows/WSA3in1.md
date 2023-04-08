---
title: 安装 WSA 及其它三件套
date: 2022-02-14 22:45:34
categories: 
	- 教程
	- Windows
description: 安装 Windows Subsystem for Android™ 以及 Root,Magisk,GApps 套件
tags: 
	- Windows
	- 软件
cover: https://store-images.s-microsoft.com/image/apps.51780.14545790782662156.958792d4-4b5d-4ce0-8679-8d56984ee999.901bcb54-d2db-4a30-a7ad-391f73965392?mode=scale&q=90&h=270&w=270&background=%230078D7
sticky: 97
---

## 前言
<font size=5>{% post_link tutorial/Windows/WSA3in1-old 旧版教程链接 %}</font>
得益于 GitHub Actions 的限制，现在构建 WSA 需要自己从 Linux 中构建
你可以自己在 VMware Workstation 或其它虚拟机中安装 Ubuntu、Debian 或 OpenSUSE 的 Linux 发行版（其它发行版需要自行安装依赖，本文不作示范）

------

再或者是使用 WSL2，安装教程如下：（使用教程自行搜索）
```
#基础教程：在 PowerShell 中使用默认安装（Ubuntu）
wsl --install

#高级教程：选择自定义 Linux 发行版
#在 PowerShell 中列出可用 Linux 发行版
wsl --list --online
#安装可用 Linux 发行版（将 <Distribution Name> 替换为要安装的发行版的名称(NAME)）
wsl --install -d <Distribution Name>
```

------

详情请看帮助文档 [README.md](https://github.com/LSPosed/MagiskOnWSALocal)

## 在 Linux 中构建 WSA
以下所有过程最好挂着代理，否则你的下载速度会出奇的慢
[配置过程](https://www.bing.com/search?q=Linux+%E7%BB%88%E7%AB%AF%E8%B5%B0%E4%BB%A3%E7%90%86)请自行搜索

### 下载文件
安装 Linux 发行版不是本文的要点，所以这里直接略过（
<font color=red size=4>TIPS：请确保磁盘剩余空间 ≥5GiB</font>
在任意文件夹右键，选择“在终端打开(E)”（WSL2 直接运行下面的命令即可）
![在终端打开](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-1.png)
在终端内输入以下命令以安装 Git（输入密码的过程默认不显示密码）
在“您希望继续执行吗？ [Y/n]”中输入 Y
```Bash
sudo apt install git
```
![安装 Git](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-2.png)
从 GitHub 中下载 MagiskOnWSALocal（SSH 还需要登录到 GitHub，索性使用 HTTP 进行下载）
```Bash
git clone https://github.com/LSPosed/MagiskOnWSALocal.git
```
![GitHub 中下载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-3.png)
切换到下载目录，并运行构建脚本
```Bash
sudo ./MagiskOnWSALocal/scripts/run.sh
```
![运行](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-4.png)
等待几分钟，脚本会自动下载所需的文件

### 构建
用上下方向键选择你需要的选项，按下空格确认选择，按下回车继续下一步

选择你需要的系统架构（正常情况下默认 x64 即可）
![架构](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-5.png)
选择 WSA 的版本
Retail=正式版 | Release Preview=预发布版 | Insider Slow=Beta 版 | Insider Fast=Dev 版
稳定性依次递减，功能性依次递增
![WSA 版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-6.png)
选择 Magisk 版本
Stable=正式版 | Beta=Beta 版 | Canary=Canary 版 | Debug=测试版
稳定性依次递减，功能性依次递增
![Magisk 版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-7.png)
选择是否安装 GApps
![安装 GApps](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-8.png)
选择要安装的 GApps 版本（一般选择 OpenGApps，MindTheGapps 没用过所以不选（硬核））
如果你需要选择 OpenGApps 的版本，请参阅 [Wiki](https://github.com/LSPosed/MagiskOnWSALocal/blob/main/Custom-GApps.md)
![GApps 版本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-9.png)
选择是否保留亚马逊应用商店
![亚马逊应用商店](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-10.png)
选择是否进行 Root，none 为否
![Root](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-11.png)
选择是否将构建的 WSA 进行压缩
![压缩](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-12.png)
->选择压缩格式（7z 速度慢但压缩率高 zip 快但压缩率一般）
![压缩格式](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-12-1.png)
完成后将开始下载所需文件、构建并压缩
![构建](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-13.png)
耐心等待，终端会长时间处于 <code>Redirecting to https://raw.githubusercontent.com/topjohnwu/magisk-files/25.2/app-release.apk</code>，但如果仍有下载进度则代表没问题，否则请检查网络并重新运行 <code>run.sh</code>
![下载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-14.png)

------

OpenGApps 从 SourceForge 下载是真的慢-。-
![下载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-15.png)

------

下载完成后就开始构建 WSA 了
![构建](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-16.png)
构建完成后，输出的文件在 <code>/MagiskOnWSALocal/output</code> 文件夹下
![输出](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-17.png)

## 安装 WSA
在任意目录新建文件夹并重命名，打开压缩包和里面的第一个文件夹，将所有内容复制到新建文件夹内
![复制文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-18.png)

------

如果你之前安装过 MagiskOnWSA，则不必担心你的数据会丢失
但如果你是安装了原版的 WSA，请将 <code>%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache</code> 下的 <code>userdata.vhdx</code> 备份

------

解压完成后，双击运行目录下的 <code>Run.cmd</code> 即可自动安装
![安装脚本](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-19.png)
在 UAC 弹窗出现时需要点击“是”（部分系统默认关闭该设置，无需理会）
![UAC](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-20.png)
然后就会开始安装
![安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-21.png)
完成后按下 <kbd>Windows 徽标键</kbd>+<kbd>R</kbd> 打开“运行”，输入 <code>OptionalFeatures</code> 回车
然后将“Hyper-V”与“虚拟机平台”这两个功能勾选并重启
![必选组件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-22.png)

## 其它问题
还是那句话，详情请看帮助文档 [README.md](https://github.com/LSPosed/MagiskOnWSALocal)（）
### 如何卸载 WSA
直接在开始菜单右键选择“卸载”，然后再将安装文件夹删除即可
![卸载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WSA3in1/WSA3in1-23.png)

### 如何升级 WSA/Magisk
请先删除 WSA 所在的文件夹，然后按照上面的方法重新下载，构建 WSA，你的所有数据会保留