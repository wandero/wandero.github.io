---
id: 211
title: 'Chrome 禁止指定扩展自动更新'
date: '2013-11-27T15:10:11+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/211'
duoshuo_thread_id:
    - '6275546013931406082'
mytory_md_visits_count:
    - '148'
dotGood:
    - '13'
categories:
    - 工具二三
tags:
    - Chrome
---

## UPDATE

另一个简单一些的方法，将扩展文件夹重新打包为 crx（扩展程序-开发者模式-打包扩展程序）再安装

<!-- more -->

- - - - - -

Chrome 的扩展更新是自动后台进行的，最近遇到莫名升级又问题不断的 Mouse Stroke （2.0.3），无奈寻找禁止扩展更新方法，步骤如下：

## 1、准备工作

管理扩展程序-开发者模式 扩展介绍下显示扩展 ID

删除高版本，安装低版本，关闭浏览器

## 2、修改 manifest

根据扩展 ID 在 Chome 用户数据文件夹中编辑相应扩展的manifest，例如 Mouse Stroke的：  
`\User Data\Default\Extensions\aeaoofnhgocdbnbeljkmbjdmhbcokfdb\1.9.5.2_0\manifest.json`

将 `"version": "1.9.5.2"`  
修改为 `"version": "11.9.5.2"`（或其他类似高版本数字）

## 3、修改扩展版本目录

将如 `\User Data\Default\Extensions\aeaoofnhgocdbnbeljkmbjdmhbcokfdb\1.9.5.2_0`

中 `1.9.5.2_0` 修改为 `11.9.5.2_0`（或其他类似高版本数字）

## 4、修改用户配置中的 Preferences

将 `\User Data\Default\Preferences` 中 Mouse Stroke 部分`"version"` 内的 `1.9.5.2` 与 `path` 内的 `1.9.5.2_0` 分别修改为 `11.9.5.2`、`11.9.5.2_0`

## 5、BTW

传说中的修改扩展 manifest 中的 update.URL 方法是无效的