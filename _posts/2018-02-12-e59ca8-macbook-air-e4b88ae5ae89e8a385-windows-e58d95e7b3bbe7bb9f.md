---
id: 923
title: 'MacBook Air 安装 Windows 单系统'
date: '2018-02-12T22:29:56+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=923'
permalink: /2018/02/12/%e5%9c%a8-macbook-air-%e4%b8%8a%e5%ae%89%e8%a3%85-windows-%e5%8d%95%e7%b3%bb%e7%bb%9f/
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/18/180212%20%E5%9C%A8%20MacBook%20Air%20%E4%B8%8A%E5%AE%89%E8%A3%85%20Windows%20%E5%8D%95%E7%B3%BB%E7%BB%9F.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '2'
categories:
    - Notes
---

需求略囧，不过受人之托，忠人之事……此类操作网上教程雷同的很多，但有些地方说的不大清楚，折腾完毕顺便记录

## 准备启动 U 盘

U 盘需已定制常规 Windows 启动工具（带 Win8 以上 PE、DiskGenius、Windows 安装器），另剩余可用空间 6G 左右，以储存系统安装文件和 Boot Camp 安装文件。

## 下载 Boot Camp

在 [官方页面](https://support.apple.com/zh-cn/boot-camp) 下载对应型号的 Boot Camp 解压至 U 盘备用（注意选择目标系统后查询兼容性表格，确认笔记本型号与目标系统兼容，例如本文 MBA 型号为「 13 英寸，2013 年中」，可装 Windows7 64 位）

## 准备待处理文件

Win7 官方安装文件未集成 USB3 驱动，需额外添加（否则 Windows 安装会因为键盘和触控板失效无法进行）

在其他电脑（似乎必须，后面用到的 dism 命令需要完整的 Win7 以上系统支持，PE 不行）新建任意文件夹（假定为 `D:\fix`），在其中新建 usb3 和 mount 文件夹（名称涉及后续命令）。

将 Boot Camp 文件夹中的`\$WinPEDriver\$\IntelxHCISetup\Drivers\xHCI\Win7\x64\` 和`\$WinPEDriver$\IntelxHCISetup\Drivers\HCSwitch\Win7\x64\` 下的全部文件复制至 usb3 文件夹。

将系统安装文件（ISO 可以使用 WinRar 解压）内 sources 下的 install.wim 和 boot.wim 复制到 fix 文件夹。

## 集成 USB3 驱动

在 CMD 中依次运行如下命令（注意第8行 index：4 对应的是 Win7 Ultimate ，其他版本需修改）：

```
d：

cd fix

dism /mount-wim /wimfile:boot.wim /index:2 /mountdir:mount

dism /image:mount /add-driver /driver:usb3\iusb3hub.inf

dism /image:mount /add-driver /driver:usb3\iusb3xhc.inf

dism /image:mount /add-driver /driver:usb3\iusb3hcs.inf

dism /unmount-wim /mountdir:mount /commit

dism /mount-wim /wimfile:install.wim /index:4 /mountdir:mount

dism /image:mount /add-driver /driver:usb3\iusb3hub.inf

dism /image:mount /add-driver /driver:usb3\iusb3xhc.inf

dism /image:mount /add-driver /driver:usb3\iusb3hcs.inf

dism /unmount-wim /mountdir:mount /commit
```

成功运行所有命令后，将 fix 下新生成的 install.wim 和 boot.wim 和其他系统安装文件一起复制到 U 盘任意文件夹备用。

## 使用 Windows 安装器 安装系统

MBA 插上 U 盘，启动后按住 option 键直至出现启动选择界面，选择 U 盘启动（显示为 Windows 之类），进入 WinPE。

使用 DiskGenius 重新分区（删除所有分区再新建，快速分区比较方便，文件系统均设置为 NTFS），并且切换到 MBR 引导（「硬盘」 – 「转换分区表类型为 MBR 格式」）。

将 U 盘内处理好的系统安装文件复制到 MBA 的非系统分区。

运行 Windows 安装器，「镜像路径」选择之前处理后复制到非系统分区的 install.wim，「选择引导驱动器」和「安装磁盘位置」默认 C：。（这里第一次安装的时候出了问题导致系统安装到了 D 盘，第二次勾选了「挂载安装驱动器」和「预分配驱动器盘符」正常）提示操作完成重启后会自动进入常规 Windows 安装界面。常规操作直至完成系统安装。

## 使用 Boot Camp 安装驱动

（Win7 系统安装完成后）运行 U 盘上之前复制的 Boot Camp，会自动安装所有驱动。另外可点击任务栏图标中的 Boot Camp 进入控制面板设置，勾选「键盘」-「将 F1、F2 等键用作标准功能键」和「触控板辅助单击」（右下角）。

## 使用易数一键还原建立恢复系统

（建立傻瓜恢复系统是装系统、修电脑工作的重中之重）

之前流行的各种 ghost 系一键还原软件一来找不到可靠来源，二来似乎是因为修改引导区的机制导致杀软报毒，最后找到了（DiskGenius 的）[易数的一键还原](http://www.onekeyrestore.cn/)，短暂体验了下好像还不错，默认安装模式会在系统启动前插入一键还原界面，按下 F3 会进入系统还原界面（此时 MBA 的触摸板会失效，可以用键盘操作）

（折腾过程主要参考了 [MacBook Air 2014款安装 windows7 单系统](https://www.jianshu.com/p/3139926ce2ed)，感谢）