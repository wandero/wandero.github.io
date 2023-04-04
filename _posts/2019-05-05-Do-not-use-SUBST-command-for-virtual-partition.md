---
id: 1034
title: '不要使用 SUBST 命令虚拟分区'
date: '2019-05-05T22:37:04+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1034'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/19/190505%20%E4%B8%8D%E8%A6%81%E4%BD%BF%E7%94%A8%20SUBST%20%E5%91%BD%E4%BB%A4%E8%99%9A%E6%8B%9F%E5%88%86%E5%8C%BA.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
tags:
    - win
---

## 缺点

**使用 subst 命令创建的虚拟分区是没有回收站的，所有在虚拟分区路径下的删除操作会永久删除文件，不论 win7 win10**

<!-- more -->

## <del>优点</del>

<del>统一多 PC 的分区目录结构：在物理磁盘分区不一致的多 PC 环境中（仅 SSD / SSD + HDD / HDD 下多分区），虚拟分区可以构建统一的分区目录结构，顺便也能大幅缩短文件路径</del>

## <del>实现</del>

<del>导入注册表后重启生效（也可以通过批处理命令实现，详见 [SUBST 词条](https://en.wikipedia.org/wiki/SUBST)），将 D:vpare（实际目录） 虚拟为 E 盘 （虚拟目录）</del>

```
Windows Registry Editor Version 5.00

[HKEY_CURRENT_USERSOFTWAREMicrosoftWindowsCurrentVersionRun]
"E Drive"="SUBST e: d:vpare"
```

## <del>搜索</del>

<del>使用 Everything 和 Listary 等软件搜索时，词条中的 Method 3 不支持虚拟路径搜索。 Method 1 和 Method 2 则会同时显示文件实际路径结果（d:vparecloudlet.info）和虚拟路径结果（e:cloudlet.info），可在搜索软件中将虚拟分区实际文件夹的上级目录（如 d:vpar）设为排除文件夹，从而隐藏文件实际路径结果，只展示虚拟路径结果。</del>

## <del>卷标</del>

<del>当虚拟分区所在的实际磁盘分区卷标存在时，虚拟分区会复制实际分区卷标且不可修改。删除实际分区卷标后（显示为本地磁盘），可以重命名虚拟分区卷标。</del>

## <del>剪切</del>

<del>在同一实际分区内的虚拟分区之间移动文件时，使用实际路径会更快</del>