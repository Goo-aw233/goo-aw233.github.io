---
title: 屏蔽获取 Windows 11 更新
date: 2022-10-30 14:21:45
categories: 
	- 教程
	- Windows
tags: Windows
description: 使用组策略/注册表功能来阻止 Windows 自动更新到 Windows 11
---

## 用前说明
如果以下操作都没有办法屏蔽，可以再试试这个方法 {% post_link tutorial/Windows/blockfeatureupd 屏蔽 Windows 各种更新 %}

## 使用组策略
（家庭版没有组策略功能，所以需要用注册表，请浏览[下一章](#使用注册表)
按下 <kbd>Windows 徽标键</kbd>+<kbd>R</kbd> 来打开运行，并输入 <code>gpedit.msc</code> 并回车
![组策略](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockWin11upd/blockWin11upd1.png)
然后找到“计算机配置”>“管理模板”>“Windows 组件”>“Windows 更新”>“适用于企业的 Windows 更新”>“选择目标功能更新版本”
![定位](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockWin11upd/blockWin11upd2.png)
然后点击“已启用(E)”，然后在下面的第一个矩形框中输入 <code>Windows 10</code>，第二个框根据你的系统版本填写，如 <code>22H2</code>，最后点确定保存
但如果设置到了不再支持设置的版本，将强制执行功能升级
![值](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockWin11upd/blockWin11upd3.png)
最后在“Windows 更新”里就会有提示了
![设置策略](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockWin11upd/blockWin11upd4.png)
Windows 11 更新的提示也没了
![提示](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/blockWin11upd/blockWin11upd5.png)

## 使用注册表