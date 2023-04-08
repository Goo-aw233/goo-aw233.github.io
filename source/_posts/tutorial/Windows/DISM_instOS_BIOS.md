---
title: BIOS 使用 DISM 命令安装系统
date: 2023-01-13 12:23:52
categories: 
	- 教程
	- Windows
tags: Windows
description: BIOS(Legacy) 启动使用 DISM 与 CMD 安装系统
---

**如果你使用的是 UEFI 启动请看下一篇文章{% post_link tutorial/Windows/DISM_instOS_UEFI 《UEFI 使用 DISM 命令安装系统》 %}**

## 操作磁盘
在 CMD 中输入如下命令

```CMD
DiskPart
List Disk
```

在列表中会展现出计算机上所有已安装的磁盘
![磁盘列表](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS1.png)
确定好需要格式化的磁盘，输入命令

```CMD
Select Disk <磁盘编号>

# 如果你需要选择磁盘 0 则命令如下

Select Disk 0
```

### 删除磁盘
#### 如果你的磁盘上有其它分区
列出磁盘内的分区

```CMD
List Partition
```

![分区列表](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS2.png)

选择你需要进行操作并删除的分区
依照以下命令可以多次执行


<blockquote>
<q>若要删除动态卷，请始终改为 使用 Delete Volume 命令。</q>
</blockquote>

```CMD
Select Partition <分区编号>
Delete Partition

# 如果你需要选择分区 1 并删除，则命令如下

Select Partition 1
Delete Partition
```

![操作分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS3.png)

<blockquote>
若要删除受保护的磁盘（如类型为“系统”与“保留”），则需要在 <code>Delete Partition</code> 命令后添加 <code>Override</code> 参数<br>
如果需要一次性将磁盘上所有分区删除，请使用 <code>Clean</code> 命令，然后再用 <code>Convert MBR</code> 将磁盘转换为 MBR</br>
</blockquote>

![参数](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS4.png)

最后再次使用 <code>List Partition</code> 即可看到<q>这个磁盘上没有显示的分区。</q>

------

#### 如果你的磁盘上没有其它分区
如果磁盘是空白的请继续往下看[创建分区](#创建分区)

------

### 创建分区
#### 创建主分区
使用命令创建主分区

<blockquote>
在 MBR 磁盘上，至多创建 4 个主分区；或者 3 个主分区+1 个拓展分区
</blockquote>

```CMD
Create Partition Primary Size=<分区大小>

# 分区大小以 MiB 为单位，1GiB=1024MiB（微软常常会省略中间的“i”不写）
# 若我需要创建一个大小为 50GiB 的主分区作为系统盘，9GiB 的主分区作为其它盘则命令如下

Create Partition Primary Size=51200
Create Partition Primary Size=9216
```

![创建主分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS5.png)

<blockquote>
如果将 <q>Size=<分区大小></q> 这个参数去掉，则会默认将所有可用的空间创建为一个分区
</blockquote>

### 格式化磁盘
使用以下命令格式化磁盘
主要分区：

```CMD
List Partition
Select Partition <分区编号>
Format fs=NTFS Quick
Assign Letter=<盘符>

# 若我需要格式化第 1 个分区，文件系统为 NTFS 并快速格式化，盘符为 C，则命令如下
# 可多次重复命令直至需要的所有分区被创建

List Partition
Select Partition 1
Format fs=NTFS Quick
Assign Letter=C
Active

# Active 命令只针对于 C 盘，其它盘无需设置
```

![格式化分区](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS6.png)

完成后使用命令查看所有卷

```CMD
List Vol
```

![所有卷](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS7.png)

完成以后退出 DiskPart 即可

```CMD
Exit
```

## 安装系统

输入命令来查看 WIM/ESD 映像内可用的系统版本

```CMD
DISM.exe /Get-WimInfo /WimFile:<WIM/ESD 存放路径>

# 假如我存放在 E 盘下的 Sources 文件夹并命名为 install.wim，则命令如下

DISM.exe /Get-WimInfo /WimFile:E:\Sources\install.wim
```

![查看可用系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS8.png)

然后，再将映像部署到本地磁盘

```CMD
DISM.exe /Apply-Image /ImageFile:<WIM/ESD 存放路径> /Index:<映像内第几个版本> /ApplyDir:<安装的盘符>:\

# 假如我存放在 E 盘下的 Sources 文件夹并命名为 install.wim，需要安装第一个版本，并安装在 C 盘，则命令如下

DISM.exe /Apply-Image /ImageFile:E:\Sources\install.wim /Index:1 /ApplyDir:C:\
```

等待一会，DISM 将开始部署映像
![安装系统](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS9.png)
几分钟后系统就安装完成了
![结束安装](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS10.png)

## 修复引导
重建 MBR 并修复引导

```CMD
Bootrec.exe /FixMbr
BCDBoot C:\Windows /l zh-cn
```

![修复引导](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS11.png)

最后重启计算机即可看到 Windows 启动了

![启动 Windows](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/DISM_instOS_BIOS/DISM_instOS_BIOS12.png)