---
title: Workstation 安装 macOS
date: 2022-02-28 23:10:12
categories: 
	- [虚拟机,VMware,Workstation]
	- [教程,macOS]
tags:
	- VMware Workstation
	- macOS
description: 利用 CDR,ISO 或 DMG 文件在 VMware Workstation 中安装 Mac OS (X)/macOS
top_img: https://www.apple.com.cn/v/mac/home/bk/images/overview/monterey/tile_monterey__bm1x7sttegty_large.jpg
cover: https://www.apple.com.cn/v/mac/home/bk/images/overview/monterey/tile_monterey__bm1x7sttegty_large.jpg
sticky: 100
---

## 用前说明
因为是虚拟机且没有显卡，所以版本越高，卡顿便越明显
<font size=3 color=yellow>推土机架构的 AMD CPU 并不确保 100% 可以使用</font> 

### 实验环境（其他版本 VMware Workstation 一样可以）
VMware Workstation Pro 16
CDR/ISO/DMG（你也可以在其他地方下载）
<font size=1> DMG 镜像需要{% post_link tutorial/VM/VMware/vmdmg 特殊手段 %}安装 </font>
[OneDrive 站点](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/EpoxWXc-tPpFnoAJTb4hoxYB0UWLRWMPHEwt5Tp-ZMZBvA)
[阿里云盘站点](https://www.aliyundrive.com/s/W4PHQ9gyLWi)
—–以下解锁工具任选一即可—–
[Unlocker（新版）](https://github.com/DrDonk/unlocker)
[Unlocker（旧版，如果不是旧版本需要请不要使用该工具）](https://github.com/theJaxon/unlocker)
（如果你的系统不预装 PowerShell 如 Windows XP，则请用旧版 Unlocker）

### 解锁工具的使用（任选一观看即可）
解锁前请关闭 VMware Workstation 的主程序窗口
如果安装不成功可能需要重启电脑后再次运行

如果你先前已经解锁过，请跳到[创建虚拟机](#创建虚拟机)的步骤

#### Unlocker（新版）
解压压缩包，进入到 <code>windows</code> 文件夹
按住 <kbd>Shift</kbd>，然后按下右键
选择<code>在此处打开 PowerShell 窗口</code>
![](https://s2.loli.net/2022/07/30/BHL2qTw1kfZzEWJ.png)
然后输入如下命令
````powershell
./unlock.exe install
````
等待一下即可完成解锁，然后按任意键即可退出
![](https://s2.loli.net/2022/07/30/EgRTumybsXYz2LQ.png)

#### Unlocker（旧版）
如果你不想下载 tools 太慢可以按照以下步骤
[tools 下载](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Evw884PwnZdGlYnUagIr3rgB8f_hX_BvQz1V4MX9sUQ3mA?e=MQp7IO)
下载完后在 unlocker 文件夹中创建一个名为 tools 的文件夹并把 tools 放进去
![](https://s2.loli.net/2022/07/30/Cmgx6Jw5iM2PsuU.png)

------

找到 win-install.cmd
右键以管理员身份运行
![](https://s2.loli.net/2022/07/30/ghEwV6mnuKW5eOI.png)
出现 UAC 弹窗点击确定即可
![](https://s2.loli.net/2022/07/30/DwxLHAYE8nRt2Fs.png)
等待一下就解锁完成然后开始下载 tools
![](https://s2.loli.net/2022/07/30/2fs6eMXYnjz1ao4.png)

------

如果你提前保存过 tools，在这个界面输入 n 即可
![](https://s2.loli.net/2022/07/30/JnxShUXVwErTY2A.png)

------

## 创建虚拟机
如果你需要用 DMG 镜像安装系统请看下面的文章
{% post_link tutorial/VM/VMware/vmdmg 使用 DMG 引导虚拟机 macOS %}

------

选择系统镜像的时候如果使用的是 CDR 则需要在右下角改为所有格式
![](https://s2.loli.net/2022/07/30/ok45shdAWFGL9PJ.png)
出现“无法检测此光盘映像中的操作系统”无需理会，点击下一步即可
然后选择好正确的系统版本
![](https://s2.loli.net/2022/07/30/F8eiKpZoU7qOnf5.png)
创建磁盘的时候一定要选将虚拟磁盘存储为单个文件(O)
![](https://s2.loli.net/2022/07/30/vid8D13wNLAzRab.png)
完成后点击编辑虚拟机设置，将网络适配器改为桥接（可能需要在虚拟网络编辑器里更改桥接对象）
![](https://s2.loli.net/2022/07/30/zvZBAWfD1XlLOaE.png)
完成后开启虚拟机即可进入 macOS
![](https://s2.loli.net/2022/07/30/lqRO1fzSsi7jKa5.png)
最后按照正常的方式安装 macOS 即可

## 题外话

### 安装报错
如果安装 macOS Big Sur 或更高版本安装时出现更新错误之类的报错，请把以下代码添加到 vmx 文件的最末端
（适用于 Intel CPU）  
（取自[黑苹果星球](https://heipg.cn/tutorial/install-macos-by-using-vmware-in-windows.html)）
````vmx
board-id = "Mac-7BA5B2D9E42DDD94" 
hw.model = "iMacPro1,1" 
uuid.action = "keep" 
smc.version = "0"
````

------

如果你是锐龙架构的 AMD CPU，请添加以下代码（可能不是每个人都适用）
[出处（有待考究）](https://blog.csdn.net/weixin_43436925/article/details/122437355) | 末尾两个代码是自己另外添加的
````vmx
smc.version = "0"
cpuid.0.eax = "0000:0000:0000:0000:0000:0000:0000:1011"
cpuid.0.ebx = "0111:0101:0110:1110:0110:0101:0100:0111"
cpuid.0.ecx = "0110:1100:0110:0101:0111:0100:0110:1110"
cpuid.0.edx = "0100:1001:0110:0101:0110:1110:0110:1001"
cpuid.1.eax = "0000:0000:0000:0001:0000:0110:0111:0001"
cpuid.1.ebx = "0000:0010:0000:0001:0000:1000:0000:0000"
cpuid.1.ecx = "1000:0010:1001:1000:0010:0010:0000:0011"
cpuid.1.edx = "0000:0111:1000:1011:1111:1011:1111:1111"
smbios.reflectHost = "TRUE"
hw.model = "MacBookPro14,3"
board-id = "Mac-551B86E5744E2388"
keyboard.vusb.enable = "TRUE"
mouse.vusb.enable = "TRUE"
````

### 磁盘
macOS 安装与 Windows 不同，需要手动格式化磁盘
近期版本可在主界面直接选择磁盘工具
![](https://s2.loli.net/2022/07/30/yjK9UZDmLi6QESB.png)
较为早期的版本（如 OS X 10.11 及更早的版本）则需要在上方的实用工具打开
![](https://s2.loli.net/2022/07/30/XWlTnwCYkbz4oVu.png)
近期版本请选择 APFS，分区表选择 GUID
![](https://s2.loli.net/2022/07/30/edS4LFOtn7CEUaK.png)
较为早期（如 OS X 10.11 及更早）不支持 APFS 的版本则选择 Mac OS 扩展 (日志式)
![](https://s2.loli.net/2022/07/30/5SUXmnB2EQOPJLC.png)