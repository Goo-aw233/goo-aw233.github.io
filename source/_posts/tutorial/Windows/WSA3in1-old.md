---
title: 安装 WSA 及其它三件套（旧版）
date: 2022-02-14 22:45:33
categories: 
	- 教程
	- Windows
description: 安装 Windows Subsystem for Android™ 以及 Root,Magisk,GApps 套件
tags: 
	- Windows
	- 软件
cover: https://store-images.s-microsoft.com/image/apps.51780.14545790782662156.958792d4-4b5d-4ce0-8679-8d56984ee999.901bcb54-d2db-4a30-a7ad-391f73965392?mode=scale&q=90&h=270&w=270&background=%230078D7
hidden: true
---

因为原有的库使用太多 GitHub Actions 而被封禁，原库地址：https://github.com/LSPosed/MagiskOnWSA
该教程不确保是否可以正常使用
<font size=5>{% post_link tutorial/Windows/WSA3in1 新版教程链接 %}</font>

------

## 用前说明
按下 <kbd>Windows 徽标键</kbd>+<kbd>R</kbd>，输入<code>optionalfeatures</code> 并回车，在里面选中 <code>Hyper-V</code> 和<code>虚拟机平台</code>
![](https://s2.loli.net/2022/07/30/cMpQnHSKIGFUbuz.png)
[OpenCL 和 OpenGL 扩展包](https://www.microsoft.com/store/productId/9NQPSL29BFFF)
[运行库](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/ErBct6X1MXVDu0gk8zVQucQBmopXB8TOSr21tl4tss5TWw)
[WsaToolbox](https://github.com/makazeu/WsaToolbox)（如果你会使用 ADB 命令可不使用）

------

WSL 显卡驱动（如果是笔记本建议两个显卡都装）
[Intel](https://www.intel.com/content/www/us/en/download/19344/intel-graphics-windows-dch-drivers.html)
[nVIDIA](https://developer.nvidia.com/cuda/wsl)
[AMD](https://www.amd.com/en/support/kb/release-notes/rn-rad-win-wsl-support)

## 下载 WSA 及其它三件套
访问 GitHub 并登陆自己的账户：https://github.com/Goo-aw233/MagiskOnWSA-2
在该页面中点击右上角的 Fork
![](https://s2.loli.net/2022/07/30/eOy6bMIYdV5srcw.png)
等待完成后会跳转到自己的主页，然后点击库下方的 Actions
![](https://s2.loli.net/2022/07/30/CtA8qs2zcxRYyi3.png)
在页面中选择 Build WSA，然后点击右边的 Run workflow，并将里面的内容修改（如果你不懂什么意思可参照下表）
最后点击 Run workflow
![](https://s2.loli.net/2022/07/30/lDxXiS8QPB74OeT.png)

------

Run Workflow 示意图
![](https://s2.loli.net/2022/07/30/DfBHuXNbyMPQc6S.png)
如果无法区分 GApps 应选什么可以参考以下图表（或者看 OpenGApps 的 [Wiki](https://github.com/opengapps/opengapps/wiki#variants)）
![](https://s2.loli.net/2022/07/30/2Ya4D7thuCq53iA.png)

------

运行过程可能有6分钟左右
![](https://s2.loli.net/2022/07/30/sxemKHcZ2bz85Pw.png)
完成后点击 Build WSA
![](https://s2.loli.net/2022/07/30/GgnsXAvJ4mTfl6N.png)
在下面点击构建好的 WSA 即可下载
![](https://s2.loli.net/2022/07/30/yrKQltxfkDioS25.png)
等待一下就开始下载了（单线程会比较慢，早上速度会快点）
![](https://s2.loli.net/2022/07/30/XyYd15EB9Pm3Mjz.png)
下载完后解压到任意路径即可（<font color=yellow size=4>如果你不需要用 WSA 了才可删除该文件夹，所以请选择解压到合适路径</font>）

## 安装
在设置中打开开发者选项
![](https://s2.loli.net/2022/07/30/XjZIwzN5CaUJ8Bs.png)
以<font size=4 color=yellow>管理员身份运行</font> PowerShell 或 Windows Terminal（终端）
然后输入以下命令
````PowerShell
cd <解压路径>
如
cd C:\Program Files\Windows Subsystem for Android
Add-AppxPackage -Register AppxManifest.xml
````
等待一会就安装好了
![](https://s2.loli.net/2022/07/30/nlOPxwCVGaeJhfj.png)

## 完善设置及双击安装包来安装应用

### 完善设置
打开<code>适用于 Android™ 的 Windows 子系统设置</code>
把<code>用于 Android> 的应用的 GPU;</code>改为独立显卡
![](https://s2.loli.net/2022/07/30/ws5nWA9yCxNZ6Dp.png)
然后在旁边的<code>开发人员</code>选项中，把<code>开发人员模式</code>打开
![](https://s2.loli.net/2022/07/30/4xikaAdqg2Cnzpw.png)

### 安装应用
<font color=purple size=4>没吃到那个红利，没给酷安打广告（（（</font>
#### 方法一：用软件安装
打开 WsaToolbox，点击安装APK，再点击选择 APK 并选择你下载好的 apk 文件，最后点击安装 APK
![](https://s2.loli.net/2022/07/30/Hzonj64T9lOEh3u.png)
安装完成后可在开始菜单中找到它们
如果你不想找应用麻烦，可以在[酷安](https://coolapk.com) 自带的应用商店下载

#### 方法二：双击安装应用
在 Microsoft Store 中安装 [APK 安装程序](https://www.microsoft.com/store/productId/9P2JFQ43FPPG)
这样就可以像 appx 那样双击安装了
![](https://s2.loli.net/2022/07/30/bBkn9TxiP3z6Zw2.png)

------

不过可能需要先下载 ADB
![](https://s2.loli.net/2022/07/30/El32OZAGpDYgew4.png)

------