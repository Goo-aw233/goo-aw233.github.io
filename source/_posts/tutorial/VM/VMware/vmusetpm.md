---
title: Workstation 免加密启用TPM
date: 2021-11-20 21:42:37
categories: 
	- VMware
	- Workstation
tags:
	- VMware Workstation
description: 通过修改 .vmx 来实现 VMware Workstation 免加密启用 TPM 模块
---

## 用前说明
该功能仅适用于 <code>Workstation 16.2</code> 及以上的版本，<font size=4 color=red>并且会导致虚拟机加密无法移除</font>
文件迁移或系统重装后会提示输入密码，目前暂无解决办法

## 创建一个虚拟机 并启用 UEFI
安全启动可以不选择启用
![](https://s2.loli.net/2022/07/31/LojuP3C4qzSDrmk.png)

## 在 .vmx 中添加代码
先关闭 VMware Workstation 主程序
用任意编辑器打开 .vmx 文件 在结尾添加以下代码后保存
````
managedvm.autoAddVTPM = "software"
````
如图所示
![](https://s2.loli.net/2022/07/31/1dpIObz3BXcCNDA.png)
重新打开 VMware Workstation 并选中虚拟机
这样你就可以做到免加密且开启 TPM 了
![](https://s2.loli.net/2022/07/31/yCcWQMfFxJ2wROn.png)
