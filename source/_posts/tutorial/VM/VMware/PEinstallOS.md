---
title: Workstation 使用 PE 装系统
date: 2021-11-20 22:41:54
categories: 
	- [VMware,Workstation]
	- [教程,Windows]
tags:
	- VMware Workstation
	- Windows
description: 在 VMware Workstation 中使用 PE 装系统
---

## 用前说明
该教程仅适用于 Windows 2000 及以上的 Windows（不包括 Windows ME）

### 实验环境
以下 PE 任选一即可
[微 PE](https://www.wepe.com.cn)
[FirPE](https://firpe.cn/page-247)
或其他可信任的 PE（不要使用带捆绑安装的 PE 如老毛桃和大白菜）

## 创建虚拟机
详细过程不用多说，只有以下需要改动的地方

你需要添加两个 CDROM
![](https://s2.loli.net/2022/07/31/1UNLpj7rI8cBv2y.png)
TIPS:你需要先挂载 PE，等 PE 完全加载后再挂载系统镜像
![勾选复选框](https://s2.loli.net/2022/07/31/qRJug9IdKk6AtaQ.png)
![取消复选框](https://s2.loli.net/2022/07/31/lLcNUGVMYRA37QP.png)

## 在 PE 里安装系统

### 原版镜像安装

#### 格式化并创建分区
首先打开桌面上的“分区工具 DiskGenius”
选中空白的磁盘 点击上方的新建分区并勾选以下内容（BIOS 启动的情况下无需勾选）
![](https://s2.loli.net/2022/07/31/pmZ1F8kI9bsDylK.png)
分区大小按自己需求决定 最后点击左上角的保存更改并一路点击确定
![](https://s2.loli.net/2022/07/31/s6Cn814kIFt7hOr.png)

#### 安装系统
点击桌面上的“Dism++”如果出现报错点击确定即可
![](https://s2.loli.net/2022/07/31/WpUdJbVT3L9nxkH.png)
点击上方的“恢复功能(R)”>“系统还原”
![](https://s2.loli.net/2022/07/31/ZAcasNzxLpt8owQ.png)
这时候需要插入 Windows 原版镜像
![](https://s2.loli.net/2022/07/31/TuR3Aj792JQ4cIL.png)

在弹出的窗口中点击第一个浏览
![](https://s2.loli.net/2022/07/31/DQwvWSLUT5crqYm.png)
然后定位到 CD 的 <code>sources\install</code> 目录下的 <code>install.wim</code> 文件并选中
![](https://s2.loli.net/2022/07/31/73C4KWSgvOJyPdL.png)
第二个空选择要安装到的磁盘即可，并勾选“添加引导”和“格式化”，可自己选择系统版本
完成后点击确定即可开始安装 Windows
![](https://s2.loli.net/2022/07/31/d7gQtRfTxo9aLJi.png)
出现以下对话框时点击“确定”即可
![](https://s2.loli.net/2022/07/31/d7gQtRfTxo9aLJi.png)
等待几分钟后 当“Dism++”出现“C: 映像已经还原成功”，则代表系统安装成功 这时可以把所有 CD 推出并重启进入系统部署界面

### Ghost 镜像安装
格式化并创建分区的过程与原版镜像安装差不多，如果是 BIOS 启动则不需要创建 MSR 和 ESP 分区

#### 安装系统
点击桌面上的“CGI 备份还原”
在“3.请选择镜像文件”那点击后面的 <code>...</code> 来选择 <code>.gho 文件</code>（通常情况下会自动选择)
选择完成后点击软件下方的“执行”按钮
![](https://s2.loli.net/2022/07/31/MdRuNU4Pj2XWgLb.png)
在此界面不需要勾选任何选项 点击“确定”即可
![](https://s2.loli.net/2022/07/31/3IKzhXDsuFOCQtR.png)
等待几分钟后，软件提示恢复成功
### 修复引导
点开桌面上的“Dism++”并忽略报错
点击上方的“恢复功能(R)“>“引导修复”（需要先点击旁边选中的 Windows 才可修复）
![](https://s2.loli.net/2022/07/31/f1vrbm25nFaG8p6.png)
直接点击“确定”即可
![](https://s2.loli.net/2022/07/31/ewzoOBGI8ANW6hU.png)
最后重启虚拟机，把所有 CD 推出
在系统引导界面选择第一个 Windows 引导项，之后就可以进入到系统部署界面了
