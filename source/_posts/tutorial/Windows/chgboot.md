---
title: 更改系统引导模式
date: 2022-04-28 20:56:39
categories: 
	- 教程
	- Windows
tags: Windows
description: 在 PE 下把系统引导从 BIOS+MBR 改成 UEFI+GPT
---

## 用前说明

### 实验环境
VMware Workstation
（其它虚拟机或物理机都可以，只是为了方便演示）
[微 PE](https://www.wepe.com.cn)
（别的 PE 也可以）


## 在 BIOS 更改引导方式
物理机请自行百度/Bing
格式为 主板厂家名+主板型号+怎么切换 UEFI 启动
如：技嘉 z390怎么切换 UEFI 启动

------

打开 Workstation，点击“虚拟机设置”>“选项”>“高级”>“(U)EFI”  >>>>>>在早些版本中只会显示 EFI 的复选框
![](https://s2.loli.net/2022/07/31/5Zrowaxh8cijOGS.png)
如果是 VirtualBox 则是选中“虚拟机”>“设置”>“系统”>“启用 EFI”
![](https://s2.loli.net/2022/07/31/fQDgkSEeUMmIYRs.png)

## 插入 PE 镜像
![](https://s2.loli.net/2022/07/31/qRJug9IdKk6AtaQ.png)

## 更改磁盘为 GUID 模式并新建分区
启动虚拟机，在 Windows Boot Manager 界面选择 1024x768 的选项（别的 PE 可能会不同，随便选一个就好，这里是为了显示比较正常）
![](https://s2.loli.net/2022/07/31/MIfOxkPCT34wjre.png)
然后回车，等待一下就能进入到 PE 了

进入系统后打开“分区工具 DiskGenius”
![](https://s2.loli.net/2022/07/31/TvW9LFwKnyDj7C5.png)
选中硬盘（不是分区）右键>“转换分区表类型为 GUID 格式”>“保存”
![](https://s2.loli.net/2022/07/31/dYSIOXEQfFjniB7.png)
保存完后随意选择一个分区（不是硬盘）右键>“拆分分区”
![](https://s2.loli.net/2022/07/31/8K5X7LsmtncQVY2.png)
在分区后的空间那里输入 500.00MiB，然后选择“保持空闲”，点击“完成”
![](https://s2.loli.net/2022/07/31/cEFOAxtdJ9Wng5e.png)

完成后右键分出来的空白分区>“建立 ESP/MSR 分区”
![](https://s2.loli.net/2022/07/31/KehOCAgR2l8tHUV.png)
把三个复选框都选上，然后按照这样设置，点击“确定”
![](https://s2.loli.net/2022/07/31/5XhGfFuec72PA3Q.png)
最后点击保存，完成后退出 DiskGenius
![](https://s2.loli.net/2022/07/31/3c91fWGtuxZapo7.png)

## 修复引导
点开桌面上的“Dism++”并忽略报错
点击上方的“恢复功能(R)”>“引导修复”（需要先点击旁边选中的 Windows 才可修复）
![](https://s2.loli.net/2022/07/31/f1vrbm25nFaG8p6.png)
直接点击“确定”即可
![](https://s2.loli.net/2022/07/31/ewzoOBGI8ANW6hU.png)
然后重启就可以了