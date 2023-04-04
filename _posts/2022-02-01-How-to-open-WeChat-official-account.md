---
id: 1094
title: 微信公众号的打开方式
date: '2022-02-01T21:45:49+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1094'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/22/220127%20%E5%BE%AE%E4%BF%A1%E5%85%AC%E4%BC%97%E5%8F%B7%E7%9A%84%E6%89%93%E5%BC%80%E6%96%B9%E5%BC%8F.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - Notes
tags:
    - RSS
    - 微信
---

微信公众号转 RSS 太过折腾，没有稳定靠谱的公开方案。所以——微信 PC 版-设置-通用设置-使用系统默认浏览器打开网页——成为了我的首选/最终方案……效果其实也还行……

只要把应用放到 Chrome 就可以用丰富的扩展提升体验，包括 Stylus 修改界面，Tampermonkey 添加脚本，Autohotkey 便利操作，等等

这里附带一个 ahk

```autohotkey
   #IfWinActive, ahk_class WeChatMainWndForPC
    {
        ;空格键翻页
        {
            $space::
            send {PgDn}
            return
        }

        ;F1键后台打开鼠标指向链接
        {
            $f1::
            click
            sleep 500
            send !{tab}
            return
        }
    }
```