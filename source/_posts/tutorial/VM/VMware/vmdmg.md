---
title: Workstation 用 DMG 镜像安装 macOS
date: 2022-02-13 22:52:13
categories: 
	- [虚拟机,VMware,Workstation]
	- [教程,macOS]
tags:
	- VMware Workstation
	- macOS
description: 在 VMware Workstation 下用 DMG 镜像和其他工具引导进系统安装界面
cover: https://www.apple.com.cn/v/mac/home/bk/images/overview/monterey/tile_monterey__bm1x7sttegty_large.jpg
---

## 用前说明

### 把话说在前面
macRecovery 是从 Apple 服务器下载镜像，安装速度因人而异
方法启发于[知乎](https://zhuanlan.zhihu.com/p/130692555)
如果安装 macOS Big Sur 或更高版本安装时出现更新错误之类的报错，请把以下代码添加到 vmx 文件的最末端
（取自[黑苹果星球](https://heipg.cn/tutorial/install-macos-by-using-vmware-in-windows.html)）
````VMX
board-id = "Mac-7BA5B2D9E42DDD94"
hw.model = "iMacPro1,1"
uuid.action = "keep"
smc.version = "0"
````

### 实验环境
[Python](https://www.python.org)
[Etcher](https://github.com/balena-io/etcher/releases/tag/v1.4.9) （建议选带 Portable 的版本）
DMG 镜像

------

如果没有DMG 镜像可在下面截取命令来获取
先下载 [OpenCore](https://github.com/acidanthera/OpenCorePkg/releases)
将压缩包解压后在 \Utilities\macrecovery 下按住 Shift 不放然后单击右键选择 PowerShell
（Windows 11 或安装终端的 Windows 10 可以直接右键选择 Open in Terminal）
下载好的镜像在 macrecovery 目录
````PowerShell
10.7:（实测不能用）
python macrecovery.py -b Mac-2E6FAB96566FE58C -m 00000000000F25Y00 download

10.8:
python macrecovery.py -b Mac-7DF2A3B5E5D671ED -m 00000000000F65100 download

10.9:
python macrecovery.py -b Mac-F60DEB81FF30ACF6 -m 00000000000FNN100 download

10.10:
python macrecovery.py -b Mac-E43C1C25D4880AD6 -m 00000000000GDVW00 download

10.11:
python macrecovery.py -b Mac-FFE5EF870D7BA81A -m 00000000000GQRX00 download

10.12:
python macrecovery.py -b Mac-77F17D7DA9285301 -m 00000000000J0DX00 download

10.13：
python macrecovery.py -b Mac-7BA5B2D9E42DDD94 -m 00000000000J80300 download

10.14：
python macrecovery.py -b Mac-7BA5B2DFE22DDD8C -m 00000000000KXPG00 download

10.15：
python macrecovery.py -b Mac-00BE6ED71E35EB86 -m 00000000000000000 download

11：
python macrecovery.py -b Mac-E43C1C25D4880AD6 -m 00000000000000000 download

（如果是 macOS 或 Linux 则需要在 macrecovery.py 前加上 .\）
更多下载可参考 GitHub：https://github.com/acidanthera/OpenCorePkg/blob/master/Utilities/macrecovery/recovery_urls.txt
````

------

## 创建虚拟硬盘
同时按下 Windows 徽标键 和 R 键打开运行，然后输入 diskmgmt.msc 并回车
在打开的窗口中选择 操作–创建 VHD
![](https://s2.loli.net/2022/07/30/UxSc1EKbPjIGCld.png)
位置随意，如果是完整的镜像推荐 15GB，macRecovery 镜像 4GB 即可
以下设置保持不动
![](https://s2.loli.net/2022/07/30/AJ5Py4w9HhNUmTd.png)
找到新建的虚拟磁盘，在左边栏右键，选择初始化磁盘(I)
![](https://s2.loli.net/2022/07/30/1rzVkQMEBixSR4b.png)
选择 GPT 模式
![](https://s2.loli.net/2022/07/30/l1qdrKVLQi3sE4t.png)

## 创建引导分区
打开 Etcher，如果有更新弹窗选择 Skip，不要更新
![](https://s2.loli.net/2022/07/30/YE1UNC9LeZJHF4b.png)

点击 Select image 并选择下载好的 DMG 镜像
一般来说会默认选择好目标磁盘，如果有插入 USB 请选择 Change
最后点击 Flash 即可
![](https://s2.loli.net/2022/07/30/yFdOMXa24TBugfZ.png)

如果出现 UAC 弹窗点击确定即可
等待一下，写入过程还是很快的
![](https://s2.loli.net/2022/07/30/DwxLHAYE8nRt2Fs.png)

这样就是写入成功了
![](https://s2.loli.net/2022/07/30/yRiPqvgl7oj2FZU.png)

然后回到磁盘管理
找到 VHD，在左边栏右键，选择分离 VHD
![](https://s2.loli.net/2022/07/30/ETpGqVXAJdBFhOY.png)

—-例外情况—-
遇到如上情况则代表你的镜像不可引导，需要更换一个
![](https://s2.loli.net/2022/07/30/QAKb2uOTB9M8DEP.png)

## 在虚拟机中使用
先创建好一个 macOS 的虚拟机，然后编辑虚拟机设置
点击下面的添加(A)…并选择硬盘，然后点击下一步(N)>
![](https://s2.loli.net/2022/07/30/wGVAcqa1XLKQPFd.png)
磁盘类型选择 SATA 即可，然后选择使用现有虚拟磁盘(E)
![](https://s2.loli.net/2022/07/30/lfdZmVCykO6LBvA.png)
在浏览磁盘时，点击右下角的菜单栏选项，然后点击所有文件 (.)并选择刚刚写入好的 VHD
![](https://s2.loli.net/2022/07/30/JIvcZbiY1xQyaeB.png)
在这里选择保持现有格式即可
![](https://s2.loli.net/2022/07/30/Te7ylds1x3prNCh.png)
完成后点击编辑虚拟机设置，将网络适配器改为桥接（可能需要在虚拟网络编辑器里更改桥接对象）
然后启动虚拟机并等待一下就能进入到系统安装界面了
![](https://s2.loli.net/2022/07/30/gPqbV8tfEde9HLz.png)

## 关于 VirtualBox 能不能用
这是 VMware Workstation 的
![](https://s2.loli.net/2022/07/30/Bfz7HFNT9Xk3xnG.png)

这是 VirtualBox 的，同 CDR 一样会无限重启
（可能得注入机型之类的）
![](https://s2.loli.net/2022/07/30/byNv5G1CnTlQD3Y.gif)