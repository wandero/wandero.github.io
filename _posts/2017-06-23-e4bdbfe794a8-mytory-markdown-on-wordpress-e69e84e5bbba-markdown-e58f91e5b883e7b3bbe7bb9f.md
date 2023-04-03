---
id: 643
title: '使用 Mytory Markdown on WordPress 构建 Markdown 发布系统'
date: '2017-06-23T00:13:13+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/?p=643'
permalink: /2017/06/23/%e4%bd%bf%e7%94%a8-mytory-markdown-on-wordpress-%e6%9e%84%e5%bb%ba-markdown-%e5%8f%91%e5%b8%83%e7%b3%bb%e7%bb%9f/
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170622%20%E4%BD%BF%E7%94%A8%20Mytory%20Markdown%20on%20Wordpress%20%E6%9E%84%E5%BB%BA%20Markdown%20%E5%8F%91%E5%B8%83%E7%B3%BB%E7%BB%9F.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_visits_count:
    - '423'
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170622%20%E4%BD%BF%E7%94%A8%20Mytory%20Markdown%20on%20Wordpress%20%E6%9E%84%E5%BB%BA%20Markdown%20%E5%8F%91%E5%B8%83%E7%B3%BB%E7%BB%9F.md'
categories:
    - Articles
tags:
    - blog
    - Markdown
    - WordPress
---

之前考虑更换 blog 系统，Jekyll on GitHub 方案某些方面堪称完美，但基于各方面的考虑，最终还是选择了 Mytory Markdown on WordPress 方案，记录如下

<!--more-->

## Jekyll on GitHub

依托 GitHub 及其原生支持的静态 blog 系统，在静态 blog 各种优点的基础上还有 GitHub 的强势 buff ，但同时也不可避免的继承静态 blog 和 GitHub 带来的短板，主要特点：

- **文件管理简单** 只需处理 Markdown 文件，相关的修改更新较为方便
- **没有数据库带来的性能瓶颈**
- **但也没有数据库带来的内容管理系统** 这里说的内容管理系统包括文章的分类、标签、状态等内容，这点对于普通用户来还是很重要的，例如 WordPress ，因为有数据库的存在可以通过各类转换工具方便的转换和提取
- **需要服务器搭建特殊环境** Jekyll 可以托管在 GitHub，这个比较特殊，一方面省去了服务器端的要求，比较省心；另一方面，这种公共的内容提供商面对的河蟹措施都够呛，比较闹心
- **渲染需要时间，文件越多处理时间越长** 站点通过渲染 Markdown 文件生成，文章越多展示前的渲染时间越长（未实际体验）
- **站点功能有限，扩展困难**

## Mytory Markdown on WordPress

依托 WordPress 成熟的程序生态，当然主要还是 Mytory Markdown 的强悍功能，MW 方案基本具备 JG 方案的优点，除了部分环节要繁琐一点

### 功能实现

- 首先要把 Markdown 文件推送至 gitHub（这步两者差不多）
- <del>获得文件在 gitHub 中 raw 的链接地址（这步略麻烦）</del>（这步其实还算简单，同一 repo 中的不同文件 raw 路径是基本一致的，网址前缀加上 Markdown 文件完整文件名即可，中文不影响，不需要在 github 中去查询文件 raw 的具体地址）
- 在 WordPress 中新建 blog，设置分类、标签等需要的参数（这步比较麻烦）
- 填入 文件链接地址，发布
- 如果仅止于此，那么 Mytory Markdown 只不过是又一款中规中矩的 Markdown 插件，但实际上……修改 Markdown 文件推送后，刷新你的 blog 页面，没错，WordPress 中的内容自动更新了

### 方案缺点

- **发文略繁琐** 缺点主要就是发布新日志中新建 blog 比较繁琐的步骤了
- **不够省心** 动态 blog 系统虽然各方面都友好得多，但需要服务器支持和一定维护，无法像 JG 方案那么省心

### 方案优点

- **便于写作** 原生 Markdown 支持，静态 blog 的最大亮点
- **便于编辑** 修改 Markdown 文件推送，blog 内容即可同步更新
- **便于管理** WordPress 内容管理系统完备，且可随时向其他 blog 系统转换
- **便于扩展** WordPress 插件生态成熟，方便 blog 扩展功能
- **便于控制版本** GitHub 副产品，静态 blog 的亮点之二

（Mytory markdown 还有一个 for dropbox 版本，支持在 blog 编辑页面读取 dropbox 内 Markdown 文件发布和更新，但不支持访问 blog 页面触发更新，虽然功能稍逊，但因为 dropbox 的强悍版本管理功能，对于不写代码或者不习惯使用 GitHub 的用户也是一个不错的选择）

## Workflowy to Typroa

上面介绍的都是展示端，而输出端个人采用的方案同样是两大神器的组合：

- Workflowy，梳理思路、整理结构化信息的笔记神器
- Typroa，简约、强大、养眼的单窗口 Markdown 编辑神器
  
    而最赞的，**Workflowy export – OPML – Typora import**，一篇无须再排版的原生 Markdown blog 直接出炉

## 趟坑相关

当前方案实现较为理想，但也非一蹴而就，中间历经：

- **各类静态 blog 系统** （Octopress、Hexo、Hugo ），缺点前文已述
- （WordPress 插件） Markdown 类编辑器实现的 **WP-Markdown、PrettyPress**，缺点显而易见
- **邮件远程发文**，仅能发文，功能太少
- **Windows Live Writer 与 Open Live Writer**，发展停滞，原生不支持 Markdown，安装插件困难
- python 程序 **MarkPress**，发文实现相对完美，但无法编辑修改
- python 程序 **PyPoster**，功能描述不错，但是安装之后各种报错，无法使用

记录于此，供有相关需求同学参考