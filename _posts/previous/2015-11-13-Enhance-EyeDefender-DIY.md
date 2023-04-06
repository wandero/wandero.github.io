---
id: 313
title: '自己动手增强 EyeDefender（番茄钟定时展现随机壁纸）'
date: '2015-11-13T14:40:50+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/313'
duoshuo_thread_id:
    - '6275546054809092866'
mytory_md_visits_count:
    - '61'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/15/151113%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%A2%9E%E5%BC%BA%20EyeDefender%EF%BC%88%E7%95%AA%E8%8C%84%E9%92%9F%E5%AE%9A%E6%97%B6%E5%B1%95%E7%8E%B0%E9%9A%8F%E6%9C%BA%E5%A3%81%E7%BA%B8%EF%BC%89.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/15/151113%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E5%A2%9E%E5%BC%BA%20EyeDefender%EF%BC%88%E7%95%AA%E8%8C%84%E9%92%9F%E5%AE%9A%E6%97%B6%E5%B1%95%E7%8E%B0%E9%9A%8F%E6%9C%BA%E5%A3%81%E7%BA%B8%EF%BC%89.md'
dotGood:
    - '2'
categories:
    - 工具二三
tags:
    - BAT
    - GTD
    - 番茄钟
---

EyeDefender 能以番茄钟形式定时展示全屏壁纸，但美中不足的是只能选择固定图片，对比 Chrome 上的 Flickr Tab 和 Unsplash Instant 不免相形见绌，好在仍然可以通过批处理命令手动增强。

<!-- more -->

## 功能

实现 EyeDefender 定时展现指定文件夹内随机壁纸（对于没有用过 EyeDefender 的同学来说，可以理解为每隔28分钟你的屏幕上会随机显示一张指定文件夹内的图片，持续2分钟，这两分钟你可以退出壁纸继续努力工作，喝水散步伸懒腰扰乱工作秩序，以及盯着壁纸看满时间……）

## 代码

**vbs 文件**（静默调用 bat 文件）

```
set ws=wscript.createobject("wscript.shell")
ws.run "helloworld.bat /start",0
```

（如果你和我一样同为代码盲）请将代码中 helloworld 改为你接下来的 bat 文件名称，例如 seeyouwork，并将其复制到记事本中保存退出，将该文本文件改名为 abc.vbs，并建立快捷方式，拖入系统 startup 文件夹。

**bat 文件** （功能实现）

```
@echo off
:main
setlocal enabledelayedexpansion
for %%a in (d:\pic\*.jpg) do set/a "n+=1" & set "jpg!n!=%%a"
set/a "a=%random%%%!n!+1"
copy /y "!jpg%a%!" "d:\pic\eyedefender\0.jpg"
ping -n 1800 127.1>nul
goto main
```

（如果你和我一样同为代码盲）记得将代码中的 `d:\pic\` 修改为自己的图片文件夹目录，将 `d:\pic\eyedefender\0.jpg` 修改为自己的展示图片位置，并在 EyeDefender 中指定。`1800` 为设定更换图片时间，例如番茄钟设定为 28-2 30分钟的话1800秒刚好。

## 其他

说到随机壁纸，个人觉得现在 Chrome 上最赞的是 FlickrTab，看到养眼的风景收下来扔到图片文件夹，改造过的 EyeDefender 没准就会在某个眼痛手酸的时候给你一剂心灵鸡汤了。