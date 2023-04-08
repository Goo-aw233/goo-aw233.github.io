---
title: 转换 Windows 10 为 LTS
date: 2022-05-28 17:45:32
categories: 
	- 教程
	- Windows
tags: Windows
description: 将你的 Windows 10 免数据丢失和重装转换为 LTSB/LTSC
cover: https://s2.loli.net/2022/08/15/dIkERT7vepgKWMD.png
---

## 用前说明
仅支持 1507、1607、1809、21H2 版本的 Windows，对应的是 LTSB 2015、LTSB 2016、LTSC 2019 和 LTSC 2021
如果你需要转换到你想要的版本则需要清除数据降级/保留数据升级到对应版本

### 实验环境
LTSB/LTSC 镜像

## 更改版本号
同时按下 <kbd>Windows 徽标键</kbd>和 <kbd>R</kbd> 键打开运行，输入 <code>regedit</code> 并回车
然后定位到以下路径
````
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion
````
![](https://s2.loli.net/2022/08/15/eca7lxpzDVbLrTI.png)
找到以下几个值，并将里面的值修改为箭头后的值
````
CompositionEditionID	>>>		EnterpriseS
EditionID		>>>		EnterpriseS
ProductName		>>		Windows 10 Enterprise LTSC 2021
↑↑↑ ProductName	后面的值改为你需要用的 LTS 版本即可 ↓↓↓
LTSB 2015 >>> Windows 10 Enterprise 2015 LTSB
LTSB 2016 >>> Windows 10 Enterprise 2016 LTSB
LTSC 2019 >>> Windows 10 Enterprise LTSC 2019
LTSC 2021 >>> Windows 10 Enterprise LTSC 2021
````
![](https://s2.loli.net/2022/08/15/lZsoSUki4hFOTwD.png)
完成后关闭注册表编辑器

## 安装 LTS 版本
双击打开 ISO 文件会自动挂载在资源管理器中，直接双击它就会打开安装程序
![](https://s2.loli.net/2022/08/15/qK3jy6dNbeCLB4p.png)
等待一会，安装程序会自动下载所需的补丁
![](https://s2.loli.net/2022/08/15/9LuxB8sS5t2POeJ.png)
直接点击安装(I)即可
![](https://s2.loli.net/2022/08/15/rkAft9SvUPOjTRc.png)

如果你没有调整注册表、调整了没有重新打开或者你的版本不是与 LTS 为同一版本则都会无法保留文件
![](https://s2.loli.net/2022/08/15/EoXGO9LTuBUdwsc.png)