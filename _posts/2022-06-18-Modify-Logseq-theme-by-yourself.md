---
id: 1135
title: '自己动手修改 Logseq 主题'
date: '2022-06-18T11:03:14+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1135'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/22/220618%20%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E4%BF%AE%E6%94%B9%20Logseq%20%E4%B8%BB%E9%A2%98.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '3'
categories:
    - Notes
tags:
    - dark
    - Logseq
---

首先当然是先找一份能接受的主题作为修改基础了，其实和 stylus 定制网页思路一样，主要是隐藏元素和修改颜色等样式，使用简单的 css 就可以实现不错的效果。

Logseq 的主题通常作为插件安装在 `%HOMEPATH%.logseq\plugins\` 中，虽然可以直接修改主题的 custom.css ，但这样不利于维护，最好使用 `%grap%\logseq\custom.css` 覆盖原主题样式（以下操作以我目前使用的 logseq-dev-theme 为例）。

<!-- more -->

## 隐藏元素

隐藏元素永远是最便捷有效的提升页面效果的方法

```
          .cp__sidebar-help-btn /*右下角帮助按钮*/
          ,.new-page /*左下角新建页面按钮*/
          ,.cp__header /*左上角工具条*/
          ,.cp__right-sidebar-topbar /*右上角工具条*/
          {opacity:0}
```

如果觉得这样不方便，加上

```
          .cp__sidebar-help-btn:hover /*右下角帮助按钮*/
          ,.new-page:hover /*左下角新建页面按钮*/
          ,.cp__header:hover /*左上角工具条*/
          ,.cp__right-sidebar-topbar:hover /*右上角工具条*/
          {opacity:1}
```

这样元素在鼠标悬停时会显示

## 调整字体

字体是影响主题的重要元素，特别是通常很少有针对中文显示优化的主题，将 `%HOMEPATH%.logseq\plugins\logseq-dev-theme\custom.css` 中的该部分代码复制到 `%grap%\logseq\custom.css` 中并修改

```
          :root {
            --ct-text-size: 16px; /*基础字体大小*/
            --ct-line-height: 1.6; /*基础行间距*/
            --ls-font-family: "xhei believe" !important;  /*基础字体*/
            --ct-page-title-font-family: var(--ls-font-family); /*均设置为基础字体*/
            --ct-code-font-family: var(--ls-font-family); /*均设置为基础字体*/
          }

          #main-content-container {
            font-size: 1.3em; /*正文部分字体大小*/
            /* text-shadow: 0.5px 0.5px 0.5px #999; */ /*明亮模式下字体加粗，深色模式下无必要*/
          }

          h1 {font-size: 26px !important;font-weight: 600 !important;}  /*缩小 h1 字体*/
```

## 调整颜色

接下来就是同样甚至更加重要的颜色调整了

```
          .dark-theme,
          html[data-theme=dark] {
            --ct-primary-color: #a3cef1;
            --ct-secondary-color: #6096ba;
            --ct-warning-color: #ff7262;
            --ct-success-color: #0dcf82;
            --ct-highlight-color: #ffc600;
            --ls-primary-background-color: #0D1117 !important;   /* #272c35 */
            --ls-secondary-background-color: #171C23;   /*#171C23 #161b22  #313942; left bar*/
            --ls-tertiary-background-color: #161B21; /* #38434c;Link Reference */
            --ls-quaternary-background-color: hsl(215, 21%, 23%);     /* #404b55; Journals selected */

            --ls-border-color: var(--ls-tertiary-background-color);
            --ls-table-tr-even-background-color: var(--ls-secondary-background-color);
            --ls-primary-text-color: rgb(235, 235, 235);
            --ls-secondary-text-color: rgb(200, 200, 200);
            --ct-bold-color: #fff;
            --ls-link-text-color: var(--ct-primary-color);
            --ls-link-ref-text-color: var(--ct-primary-color);
            --ls-link-ref-text-hover-color: var(--ct-secondary-color);
            --ls-active-primary-color: var(--ct-primary-color);
            --ls-active-secondary-color: var(--ct-secondary-color);
            --ls-external-link-color: var(--ct-secondary-color);
            --ls-guideline-color: var(--ls-tertiary-background-color);
            --ls-block-bullet-color: var(--ls-tertiary-background-color);
            --ls-bullet-closed-color: var(--ls-secondary-text-color);
            --ls-block-bullet-border-color: var(--ls-quaternary-background-color);
            --ct-block-arrow-color: rgb(165, 165, 165);
            --ct-page-reference-color: var(--ls-active-primary-color);
            --ls-icon-color: var(--ls-primary-text-color);
            --ct-block-reference-background: rgba(16, 107, 163, 0.2);
            --ct-block-reference-background-hover: rgba(16, 107, 163, 0.3);
            --ls-page-properties-background-color: var(--ls-tertiary-background-color);
            --ls-scrollbar-foreground-color: var(--ls-secondary-background-color);
            /* Will be used if backdrop-filter not supported */
            --ct-header-bg-color: #272c35ee;
            --ls-selection-color: #000;
          }

          .ls-block:not(:focus-within) .bullet {
            background-color: var(--ls-quaternary-background-color);
          }
```

这里可能就会出现一些问题，不同的主题元素命名各异，怎么知道需要修改哪些内容呢？

最简单粗暴的方法是边改边看效果，Logseq 对 custom.css 的修改几乎是实时更新的，保存 custom.css 后一两秒钟就可以看到变化，直接使用显眼的颜色替换原来的颜色就可以很快清楚大部分需要调整的颜色代码位置了）

复杂一点的方法是使用 Web 端的开发者工具，<del>（Logseq 桌面端也有同名工具，但好像没有办法呼出开发者工具面板），这里就要提到 Logseq 特殊的 Web 机制了，在 Web 端 设置 – 常规 – 自定义主题 – 编辑 custom.css 将桌面端使用的主题 css 复制过去（先复制主题 css，再补充 `%grap%\logseq\custom.css`，即可实现与桌面端几乎一致的界面，</del>（alt 激活工具栏，View Toggle Developer Tools） ，接下来哪里不顺眼改哪里了



## 标题栏

Win10 的标题栏也是深色模式的一大障碍，好在仅仅针对 Logseq 的话还要办法补救，个性化 – 颜色：选择颜色：深色、 自定义颜色 – 更多，填入 Logseq 的主背景色（例如我这里的`--ls-primary-background-color: #0D1117`），勾选颜色面板底部的「标题栏和任务窗口」，浑然一体的 Logseq 深色界面完成

可以收工了吗？如果使用微软拼音的话还有最后一步看上去完全不沾边的问题要处理，打开微软拼音选项 – 常规 – 兼容性 – 使用以前版本的微软拼音输入法，勾选开，这样可以关掉深色模式时存在严重 bug （首选字词不不反转颜色）的当前版本微软拼音，开启无此 bug 的老版本（顺便，一版微软的 bug 请不要报有会有人修复的打算）