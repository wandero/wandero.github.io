---
id: 1268
title: 'Logseq  移动端使用'
date: '2023-01-12T20:36:00+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1268'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/23/230112%20Logseq%20%20%E7%A7%BB%E5%8A%A8%E7%AB%AF%E4%BD%BF%E7%94%A8.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
tags:
    - Logseq
excerpt_separator: <!-- more -->
---

Logseq 同步功能迟迟不能正式发布，移动端轻度使用或隐私要求不高可以使用 iCloud 或坚果云等同步软件代替

## css

移动端基本可直接使用 PC 端 CSS，在 设置 – 自定义主题 – 编辑 custom.css（当前库） 中复制粘贴 PC 端 的 custom.css 内容即可（可以通过滴答清单或邮件之类应用中转，坚果云打开会乱码，微信转发长度受限，替换 custom.css 可以使用 select 再手动选择全部内容删除，select all 无效）

<!-- more -->

## iOS 端 只读访问 PC 端内容

Windows 安装 iCloud，使用 Goodsync（或其他同步软件）定时单向同步坚果云（保障 PC 间同步）中的 logseq 文件夹内容至 iCloud~com~logseq~logseq 内

注意先在同步软件中设置好不需要同步的文件夹，特别是 logseq 中的 bak 和 recycle，iCloud 同步速度可能非常慢，不选择文件夹几万个文件会同步好几天，一直显示 正在上传

文件同步有时会导致 ios 端页面消失，点击右上角菜单图谱名处（icloud 同步会是 Documents）点击刷新即可

## Android 端同步访问 PC 端内容

Foldersync 同步坚果云, 海信 A5 不知道是不是安卓版本过低，尝试了几乎所有版本都无法正常使用（选择文件夹后崩溃或者说重启）