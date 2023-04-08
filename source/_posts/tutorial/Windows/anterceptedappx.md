---
title: 抓包 APPX
date: 2022-07-13 22:25:48
categories: 
	- 教程
	- Windows
tags: 
	- 软件
	- Windows
description: 用网站或 Fiddler 截取 Microsoft Store 的内容
---

## 用网站抓取
访问 [store.rg-adguard](https://store.rg-adguard.net)
在第一个框中选择 <code>URL (link)</code>，第二个框输入 Microsoft Store 所对应的网页地址，第三个框则默认选择 RP
![输入链接](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx1.png)
其中，第三个框内容对应如下：
Fast=快速测试版 | Slow=最快速测试版 | RP=正式版 | Retail=预发布版
第二个框中的网页地址可在 Microsoft Store 中获取，以 [Loaf - a WinUI3 App](https://www.microsoft.com/store/productId/9NDJ3Q12NRRM) 为例
点开软件详情页，点击右方的“分享”，并在弹出的窗口中选择“复制链接”
![获取链接](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx2.png)
完成后粘贴到第二个框，然后点击“√”即可查找适用的包

加载一会，你会看到各种各样的包
![包加载](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx3.png)
其中，后缀为 <code>.BlockMap</code> 的文件是文件属性，可以不下载；包名中带有 <code>ARM64、ARM、x64 或 x86</code> 字样的则对应的是你的系统架构，一般情况下选择 x64
而后缀为 <code>.eappx </code>之类的则是给 Xbox 使用的包
如果没有标明架构，就像下图
![未标出架构](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx4.png)
则代表这个软件同时兼容 <code>x64 和 x86</code>，是否兼容 ARM(64) 还另需将 APPX 解压后才可得知
软件运行需要运行库，所以你还需要下载与你系统架构对应的运行库，如果你不知道选哪个版本（不是架构）的运行库，则可以全部下载后逐个安装

### 如果你不知道下载地址
类似于 Microsoft Store，在商店内是搜索不到的
![无法搜索到](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx5.png)
这时候你可以给那个软件创建个快捷方式右键——属性，其中“目标类型：”或“目标(T)：”就是软件的包名
![获取包名](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx6.png)
这时候回到网页，在第一个框中选择“PackageFamilyName”
![更改类型](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx7.png)
第二个框输入包名（包名不包括后缀的 <code>!App</code>）
这样也同样可以搜索到
![搜索包](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx8.png)

## 用 Fiddler 抓取
这个办法远没第一个方便
以 Minecraft Preview for Windows 为例

------

第一次使用 Fiddler 必看
在这个弹窗点击“取消”
![取消警告](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx9.png)
在软件上方点击“工具”——“选项...”——“HTTPS”，把“捕获 HTTPS 链接”和“解密 HTTPS 通信给勾选上”，这时候出现安装证书，点击“是”即可
![解密 HTTPS](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx10.png)
在这俩弹窗点击“Yes”
![信任证书 1](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx11.png)
![信任证书 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx12.png)
然后回到主程序，点击左上角的“WinConfig”，弹窗点击“No”
![取消警告](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx13.png)
找到名为“Microsoft Store”的项，勾选它，并点击“保存更改”
![解除沉浸式](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx14.png)

------

先在 Microsoft Store 下载软件（这里建议先退出无关软件避免有多余的链接产生）
回到主程序界面，当软件正在下载时列表会刷新
随机找一个链接，一般为 <code>tlu.dl.delivery.mp.m...</code>
![获取链接](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx15.png)
然后右键——“复制”——“仅 URL  Ctrl+U”
![复制链接](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/anterceptedappx/anterceptedappx16.png)
再用软件（如 IDM 等）下载即可（有效期仅为 15min）
