---
title: 在 iOS 6/5 使用 QQ 和微信
date: 2022-01-03 23:10:12
categories: 
    - 教程
    - iOS
    - 越狱
description: 利用文件替换法登录 QQ 和密码更改法在多平台登录微信
tags: iOS
cover: https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX_top.png
---

## 用前说明
以下办法不一定100%有效，且有小概率会被封禁（雀食很小）

### 实验环境（其他环境一样可以）
iOS6.1.3|iOS9.3.6
QQ：5.6(4.7.2)|8.0.0
微信：版本≥2.0

### 越狱
需要先对 iOS6.1.3 和 iOS9.3.6 进行越狱
并在 Cydia 中添加 Apple File Conduit”2” 和 AppSync 插件(文章尾部有教程)

## 登陆 QQ

### 在 iOS9.3.6中查找所需文件(夹)
将设备登录 QQ，确保设备为越狱状态并将其连接到电脑
#### 提取 <font size=6 color=green>QQAccountsManager</font> <font size=6 color=yellow>文件</font>
在[爱思助手](https://www.i4.cn)的文件管理中找到以下路径
````
/var/mobile/Containers/Data/Application/QQ 的字符串名/Documents/contents
````
其中一长串字符因人而异,需要自己摸索
有的人的路径可能是
````
/var/mobile/Applications/QQ/Documents/contents   （一般是 QQ5.6 左右的路径）
或
/var/mobile/Containers/Data/Application/QQ/Documents/contents   （一般是 QQ5.6+ 的路径）
````
找到路径后将其中的 QQAccountsManager 文件复制出来
![QQAccountsManager 文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX1.png)

#### 提取 <font size=6 color=green>WtloginConf</font> <font size=6 color=yellow>文件夹</font>
在文件管理中找到以下路径
````
/var/mobile/Containers/Data/Application/QQ 的字符串名/Documents/contents
````
其中一长串字符因人而异,需要自己摸索
有的人的路径可能是
````
/var/mobile/Applications/QQ/Documents/Library   （一般是 QQ5.6 左右的路径）
或
/var/mobile/Containers/Data/Application/QQ/Library  （一般是 QQ5.6+ 的路径）
````
找到路径后将其中的 WtloginConf 文件夹复制出来
![WtloginConf 文件夹](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX2.png)

### 在 iOS6 中替换文件(夹)
你需要打开一次 QQ
与上面相同,你需要用文件管理找到 QQAccountsManager 文件和 WtloginConf 文件夹所在的位置
然后把这两个文件(夹)<font color=red>替换(不要删除)</font>到里面
![替换文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX3.png)
<font color=red>替换成功后在设备退出 QQ 后台,然后重新打开 QQ</font>
打开 QQ 后点击倒三角,然后选择头像
![登录 QQ](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX4.png)
等待加载一下,就可以正常使用了
![QQ5.6](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX5.png)
![QQ5](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX6.png)

## 登录微信
施工（
改密码的方式已经失效了（可能

## 题外话

### 如何安装 Apple File Conduit”2” 和 AppSync 插件
{% post_link tutorial/iOS/jailbreak/afc+appsync 安装方法 %}

### 找不到对应文件夹怎么办
爱思助手中的资料管理中有个搜索功能
直接在里面搜索关键词即可(速度可能稍慢)
![搜索文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/iOSuseQQVX/iOSuseQQVX7.png)