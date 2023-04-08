---
title: Windows 11 启用 Internet Explorer
date: 2022-04-28 20:52:39
categories: 
	- 教程
	- Windows
tags: Windows
description: 利用多种方法调用被隐藏起来的 Internet Explorer
---

## 方法一
打开 Microsoft Edge 的设置
![](https://s2.loli.net/2022/07/31/qzJDAvE4SX9hNfV.png)
然后在搜索框搜索“Internet Explorer 模式”，并点击“允许在 Internet Explorer 模式下重新加载站点”
![](https://s2.loli.net/2022/07/31/1k7E4rfw3eCSKbB.png)
在“让 Internet Explorer 在 Microsoft Edge 中打开网站”中点击右边的选项框，点击“始终（推荐）”
<font size=3 color=green>（如果你设置为“从不”，把”允许在 Internet Explorer 模式下重新加载网站“改为允许的话
可以尝试用别的软件来重新修复 Internet Explorer 的可用性而不会打开到 Microsoft Edge）</font>
![](https://s2.loli.net/2022/07/31/6OjUNmCzPIe4pkH.png)
然后重启浏览器，你就发现这个功能选项就自动打开了
在你需要用它的时候点击右上角的“Internet Explorer 模式”就好
![](https://s2.loli.net/2022/07/31/f7DjC3v4o5AYhxy.png)

## 方法二
<font size=3 color=red>TIPS：如果你在 Microsoft Edge 中将“让 Internet Explorer 在 Microsoft Edge 中打开网站”选项改为“始终（推荐）”的话这个方法会不起效果
该功能在 Windows 11 22H2 某个预览版中被移除，请使用方法一或三</font>
打开“控制面板”，选择“网络和 Internet”
![](https://s2.loli.net/2022/07/31/NuJn4iEUIVjfo7S.png)
然后再选择“Internet 选项”
![](https://s2.loli.net/2022/07/31/vNbE6kpoDwl7rQ4.png)
在“Internet 属性页”中点击右上角的“?”即可打开 Internet Explorer
![](https://s2.loli.net/2022/07/31/V3TUqAwPlYbuCNe.png)
![](https://s2.loli.net/2022/07/31/tpYF1SydDGPfRIm.png)

## 方法三
在桌面（或任意地方）新建文本文档
![](https://s2.loli.net/2022/07/31/cHkiY3fJVnZ2aL7.png)
并将其命名为 <code>IE.vbs</code>（前缀 IE 可以自定义名字，如果默认不显示后缀名则须[手动打开](https://jingyan.baidu.com/article/fa4125acd0dee369ad709223.html)）
![](https://s2.loli.net/2022/07/31/PJhdKHUO5j23wm6.png)
然后右键它，选择“编辑(E)”
![](https://s2.loli.net/2022/07/31/gnIB3NdZFl5yMhA.png)
然后输入以下代码并保存退出
````vbs
CreateObject("InternetExplorer.Application").Visible=true
````
![](https://s2.loli.net/2022/07/31/wku8AebCrfiB734.png)
完成后双击它即可打开 Internet Explorer
![](https://s2.loli.net/2022/07/31/tpYF1SydDGPfRIm.png)