---
title: 解决 Workstation 问题合集（1）
date: 2022-03-24 22:57:54
categories: 
	- [VMware,Workstation]
	- [教程,Windows]
tags:
	- Windows
	- VMware Workstation
description: 通过补丁的办法给部分 Windows 安装 VMware Workstation 的 tool 以及解决 tool 安装按钮为灰色
cover: https://s2.loli.net/2022/07/31/SkExKePhFpizCVb.png
---

## 用前说明

### 实验环境（其他版本 VMware Workstation 一样可以）
VMware Workstation 16.2.3
Windows 7 SP1（必须附带 SP1，如果你没有可以在下方补丁包内找到补丁）/Windows ES 7
Windows Vista（必须附带 SP2，如果你没有可以在下方补丁包内找到补丁）
Windows 2000
Windows NT4
[补丁](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Em5nztbLCAxEj8OSLo8dTtoBdAxnGJKpmjFTdLoqCAGXLQ)

## 章节 I（安装 tool）
{% post_link tutorial/Windows/NT6upd Windows Vista/7 没有装 SP 的看这里 %}

### Windows 7

#### 在虚拟机中插入补丁
点击虚拟机设置
![](https://s2.loli.net/2022/07/31/Wki8ueYRaBp5nq3.png)
在虚拟机设置中选择 CD/DVD，然后点击右边的使用 ISO 映像文件，并点击“浏览”，然后选择 <code>win7-ser2008(R2)解决 vm16 无法安装 tool 的补丁.iso</code>
![](https://s2.loli.net/2022/07/31/LGsBKAMmPaOhyje.png)
选择完成后点击“确认”并返回到虚拟机

#### 安装补丁
插入补丁后点击 Windows 徽标键>计算机
![](https://s2.loli.net/2022/07/31/SgeCAwcjHYqQKoX.png)
双击打开 CD 驱动器
![](https://s2.loli.net/2022/07/31/TWbXUrI6x5VHCqi.png)
在里面选择与你系统合适的补丁版本并安装

------

Windows Home Server 2011 请安装
适于 <code>Windows Server 2008 R2 x64 的 安全更新 (KB4474419).msu</code>

------

等待一会，然后选择“是(Y)”
![](https://s2.loli.net/2022/07/31/MZK8qshyOcexQ5X.png)
大约会在 30s 左右完成
![](https://s2.loli.net/2022/07/31/1XenDFljRqbB52v.png)
完成后点击“立即重新启动”
![](https://s2.loli.net/2022/07/31/HntQVgGT1msyjf7.png)

#### 安装 tool
重启后安装正常方式安装 tool 即可
![](https://s2.loli.net/2022/07/31/qWCPBx2gYEjyZtn.png)

### Windows Vista

#### 在虚拟机中插入镜像
点击虚拟机设置
![](https://s2.loli.net/2022/07/31/Wki8ueYRaBp5nq3.png)
在虚拟机设置中选择 CD/DVD，然后点击右边的使用 ISO 映像文件，并点击浏览，然后选择 <code>vm15tool.iso</code>
![](https://s2.loli.net/2022/07/31/LGsBKAMmPaOhyje.png)
选择完成后点击“确认”并返回到虚拟机

#### 安装 tool
插入 tool 后点击 Windows 徽标键>计算机
![](https://s2.loli.net/2022/07/31/2aPz4mNMDl5dnEF.png)
然后在资源管理器选择 tool 安装即可
![](https://s2.loli.net/2022/07/31/8HNIdKe5ig9zVWk.png)

### Windows 2000

#### 在虚拟机中插入补丁
点击虚拟机设置
![](https://s2.loli.net/2022/07/31/Wki8ueYRaBp5nq3.png)
在虚拟机设置中选择 CD/DVD，然后点击右边的使用 ISO 映像文件，并点击浏览，然后选择 <code>win2000 无法安装 tool 补丁.iso</code>
![](https://s2.loli.net/2022/07/31/LGsBKAMmPaOhyje.png)
选择完成后点击“确认”并返回到虚拟机

#### 安装补丁
补丁插入后会自动运行安装界面
（如果没有就自己在我的电脑里选择插入的补丁镜像即可）
![](https://s2.loli.net/2022/07/31/eM6W1sTS4opAzYv.png)
点击“我同意”——“下一步”
![](https://s2.loli.net/2022/07/31/hjAbWXnTc3pkxsY.png)
完成后点击“完成”即可自动重启
![](https://s2.loli.net/2022/07/31/xXkWhR9D57LAvMc.png)

#### 安装 tool
重启后安装正常方式安装 tool 即可
![](https://s2.loli.net/2022/07/31/YHq1vMr9xfc37DK.png)

### Windows NT4

#### 在虚拟机中插入补丁
点击虚拟机设置
![](https://s2.loli.net/2022/07/31/Wki8ueYRaBp5nq3.png)
在虚拟机设置中选择 CD/DVD，然后点击右边的使用 ISO 映像文件，并点击“浏览”，然后选择 <code>Windows NT 4.0 SP6a.iso</code>
![](https://s2.loli.net/2022/07/31/LGsBKAMmPaOhyje.png)
选择完成后点击“确认”并返回到虚拟机

#### 安装补丁
补丁插入后会自动运行安装界面
（如果没有就自己在我的电脑里选择插入的补丁镜像即可）
然后勾选第一个复选框，第二个可以取消，然后点击“安装(I)”
![](https://s2.loli.net/2022/07/31/xOrX6JMfo2bBG4U.png)
等待一下，安装程序完成后点击“重新启动(R)”
![](https://s2.loli.net/2022/07/31/78zRy6JL51lGvoe.png)

#### 安装 tool
重启后安装正常方式安装 tool 即可
![](https://s2.loli.net/2022/07/31/s5AUb9TDN41oSWL.png)

如果你在安装过程遇到以下几个弹窗，点击“YES”、“OK”和“好”即可
![](https://s2.loli.net/2022/07/31/KUImdcZlDsTOQxb.png)

## 章节 II（如果你安装 tool 的按钮是灰色）
—–如果你知道安装路径可忽略这段—–
在桌面上右键 VMware Workstation 快捷方式，然后选择“属性”
![](https://s2.loli.net/2022/07/31/1SEVKo8YjUnNMwg.png)
然后复制起始位置这个路径（不包括引号）
![](https://s2.loli.net/2022/07/31/ynSuFXxrRfmaBG5.png)

------

然后回到虚拟机，点击虚拟机设置
![](https://s2.loli.net/2022/07/31/Wki8ueYRaBp5nq3.png)
在虚拟机设置中选择 CD/DVD，然后点击右边的使用 ISO 映像文件，并点击浏览
（如果没有 CD/DVD 则需要自己在设置下面添加一个
在弹出的窗口中点击上方的地址栏空白处并将路径粘贴进去，然后回车
![](https://s2.loli.net/2022/07/31/SrVkWnJTlNuYjZd.png)
向下滑动找到 <code>windows.iso</code> 并选择，然后点击“打开(O)”
![](https://s2.loli.net/2022/07/31/hvZlFq3yD17iIHf.png)
然后点击虚拟机设置下方的确定按钮即可
插入补丁后点击 Windows 徽标键>计算机
![](https://s2.loli.net/2022/07/31/SgeCAwcjHYqQKoX.png)
双击 CD 驱动器即可打开安装程序
![](https://s2.loli.net/2022/07/31/TWbXUrI6x5VHCqi.png)
然后正常安装 tool 即可
![](https://s2.loli.net/2022/07/31/qWCPBx2gYEjyZtn.png)
