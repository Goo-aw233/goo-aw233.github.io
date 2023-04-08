---
title: 远程桌面到登录 AzureAD 的设备
date: 2022-12-25 23:35:36
categories: 
	- 教程
	- Windows
tags: Windows
description: 远程桌面到登录到 Azure AD 账户的 Windows 设备
cover: https://learn.microsoft.com/zh-cn/windows/client-management/images/rdp.png
---

## 配置设备
在被操控的设备中执行以下操作：
按下 <kbd>Windows 徽标键</kbd>+<kbd>R</kbd>，输入 <code>SystemPropertiesRemote</code> 并回车
在“远程”页，选择“允许远程连接到此计算机(L)”，并取消勾选“仅允许运行使用网络级别身份验证的远程桌面的计算机连接(建议)(N)”，最后点击“确定”
![开启远程桌面](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/AADmstsc/AADmstsc1.png)

如果被操控的设备中 Azure AD 账户不为管理员则需要进行以下操作，否则请跳过该段

------

在“搜索”中搜索 <code>PowerShell</code>，右键选择“以管理员身份运行”
![运行 PowerShell](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/AADmstsc/AADmstsc2.png)
接着在 PowerShell 中输入以下内容
```PowerShell
net localgroup "Remote Desktop Users" /add "AzureAD\<Azure AD 的账户域名>"
```
比如我的 Azure AD 账户域名是 <code>114514@homo.com</code>，则命令就是（包括引号）
```PowerShell
net localgroup "Remote Desktop Users" /add "AzureAD\114514@homo.com"
```
![添加用户](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/AADmstsc/AADmstsc3.png)

------

如果操控设备为 Windows 10 1607 及更高版本的 Windows，则需要在[设置](ms-settings:workplace)中登录到与被操控的设备同样的 Azure AD 域中
![登录 Azure AD](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/AADmstsc/AADmstsc4.png)

最后在登录时，登录的账户应为
```
AzureAD\<Azure AD 的账户域名>
```
比如我的 Azure AD 账户域名是 <code>114514@homo.com</code>，账户就是
```
AzureAD\114514@homo.com
```
![登录到设备](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/AADmstsc/AADmstsc5.png)

## 注意事项
<li>本地和远程电脑都必须运行 Windows 10 1607 或更高版本，不支持与运行早期版本的 Windows 10 与已加入 Azure AD 的电脑建立远程连接</li>
<li>从进行连接的本地电脑，如果运行 Windows 10 1607 及更高版本，则必须已加入 Azure AD ，或已加入混合 Azure AD；如果使用 Windows 10 2004 及更高版本，则必须注册到 Azure AD， 不支持从未加入的设备或非 Windows 10/11 设备远程连接到已加入 Azure AD 的电脑</li>
<li>本地电脑和远程电脑必须位于同一 Azure AD 租户中，远程桌面不支持 Azure AD B2B 来宾</li>
<li>确保在用于连接到远程电脑的客户端电脑上关闭远程 Credential Guard（Windows 10版本 1607 中的一项新功能）</li>

## 参考文献
[Microsoft Learn](https://learn.microsoft.com/windows/client-management/connect-to-remote-aadj-pc)