---
title: QEMU 安装 Windows ARM
date: 2022-07-10 21:33:43
categories: 
	- [虚拟机,QEMU]
	- [教程,Windows]
tags:
	- Windows
	- QEMU
sticky: 96
description: 用 QEMU 模拟 AArch64(ARM64) 以安装 Windows ARM
cover: https://wiki.betaworld.cn/images/thumb/b/b1/Win11_on_QEMU_ARM64_Linux.png/718px-Win11_on_QEMU_ARM64_Linux.png
keywords: QEMU,虚拟机,VM,KVM,Windows,ARM,ARM64,arn,arm64,aarch64,AArch64,x86,WindowsARM,Arm Windows
---

## 实验环境
{% post_link tutorial/Windows/UUP Windows ARM %}

------

3.1.2022 更新
建议在构建镜像的时候用 uup.rg-adguard，那个可以移除安装限制，可以有效避免 TPM 问题（因为还不会怎么模拟 TPM）
或者自己手动修改镜像

------

[QEMU 最新版](https://qemu.weilnetz.de)
<font size=3 color=yellow>QEMU 的安装位置需要记牢，在安装程序会出现，后面需要用到</font>
![QEMU 安装路径](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU1.png)
[UEFI 固件](https://www.kraxel.org/repos/jenkins/edk2)
<font size=3 color=yellow>下载文件名开头为 edk2.git-aarch64 的文件，并用 7-Zip 等解压缩工具多次解压，直至提取出 QEMU_EFI.fd 和 vars-template-pflash.raw 这两个文件</font>
[VirtIO ARM64 驱动光盘](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/latest-virtio/virtio-win.iso)
![QEMU_EFI.fd 和 vars-template-pflash.raw](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU2.png)

------

如果你觉得从以上的站点下载解压文件太麻烦，可以直接到我的 OneDrive 站点下载打包好的所需文件（不包括系统镜像，不一定为最新）
[OneDrive](https://ys8rx-my.sharepoint.com/:f:/g/personal/gucats_ys8rx_onmicrosoft_com/Et7P87cp3vpHpmx7G5xWNEkB3BazOdGz0zdoMUzpVsv3Kg?e=AcSkXc)

------

## 配置环境变量
按下 <kbd>Windows 徽标键</kbd>+<kbd>R</kbd>，输入 <code>SystemPropertiesAdvanced</code> 并回车
点击“环境变量”
![环境变量 1](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU3.png)
在“系统变量(S)”里找到名为“Path”的项并双击，点击旁边的“新建(N)”，最后在矩形框中输入 QEMU 的安装目录
![环境变量 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU4.png)
然后全部点击“确定”即可

## 创建硬盘文件
按下 <kbd>Windows 徽标键</kbd>+<kbd>Q</kbd>，输入 CMD，并右键选择“以管理员身份运行”
![CMD](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU5.png)
然后输入以下命令
```CMD
qemu-img.exe create -f 硬盘格式 <自定义存放路径\文件名.硬盘格式> <容量大小><单位>
```
比如我的存放位置为 E:\QEMU\ARM，文件名为 OS，硬盘格式为 qcow2（可选的有还 raw、host_device、qcow、cow、vdi、vmdk、vpc、cloop、img），容量大小为 60GB（单位有 K、M、G、T、P、E）
那么我的命令如下（<font size=3 color=yellow>需要区分大小写，而且路径和文件名不要有空格，用下划线 _ 代替</font>）
```CMD
qemu-img.exe create -f qcow2 E:\QEMU\ARM\OS.qcow2 60G
```
没有别的提示就代表成功了
![创建硬盘文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU6.png)

<font size=3 color=red>最后，将 QEMU_EFI.fd、vars-template-pflash.raw 这两个文件一并复制到存放位置</font>

## 启动系统
在存放的目录（我的是 E:\QEMU\ARM）下新建文本文档，命名为 start.cmd，并编辑内容【<>里的内容（包括引号）是需要自行修改的内容，你可以在最顶端插入 chcp 65001，这样 cmd 内提示的中文报错就不会乱码】
```CMD
qemu-system-aarch64.exe -M virt,virtualization=true -cpu cortex-<CPU 型号> -smp <CPU 核心数> -m <运行内存大小> ^
-device qemu-xhci -device usb-kbd -device usb-tablet ^
-drive file=<"硬盘文件路径\文件名.qcow2">,if=virtio ^
-nic user,model=virtio ^
-drive file=<"系统镜像路径\文件名.iso">,media=cdrom,if=none,id=cdrom -device usb-storage,drive=cdrom ^
-drive file=<"virtio-win 所在路径\virtio-win 的名称.iso">,media=cdrom,if=none,id=cdrom1 -device usb-storage,drive=cdrom1 ^
-bios QEMU_EFI.fd -device ramfb ^
-drive file=vars-template-pflash.raw,if=pflash,index=1,format=raw
```
比如我的 CPU 型号为 a76（可选的还有 a72,a57 和 a53，亦或者是其它）
CPU 核心数量为 4，运行内存大小为 4096MiB
硬盘文件、系统镜像和 virtio-win 镜像命名为 Image.iso,OS.qcow2 和 virtio-win-0.1.225.iso
（若 start.cmd 与前面几个文件在同一目录下就不需要指定目录，直接填写名称即可）
那么我的命令如下（<font size=3 color=yellow>需要区分大小写，而且路径和文件名不要有空格，用下划线 _ 代替，或者在收尾添加英文引号： <code>"</code></font>）
```CMD
qemu-system-aarch64.exe -M virt,virtualization=true -cpu cortex-a76 -smp 4 -m 4096 ^
-device qemu-xhci -device usb-kbd -device usb-tablet ^
-drive file=OS.qcow2,if=virtio ^
-nic user,model=virtio ^
-drive file=Image.iso,media=cdrom,if=none,id=cdrom -device usb-storage,drive=cdrom ^
-drive file=virtio-win-0.1.225.iso,media=cdrom,if=none,id=cdrom1 -device usb-storage,drive=cdrom1 ^
-bios QEMU_EFI.fd -device ramfb ^
-drive file=vars-template-pflash.raw,if=pflash,index=1,format=raw
```
保存后双击运行，如果正常会是这样，可以进入到 TinaoCore Logo 的引导页
![启动 Windows](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU7.png)

------

若有如下报错为正常，无需理会
第一个是未指定 vars-template-pflash.raw 的格式（已在文中更新代码，故不会出现该报错），第二个不知道有什么用（反正不影响.jpg
![报错 1](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU8.png)

但或者是这种找不到文件的报错，则需要自己在文件名前加上路径
![报错 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU8.1.png)

------

然后就这样漫长的等待，就会进入到 Windows 安装程序页（按下 <kbd>Ctrl</kbd>+ <kbd>Alt</kbd>+<kbd>G</kbd> 即可将鼠标脱离虚拟机）
![Windows 安装程序](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU9.png)

## 安装系统
在选择磁盘的时候，点击“加载驱动程序(L)”
![加载驱动程序](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU10.png)
选择“浏览(B)”
![浏览](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU11.png)
选择 virtio-win 光驱
![选择 virtio-win 光驱](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU12.png)
找到名为“viostor”的文件夹，选择里面“w11”文件夹下的“ARM64”文件夹（如果安装的是 Windows 10 则选择 w10）
![选择 virtio 驱动](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU13.png)
选择驱动程序，然后点击“下一页(N)”，这样就可以正常安装系统了
![选择驱动](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU14.png)
最后进入无尽的等待...
![复制文件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU15.png)
x86 转译 AArch64 性能会有所下降（不止一点点，再加上 QEMU 是软件模拟），所以安装时间会比普通的虚拟机要长不知道多少倍（
<font size=1>*记得开启“鼠标经过时捕获”（“Grab On Hover”）或“捕获输入”（“Grab Input”）</font>
![鼠标经过时捕获](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU15.1.png)

从进入安装程序到准备就绪，花了近一个半小时（
没什么意外的话，可能这个要转 114514h（悲
（而且鉴于无法联网，且硬盘驱动都要自己加载，所以这个过程跳过也没啥问题（）
![准备就绪](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU16.png)

------

这里不得不说一下 CPU 才 1.0Ghz 属实吝啬，不过不难看出它真的在动了（
有需要的话可以自己搜一下 [QEMU 配置 CPU](https://cn.bing.com/search?q=QEMU+%E9%85%8D%E7%BD%AE+CPU)
![CPU 信息](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU17.png)
当我把 QEMU 升级之后之后就被识别出是虚拟机力（无慈悲
![CPU 信息 2](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU17.1.png)

------

按下 <kbd>Shift</kbd>+<kbd>F10</kbd> 打开 CMD 窗口，并输入以下命令
```CMD
OOBE\MSOOBE
```
然后就会跳过那漫长的准备就绪阶段
![命令（卡一下才会自动重启）](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU18.png)
![下一阶段](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU19.png)
再等待亿会，就可以进入 OOBE 了
![OOBE](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU20.png)


由于暂时没有网卡驱动，且 Windows 11 要求联网才能继续，所以需要跳过联网激活验证（Windows 10 可跳过该步骤）
按下 <kbd>Shift</kbd>+<kbd>F10</kbd> 打开 CMD 窗口，并输入以下命令
```CMD
OOBE\BypassNRO
```
（如果这期间 OOBE 仍要求联网，可以打开 CMD 窗口，输入 <code>explorer</code> 并打开，然后再按[网卡驱动](#网卡驱动)的方式安装网卡驱动）
![命令](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU21.png)
等待一会，系统会自动重启，然后就可以继续正常安装了
![请稍等](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU22.png)
可能你会遇到“为什么我的电脑重启了?”这个提示，无需理会，点击“下一步(N)”即可
![为什么我的电脑重启了?](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU23.png)
接着就可以按照正常方式继续安装了

一切都开始好起来力）
![此操作可能需要几分钟](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU24.png)
![进入桌面](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU25.png)

## 网卡驱动
右键“开始菜单”按钮，选择“Windows PowerShell（管理员）”（或者在 CMD 窗口输入 <code>powershell</code> 也可以）
然后在命令框中输入以下命令并重启
```PowerShell
bcdedit /set testsigning on
```
![开启测试模式](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU26.png)

在文件资源管理器里打开 virtio-win 光驱，然后定位到 \NetKVM\w11\ARM64（如果是 Windows 10 就选择 w10 文件夹）
右键类型为“安装信息”的 netkvm 文件，选择“安装”
![安装 netkvm](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU27.png)
在弹出的 UAC 窗口中选择“是”
![UAC](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU28.png)
等待一会，就提示安装完成
![安装完成](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU29.png)
再等一会就有网络了

这是最后在里面运行 Dism++ ARM64 的效果（启动速度和运行效率会比 x86 转译 ARM64 快许多）
![运行软件](https://gcore.jsdelivr.net/gh/Goo-aw233/WebSiteResources@main/Pics/WindowsARMonQEMU/WindowsARMonQEMU30.png)

## 后话
1.如果你后面不需要光驱了可以把
<code>-drive file=<"系统镜像路径\文件名.iso">,media=cdrom,if=none,id=cdrom -device usb-storage,drive=cdrom ^
-drive file=<"virtio-win 所在路径\virtio-win 的名称.iso">,media=cdrom,if=none,id=cdrom1 -device usb-storage,drive=cdrom1 ^</code>
这两行代码删除

2.因为没有显卡驱动以及其它的驱动，在 QEMU 模拟 Windows ARM 性能会大打折扣，整个过程会非常漫长，建议将文件存放在 SSD 内

3.文章内仅模拟了所需的硬件及网卡，其它的硬件需要自行查询
镜像内其它驱动的大致意思如下：<sup><a href="#参考文献">[3]</a></sup>
NetKVM/: Virtio 网络驱动
viostor/: Virtio 块驱动
vioscsi/: Virtio SCSI 驱动
viorng/: Virtio RNG 驱动
vioser/: Virtio 串口驱动
Balloon/: Virtio 内存气球驱动
qxl/: 用于 Windows 7 及之前版本的 QXL 显卡驱动. (virtio-win-0.1.103-1 和之后版本会创建)
qxldod/: 用于 Windows 8 及之后版本的 QXL 显卡驱动. (virtio-win-0.1.103-2 和之后版本会创建)
pvpanic/: QEMU pvpanic 设备驱动 (virtio-win-0.1.103-2 和之后版本会创建)
guest-agent/: QEMU Guest Agent 32bit 和 64bit 安装包
qemupciserial/: QEMU PCI 串口设备驱动
*.vfd: 用于 Windows XP 下的 VFD 软驱镜像

4.如果真的很慢可以看看 BetaWiki 给出的解决方案（不一定 100% 有效）
```CMD
sc stop "Spooler"
sc config "Spooler" start= disabled
sc stop "WSearch"
sc config "WSearch" start= disabled
REM Disable Automatic Defragmentation
schtasks /Delete /TN "\Microsoft\Windows\Defrag\ScheduledDefrag" /F
REM Disable Pagefile
wmic computersystem set AutomaticManagedPagefile=FALSE
wmic pagefileset delete
REM Disable Hibernation
powercfg -h off
```

## 参考文献
1. <a name = "ref1" href="https://wiki.betaworld.cn/%E5%A6%82%E4%BD%95%E5%9C%A8QEMU%E4%B8%AD%E5%AE%89%E8%A3%85Windows_Client_ARM64">BetaWorld Wiki（由此改编）</a>
2. <a name = "ref1" href="https://wiki.betaworld.cn/%E6%96%87%E4%BB%B6:Win11_on_QEMU_ARM64_Linux.png">封面：BetaWorld Wiki</a>
3. <a name = "ref1" href="https://blog.51cto.com/dangzhiqiang/1833615">51CTO 博客——党志强</a>