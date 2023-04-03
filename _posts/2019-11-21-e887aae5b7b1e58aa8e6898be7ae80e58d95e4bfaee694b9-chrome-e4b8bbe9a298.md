---
id: 1051
title: '自己动手简单修改 Chrome 主题'
date: '2019-11-21T21:18:19+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1051'
permalink: /2019/11/21/%e8%87%aa%e5%b7%b1%e5%8a%a8%e6%89%8b%e7%ae%80%e5%8d%95%e4%bf%ae%e6%94%b9-chrome-%e4%b8%bb%e9%a2%98/
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/19/191124%20%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E7%AE%80%E5%8D%95%E4%BF%AE%E6%94%B9%20Chrome%20%E4%B8%BB%E9%A2%98.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
tags:
    - chromext
---

虽然 Chrome 77 已经允许自定义浏览器主题颜色，Chrome 之前也推出过「我的Chrome 主题」应用可以自定义主题（已下架，但还能在其他地方找到），但如果因为浏览器版本或者自由度之类的问题仍然想小幅修改之前的 Chrome 主题的话（之前一些经典主题与现在的扁平风格不搭，一时也难以找到类似的配色），方法如下：

<!-- more -->

## 1、解压扩展

重命名 oldtheme.crx 为 oldtheme.zip，解压

## 2、修改图片

修改 images 文件夹中的图片，只是扁平化的话可以简单粗暴的把整张图片调成一个颜色（之前的主题大多有渐变色）

## 3、修改文件

修改 manifest.json，如果是比较老的主题，可能会缺少 `"manifest_version": 2,` （直接打包会报错 `The 'manifest_version' key must be present and set to 2 (without quotes). See developer.chrome.com/extensions/manifestVersion.html for details.`），另外可以修改下主题名称 `"name": "newtheme",`

## 4、打包安装

在 Chrome 的扩展程序页面打开「开发者模式」，点击「打包扩展程序」，「扩展程序根目录」选择 oldtheme 文件夹，点击「打包扩展程序」，新的 Chrome 主题出炉，将 newtheme.crx 拖入浏览器即可安装。