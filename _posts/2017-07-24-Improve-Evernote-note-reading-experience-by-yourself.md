---
id: 767
title: '自己动手改善 Evernote 笔记阅读体验'
date: '2017-07-24T14:01:11+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/?p=767'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/17/170724%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E6%94%B9%E5%96%84%20Evernote%20%E7%AC%94%E8%AE%B0%E9%98%85%E8%AF%BB%E4%BD%93%E9%AA%8C.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_visits_count:
    - '288'
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/17/170724%E8%87%AA%E5%B7%B1%E5%8A%A8%E6%89%8B%E6%94%B9%E5%96%84%20Evernote%20%E7%AC%94%E8%AE%B0%E9%98%85%E8%AF%BB%E4%BD%93%E9%AA%8C.md'
categories:
    - 工具一二
tags:
    - 工具一二
---

## 背景

Evernote 桌面端在拥有同类软件中最优异的剪辑功能的同时，也具备足够糟糕的阅读体验，长文尤其如此（几乎无法设定的更加糟糕的演示功能也挽救不了它）。针对笔记内容单独排版虽然能够带来一定改善，但费时费力且效果有限。

那么，是否存在一种一劳永逸、一经设置、永久生效的方法来改善 Evernote 的阅读体验，改变其灾难的笔记字体、大小、颜色、行距、留白、背景等等等等呢，请看下文

<!-- more -->

## 思路

- 选择目标笔记，通过「复制笔记本内部链接」功能获取笔记 URL
- 使用浏览器打开笔记，（Evernote 会自动弹出），切换回浏览器窗口
- 通过 Stylus（Stylish 类扩展）定制笔记页面
- 上述键鼠操作部分通过 AutoHotKey 脚本一键完成

## 代码

抛砖引玉

### ENview AHK

```ahk
;ENview AHK  r0.0.1
;在 Evernote 笔记列表选中目标笔记（或位于目标笔记内容面板）时按 F12 即可

SetTitleMatchMode Regex
#IfWinActive ahk_class (ENSingleNoteView|ENMainFrame)
{
    $f12:: ;激活热键 F12，可自行替换
    send {Escape}
    Sleep, 100
    send {AppsKey}
    Sleep, 100
    send l
    Sleep, 100
    Run, %Clipboard%
    Sleep, 500
    WinWaitActive ahk_class (ENSingleNoteView|ENMainFrame)
    Sleep, 500
    send !{tab}
    return
}
```

### ENview Stylus

```css
/* ENview Stylus  r0.0.1 */
.logo-bar.public-layout,
.footer.note-footer,
.footer.wrapper,
#message-container {
    display: none !important
}
body {
    background: url('') center !important;
}
#container.wrapper {
    box-shadow: 0 0 0 #fff !important
}
.note-content a,.note-content abbr,.note-content acronym,.note-content address,.note-content area,.note-content b,.note-content bdo,.note-content big,.note-content blockquote,.note-content caption,.note-content center,.note-content cite,.note-content code,.note-content col,.note-content colgroup,.note-content dd,.note-content del,.note-content dfn,.note-content div,.note-content dl,.note-content dt,.note-content em,.note-content font,.note-content h3,.note-content h4,.note-content h5,.note-content h6,.note-content hr,.note-content i,.note-content ins,.note-content kbd,.note-content li,.note-content map,.note-content ol,.note-content p,.note-content pre,.note-content q,.note-content s,.note-content samp,.note-content small,.note-content span,.note-content strike,.note-content strong,.note-content sub,.note-content sup,.note-content table,.note-content tbody,.note-content td,.note-content tfoot,.note-content th,.note-content thead,.note-content tr,.note-content tt,.note-content u,.note-content ul {
    line-height: 2.2em !important
}
.note-content {
    font-size: 18px;
    line-height: 2.2;
    color: #4a4a4a;
}
.ennote > p {
    margin: 20px 0px !important
}
.vtop,
.image-gallery-button {
    opacity: 0.2
}
.note-title {
    color: #444;
    font-weight: 700;
    width: 100%;
    margin-top: 15px
}
```

## 说明

通常来说，能受 Mactpye（Windows） 和各种扩展加持的现代浏览器本身能提供各类软件中最理想的阅读体验，而依托各类扩展和脚本（Stylus、Tampermonkey），用户几乎可以任何形式定制站点内容，思路很简单，但处理后，终于能舒服的阅读长笔记了。

注意，鼠标点击笔记正文面板后可能出现空格键和鼠标手势失效的情况，点击左右两侧空白即可解决