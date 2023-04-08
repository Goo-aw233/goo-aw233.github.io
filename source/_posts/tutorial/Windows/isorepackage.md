---
title: 自定义集合多版本的系统镜像
date: 2022-04-17 19:05:21
categories: 
	- 教程
	- Windows
tags: 
	- 软件
	- Windows
description: 利用 Dism++ 和 imagex 整合多版本的 Windows ISO 镜像
cover: https://s2.loli.net/2022/07/31/urWsnoISp16zcwe.png
---

## 用前说明

### 实验环境（Dism++ 可用 WimTool 代替）
Dism++
imagex
UltraISO
[如果没有可从这里下载](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/ElXthCE3Bs5MnFtFR24sfyMBVJcC9n6pUJzJY7vtTPwogg)
（系统映像仅限 WIM/ESD，不支持 GHO）

## 修整映像

### 解压镜像
先下载好系统镜像并将其解压到空白文件夹

### 删除多余的版本
打开 “Dism++x64.exe”，然后选择“文件(F)”-“打开映像文件 Ctrl+O”
![](https://s2.loli.net/2022/07/31/pVCmJjTU5LsIHb4.png)
然后点击“浏览”，选择到解压好的 Windows 镜像文件夹
![](https://s2.loli.net/2022/07/31/3ctUhpqySMPz4aH.png)
然后打开“sources 文件夹”，再选择<code>install.wim</code>
![](https://s2.loli.net/2022/07/31/61SBj5RCQd8IlMo.png)
选择你不需要的镜像版本，然后点击“删除镜像”
![](https://s2.loli.net/2022/07/31/G5KRtCinAZslc1P.png)
然后双击镜像名字，在里面修改你想修改的内容，点击“保存”（也可以不更改）
![](https://s2.loli.net/2022/07/31/4gE3WijnDwNPLya.gif)
然后再次选中所有镜像，点击“导出镜像”，选择空白文件夹 1
![](https://s2.loli.net/2022/07/31/aoeNpurI7WnYw5K.png)
将其命名后点击“保存(S)”
![](https://s2.loli.net/2022/07/31/iVLDdtykWUIwoah.png)
等待一会，出现操作成功的窗口后点击“确定”，然后再关闭编辑映像的窗口
![](https://s2.loli.net/2022/07/31/Xhu2VEkTLx4qoSN.png)
<font size=4 color=green>然后第二个（或更多）系统镜像也是向上面一样操作</font>

## 整合映像
将 imagex.exe 放入到以下文件夹
````
C:\Windows\System32
````
![](https://s2.loli.net/2022/07/31/mTCQjnGXrvo8WJK.png)
在搜索框搜索 cmd 并选择“以管理员身份运行”
![](https://s2.loli.net/2022/07/31/SWhKqRzDe97JQFf.png)
然后在 cmd 输入以下命令
````cmd
imagex /export <映像路径\文件名.wim> <第几个版本> <导出路径\install.wim> /compress maximum

------

其中，
<映像路径\文件名.wim> 就是修整后映像导出的位置
<第几个版本> 就是你一共有几个版本在内，仅有一个就只填写 1，如果有多个，需要多次执行命令并更改版本位数
<导出路径\install.wim> 就是导出的地方在哪，需要和第一个导出的路径统一

------

示例：（一个单版本的 Windows 10 和一个双版本的 Windows 7）
imagex /export D:\isoput\after\test\1.wim 1 D:\isoput\after\test\putout\install.wim /compress maximum
imagex /export D:\isoput\after\test\2.wim 1 D:\isoput\after\test\putout\install.wim /compress maximum
imagex /export D:\isoput\after\test\2.wim 2 D:\isoput\after\test\putout\install.wim /compress maximum
````
<font size=4 color=red>重要事项：
路径中只能有英文和下划线 路径中只能有英文和下划线 路径中只能有英文和下划线</font>

等待一会就完成了
![](https://s2.loli.net/2022/07/31/r91kibThl5JCUyv.png)

------

如果你想知道成功了没
打开 “Dism++x64.exe”，然后选择“文件(F)”-“打开映像文件 Ctrl+O”
![](https://s2.loli.net/2022/07/31/pVCmJjTU5LsIHb4.png)
然后点击浏览，选择到整合好的 wim
![](https://s2.loli.net/2022/07/31/3ctUhpqySMPz4aH.png)
![](https://s2.loli.net/2022/07/31/jQFa4IcKd51ECfZ.png)
成功了之后关闭 Dism++ 和 cmd 即可
![](https://s2.loli.net/2022/07/31/sNdRYfAnP1HmpGv.png)

------

## 修改镜像
打开 UltraISO，并选择你要修改的镜像【不建议选择 Windows 11 的镜像，不兼容 Windows 11 的电脑会报错（除非往镜像替换 appraiserres.dll）】![](https://s2.loli.net/2022/07/31/GMpVOcR6vgrKwWZ.gif)
打开 sources 文件夹，然后把修改好的 install.wim 拖进去
![](https://s2.loli.net/2022/07/31/tSeUVhQLglnozTx.png)
然后点击是
![](https://s2.loli.net/2022/07/31/W8RqgdKBslCmUAw.png)

------

你还可以更改镜像显示的名字
![](https://s2.loli.net/2022/07/31/AIh61tDFZaMgom8.png)

------

完成后点击保存即可（右边的红条不用理会）
![](https://s2.loli.net/2022/07/31/zMmQlN7I682ouAd.png)

## 测试
在虚拟机中加载镜像，进入安装程序后就能正常加载
![](https://s2.loli.net/2022/07/31/aRIjW2QreiwbM8J.png)
也能正常安装
![](https://s2.loli.net/2022/07/31/7sBXaMgEVlb1dOW.png)
![](https://s2.loli.net/2022/07/31/ztd8QqIoAbprDv9.png)