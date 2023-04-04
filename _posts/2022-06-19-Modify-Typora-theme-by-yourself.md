---
id: 1141
title: '自己动手修改 Typora 主题'
date: '2022-06-19T11:06:28+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1141'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/22/220619%20%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E4%BF%AE%E6%94%B9%20Typora%20%E4%B8%BB%E9%A2%98.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - 工具二三
tags:
    - dark
    - typora
---

一入 dark 深似海？……入了深色模式的大坑，发现各种应用主题的适配成为一个头痛的问题，这边才把 Logseq 摆平（话说安利我深色模式的还是 Obsidian……），那边 Typora 的问题就出来了，找了一圈主题各种不满意，自己写吧姿势水平又不够，还是老办法，找个模板改改

找的过程仔细看了下 Typora 的官网，才发现开发者高瞻远瞩，早就把我们这类眼高手低的补丁控安排的明明白白

<!-- more -->

## base.user.css

先在 theme 文件夹里新建一个 base.user.css，里面的规则会对所有 theme 生效（懒但又爱折腾用户福音），这里可以放一些通用规则，例如字体风格和字体大小、标题样式之类

```css
        body {
        font-family:"xhei believe";
        font-size: 22px;
        line-height: 2;
        }

        #write{
        max-width: 900px;
            margin: 0 auto;
            padding: 20px 30px 40px 30px;
            padding-top: 20px;
        }

        h1,h2,h3,h4,h5,h6 {line-height: 2.2;}

        h1 {font-size: 1.6em; font-weight: 900;margin: 1.8em 0 1em;}
        h2 {font-size: 1.4em; font-weight: 500;margin: 1.8em 0 0;}
        h3 {font-size: 1.2em; font-weight: 500;margin: 1.8em 0 0;}
        h4 {font-size: 1.1em; font-weight: 400;margin: 1.8em 0 0;}
```

## night.user.css

接着再在 theme 文件夹里新建一个 night.user.css（night 是需要打补丁的 css 名称，反正都是要改，所以选择更稳定的默认主题），这里放一些针对 ngiht 的特殊规则，例如颜色、颜色还有颜色什么的……具体操作和 [自己动手修改 Logseq 主题](https://cloudlet.info/t/1135)类似，复制需要覆盖的代码，修改保存收工

```css
:root {
    --bg-color:  #0D1117;
    --side-bar-bg-color: #171C23;
    --text-color: rgb(235, 235, 235) !important;

    --select-text-bg-color:#4a89dc;

    --item-hover-bg-color: #0a0d16;
    --control-text-color: #b7b7b7;
    --control-text-hover-color: #eee;
    --window-border: 1px solid #555;

    --active-file-bg-color: rgb(34, 34, 34);
    --active-file-border-color: #8d8df0;

    --primary-color: #a3d5fe;

    --active-file-text-color: white;
    --item-hover-bg-color: #70717d;
    --item-hover-text-color: white;
    --primary-color: #6dc1e7;

    --rawblock-edit-panel-bd: #333;

    --search-select-bg-color: #428bca;
}

html,
body,
button,
input,
select,
textarea,
div.code-tooltip-content {
    color: var(--text-color);
    border-color: transparent;
}

pre.md-fences {background: #171C23;}
```

## 其他

Typora 的调试和 Logseq 有些区别，一方面软件本身可以呼出开发者工具（需要先在 偏好设置 通用 高级设置 中开启调试模式，再在正文中右键检查元素）更方便，一方面 css 的修改不是实时更新需要重启软件，但总的来说大同小异  
顺便，Win10 碍眼的标题栏又要立功了，在偏好设置 外观 窗口样式 中选择一体化就可以眼不见为净了  
至此，一款个人深度定制的 Logseq 同款 Typora 就出炉了