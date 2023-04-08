---
title: 解除 UWP 联网限制
date: 2022-06-11 14:56:30
categories: 
	- 教程
	- Windows
description: 利用 EnableLoopback 解除 UWP 连接代理时指向 127.0.0.1 的设定
tags: 
	- Windows
	- 软件
---

## 用前说明
这个玩意 Fiddler 里也有（）
[EnableLoopback](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Etnn58PCyzNJrImYVThl_P4Bvcg0oXLA8wYgTKq7byPaRw)

## 解除限制

------

如果有类似的提示点击否(N)即可
![(https://s2.loli.net/2022/08/15/REZAp3m4idS7JlF.png)

------

在列表中选择你需要解除的应用，点击右边的复选框
或者点击全部选择，再点击上面的保存更改即可
![](https://s2.loli.net/2022/08/15/429JUjVhILYZFuQ.png)
然后重启 UWP 应用即可

## 报错
就像这样的
![](https://s2.loli.net/2022/08/15/8gfoB1GRxyhpNrz.png)
点击刷新
![](https://s2.loli.net/2022/08/15/g29kSQRvc34YyzH.png)
然后找到没有被√起来的那个项，并终止它（如果没有在运行的话可能重启可以解决）
![](https://s2.loli.net/2022/08/15/48KnYXZsjEUrANW.png)
然后就可以重新√上继续使用了