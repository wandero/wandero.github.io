---
id: 1098
title: '使用 Dell Mobile Connect 在 PC 上使用手机'
date: '2022-02-01T22:50:12+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1098'
permalink: /2022/02/01/%e4%bd%bf%e7%94%a8-dell-mobile-connect-%e5%9c%a8-pc-%e4%b8%8a%e4%bd%bf%e7%94%a8%e6%89%8b%e6%9c%ba/
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/22/220127%20%E4%BD%BF%E7%94%A8%20Dell%20Mobile%20Connect%20%E5%9C%A8%20PC%20%E4%B8%8A%E4%BD%BF%E7%94%A8%E6%89%8B%E6%9C%BA.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '1'
categories:
    - Notes
---

严格来说，是使用（最新版本，目前 v4.1） Dell Mobile Connect 在（任意非 Dell 的 Windows 10）PC 上使用手机（包括 iPhone）（接打电话、接发消息、接收通知）

## 安装

（非 Dell PC）直接在 Microsoft Store 中安装 Dell Mobile Connect 会提示 「此设备不满足安装软件的最低要求」

xxxxxxxxxx    #IfWinActive, ahk_class WeChatMainWndForPC    {        ;空格键翻页        {            $space::            send {PgDn}            return        }​        ;F1键后台打开鼠标指向链接        {            $f1::            click            sleep 500            send !{tab}            return        }    }autohotkey

```bash
echo Setting OEMID in RegEdit...
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Store" /v OEMID /f /t REG_SZ /d DELL
echo Setting SCMID in RegEdit
REG ADD "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Store" /v StoreContentModifier /f /t REG_SZ /d DELL_Xps
```

安装 [Dell Mobile Connect Driver](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=0gdtn&oscode=wt64a&productcode=xps-15-9560-laptop)

即可（安装）运行 Dell Mobile Connect

## 其他

### 程序版本

注意，网上的帖子大多说的是老版本的 Dell Mobile Connect，实际上（按照本文操作）最新的 Store 版本是可以在非 Dell 电脑上正常运行的

### 设备连接

连接失败多尝试几次（正确连接后 PC 上可浏览手机上的通讯录，可以看到手机的电量）

### 设备更换

似乎因为程序设计的原因，手机更换连接 PC 后无法通过 PC 主动拨号发消息，但仍可被动接受手机电话和通知

### 程序 后台

程序关闭后，一台电脑托盘中有图标，一台没有，但不影响使用