---
id: 1083
title: 'Kodi 简易上手指南'
date: '2021-12-12T21:22:24+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1083'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/21/211212%20Kodi%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
---

作为智能电视视频播放器的首选，Kodi 功能强大、定制性高同时也存在各种使用问题，本文以折腾记录为主介绍下 Kodi 的常规使用

<!-- more -->

## 下载

推荐 [官网下载](<https://kodi.tv/download/android>)，[历史版本](http://mirrors.kodi.tv/releases/android/)

## 安装

安装使用本地安装或 \[PC adb 推送安装\]() 均可

（版本不合安装时会报错 `Failed to extract native libraries, res=-113`，例如 ARMV7A 32BIT 和 ARMV8A 64BIT 混淆）

## 中文化

Kodi 内置中文界面，但切换中文前需要先修改默认字体（否则乱码）

在 Interface – Skin – Fonts 中将默认字体设置为 Arial based

在 Regional – Language 中将默认语言设置为 Chinese (Simple)，等待下载安装完成即可，如果因为网络等原因无法下载，可在 \[官网\] <https://kodi.tv/addons/matrix/search> 下载语言包，扩展同理

## 刮削

因为种种原因，建议使用 TinyMediaManager 进行刮削影视信息（注意 TMM v4 是收费版，v3 是免费版且功能足够常规使用）

TMM 除了刮削外可以对文件名和文件结构进行整理（菜单 – 重命名和整理），设置中可以修改命名规则，例如 `${originaltitle}.${year}.${mediaSource}.${videoFormat}.${videoCodec}.${videoBitDepth}bit.\${hdr}`

## 字幕

### PC 手动下载

一般 [字幕库](https://zimuku.org/) 和 [SUBHD](https://subhd.com/) 足够使用

### PC 自动下载

如果要求不高只需要中文字幕，使用[射手影音经典版](https://file.splayer.org/SPlayerSetup.exe?SPlayerSetup2437_701266.exe&from=splayer) 播放视频可自动下载相应字幕

### TV 插件下载

[zimuku for kodi](<https://github.com/pizzamx/zimuku_for_kodi>) 用于从字幕库下载字幕，目前只有 [Kodi V19](https://kodi.tv/) 版本。

## 媒体库

### 硬件

没有 NAS 和高性能路由，用的 PC 接大硬盘方案走局域网共享方案。普通路由 CPU 性能弱，接硬盘播放高帧率视频会严重卡顿，还有 USB2 的速度限制和 USB3 对 WIFI 的干扰，均不推荐。为流畅播放 4K 影视，建议有线或 5G WiFi。局域网共享有几种方式可以选择

### SMB 方式

SMB 1.0 不需要密码，但因安全原因普遍被放弃，建议使用 WIN10 默认开启的 smb v2/v3（需要用户名和密码）

#### PC 端

设置 专用网络

网络状态 – 属性 – 网络配置文件 – 专用

开启 网络共享和网络发现

共享文件夹

文件夹属性 – 共享 – 共享 – 选择要与其共享的用户

选择或创建带密码的用户

#### TV 端

视频 – 添加视频 – 浏览 即可打开媒体库目录配置菜单

注意 默认的 Windows 网络（SMB） 无效，需要在 添加网络位置 中设置 IP、用户名、密码 后添加

该目录包含 选择 电影/剧集

信息提供者 提供 Local information only （已由 TMM 刮削好）

#### 设置 SMB 播放缓冲

在 Kodi 配置文件夹内添加文件如下


adb push d:\\p\\t\\advancedsettings.xml /sdcard/Android/data/org.xbmc.kodi/files/.kodi/userdata

adb pull /sdcard/Android/data/org.xbmc.kodi/files/.kodi/userdata/advancedsettings.xml d:\\p\\t

#### 检查缓冲设置是否生效

高清视频体积较大，缓冲条不明显，建议使用几百兆的视频，可以看到清晰的灰色缓冲进度条

网上说 19 版本缓冲失效，实际上 19 版本仍然可以看到缓冲进度条，但卡顿问题复杂，可以考虑更换共享方式

### FTP 方式

FTP 方式兼容性相对较差，影视海报信息现实情况也不如 SMB，但默认对视频播放提供缓冲，SMB 方式播放卡顿可考虑 FTP 方式

### NFS 方式

需要安装单独软件且没有免费和方便实现方案

## 设置

### 人声/对白 音量过小

使用电视自带音箱（2.0声道）播放视频（5.1 以上声道）时，因为没有中置的关系，人声/对白音量会显著小于背景音

调整 设置&gt;音频设置&gt;混缩:中置混合级别 即可

### 3D 源文件出现分屏（左右、上下）

在视频播放菜单中调整视频流设置

### 启动 Kodi 自动进入电影页面

设置里没有该功能，需要通过自定义脚本实现，建立一个 名为 `autoexec.py` 的文件，内容： `import xbmcxbmc.executebuiltin('XBMC.ActivateWindow(Videos,MovieTitles,return)')`

放在应用目录 \\~/.kodi/userdata 中

`adb push d:\\cloudlet.info\\autoexec.py /sdcard/Android/data/org.xbmc.kodi/files/.kodi/userdata`

## 其他

### Xbox 版

xbox 版 Kodi 默认关闭 SMB 协议，需要在 kodi-系统-插件-我的插件-虚拟文件系统- smb support 启用

因版权等因素限制，xbox 版 Kodi 对小部分编码视频支持有问题，大部分还好