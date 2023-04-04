---
id: 428
title: '使用 OneTab 处理 Chrome 页面的稍后阅读'
date: '2017-02-24T16:05:02+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/428'
duoshuo_thread_id:
    - '6390582799509750529'
mytory_md_visits_count:
    - '264'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170224%E4%BD%BF%E7%94%A8%20OneTab%20%E5%A4%84%E7%90%86%20Chrome%20%E9%A1%B5%E9%9D%A2%E7%9A%84%E7%A8%8D%E5%90%8E%E9%98%85%E8%AF%BB.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170224%E4%BD%BF%E7%94%A8%20OneTab%20%E5%A4%84%E7%90%86%20Chrome%20%E9%A1%B5%E9%9D%A2%E7%9A%84%E7%A8%8D%E5%90%8E%E9%98%85%E8%AF%BB.md'
categories:
    - smgmt
tags:
    - Chrome
    - read
---

OneTab 通常被视为减少内存的占用，实际上相比减少内存占用，较为理想的稍后阅读功能才是它的核心

<!-- more -->

## 与相关功能的区别

### 与原生书签栏的区别

#### 添加书签

（自定义处理之后）都很便捷，Chrome 依托 MouseStroke 可以实现鼠标手势直接将页面加入书签栏根目录，依托 OneTab （Chrome – 扩展程序-键盘快捷键）可以实现 F1 （F1 需要 AutoHotkey 映射）将页面加入 Onetab

#### 呈现书签

书签栏虽然可以分类，但分类需要额外的操作，而对于稍后阅读功能，更缺少关键的OneTab 能自动添加的日期属性（另一方面，OneTab 通过处理也可以实现一定程度的分类）

顺便说句，OneTab 的主页面也可以加入书签栏……

#### 整理书签

OneTab 的 打开标签页并将其从OneTab列表中删除 功能（仍然可以按ctrl、cmd或shift来恢复标签页，而且不会将其从OneTab中删除）显然更加方便和灵活

### 与论坛原生收藏的区别

OneTab 中待处理的页面更直观，不需要先打开特定站点才能了解有书签有无和具体多少。但论坛原生收藏功能做的完善的话，收藏页面包含的信息量会更大

## OneTab 的同步

OneTab 没有提供原生的同步功能（仅有手动导入导出选项，且会丢失标签页时间属性），而它的内容配置又偏偏在 User DataDefaultLocal Storage 中（chrome-extension\_chphlpgkkbolifaimnlloiipkdnihall\_0.localstorage），给同步带来了一定的麻烦

对于不支持符号连接的坚果云来说，只有同步整个 LocalStorage（这样似乎会带来不少站点每次都要重新登录之类的副作用以及剧增的流量），或者使用第三方命令定期同步至坚果云文件夹内（比较麻烦）

对于支持文件符号链接的 Dropbox 来说就比较轻松了，详见 [通过 mklink 使用 Dropbox 同步任意位置文件](http://cloudlet.info/t/425)

## OneTab 的整理

OneTab 的导出功能可以将全部书签导出为文本（会丢失时间属性），在数量巨大的时候可以使用 Excel 根据书签 URL 筛选排序删除等等重新排序分组标签页，效果不错

**其他**

[稍后阅读类应用使用小结](http://cloudlet.info/t/395)