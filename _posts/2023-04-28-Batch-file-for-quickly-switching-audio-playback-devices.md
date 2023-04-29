---
layout: post
title: "批处理快速切换声音播放设备"
date: 2023-04-28 20:00:00 +0800
categories: 工具二三
tags:
    - BAT
---

PC 存在多个音频播放设备时，一般需要通过任务栏系统图标来切换，这样比较麻烦，继续批处理，Windows 10 没有原生命令，所以需要借助第三方工具，选择的 nircmd

nircmd 似乎只有两个声音设备相关的命令：

`showsounddevices` 显示所有声音设备的友好名称

`setdefaultsounddevice "耳机"` 切换至指定声音设备

<!-- more -->

需要注意，"耳机"这种就是所谓的友好名称，很多会重名，在任务栏声音图标右键，选择声音，可以在默认的播放面板中看到并修改

然后建立 sounddeviceswitch.bat 文件

```bat
@echo off
echo 切换到内置声卡
C:\O\0little\nircmd.exe setdefaultsounddevice "内置声卡"
```

可以根据实际情况分别建立几个 bat 文件，然后在 path 中建立对应的快捷方式从而可以 Win+R 快速切换

也可以使用一个 bat 文件文件搞定，nircmd 似乎无法实现一个 bat 自动切换

```bat
@echo off
set /p input="请输入 1(内置声卡)、2(外置声卡) 、3（显示器）："

if "%input%"=="1" (
    echo 切换到内置声卡
    C:\O\0little\nircmd.exe setdefaultsounddevice "内置声卡"
) else if "%input%"=="2" (
    echo 切换到外置声卡
    C:\O\0little\nircmd.exe setdefaultsounddevice "外置声卡"
) else if "%input%"=="3" (
    echo 切换到 DELL S2721QS
    C:\O\0little\nircmd.exe setdefaultsounddevice "显示器"
) else (
    echo 无效的输入，请输入 1、2 或 3。
)

```

