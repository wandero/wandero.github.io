---
id: 122
title: 'Chrome 搜索使用经验'
date: '2012-02-05T18:10:43+08:00'
author: Zephur
layout: post
guid: 'http://dolo.cloudlet.info/?p=97'
permalink: /2012/02/05/chrome%e6%90%9c%e7%b4%a2%e4%bd%bf%e7%94%a8%e7%bb%8f%e9%aa%8c/
duoshuo_thread_id:
    - '6275545969316594434'
mytory_md_visits_count:
    - '193'
categories:
    - Notes
tags:
    - Chrome
---

Chrome 原生搜索已经相当强大，如支持关键字调用相应搜索引擎、划词右键搜索（配合扩展可以拖拽搜索），手动添加页面搜索引擎、自动获取页面搜索引擎等（这个功能优劣见仁见智，不过没找到关闭的方法）。而这里介绍的主要是结合 Chrome 搜索的关键字功能与 Google 的页面搜索功能实现对特定站点的快速搜索，

<!--more-->

**实例**

在 Chrome 地址栏输入 d，空格（常见的 Chrome 介绍中提到的 Tab 键实际上会补完当前提示，没有空格方便）， cloudlet ，回车，即可在 dolo.cloudlet.info 直接搜索 cloudlet

**实现**

其实原理非常简单，就是结合 Google 的页面搜索（site:）和 Chrome 的关键字搜索功能，具体操作上，将`https://www.google.com/search?q=site:[SITE]+%s`填入 Chrome 的搜索引擎中并补充搜索引擎名称和关键字（\[SITE\]替换成目标站点）。

批量处理：excel单元格中C列填入相应的页面地址，D列填入  
`="https://www.google.com/search?hl=zh_cn&q=site:"&C2&"+%s"`，下拉

**小书签**

（这种功能用书签也可以实现 ，在Chrome 中新建地址为

```
javascript:q = "" + (window.getSelection ? window.getSelection() : document.getSelection ? document.getSelection() : document.selection.createRange().text); if (!q) q = prompt(document.domain+’站内搜索:’, ""); if (q!=null) location=("http://www.google.com/search?num=100&q=site:" + escape(location.hostname) + " "" + encodeURIComponent(q.replace(/"/g,"")) + """).replace(/ /g, "+"); void 0

```

的小书签，即可在单击 bookmarklet 后弹出关键字输入窗口从而进行页面搜索。 但这样首先要打开相应的页面。）

**优势**

方便快捷，直接在地址栏上处理，不需要打开相应站点（这个是最重要的）  
适应性广，不少站点的原生搜索使用反而没有 Google 方便或者强大  
定制性高，前面只是以 Google 举例，而实际上基本任何不需要搜索权限的站点都可以使用同样方法定制（例如 Baidu 及针对 Discuz 平台的纵横搜索，当然后者一般都是站点原生搜索，可以直接在 Chrome 上添加）

**扩展**

上述方法主要针对是单一站点情况，如内容或性质相近的站点也可以通过 Google 自定义搜索 <http://www.google.com/cse/> 来自行定制自己的内容搜索引擎（而不仅仅是他自己介绍的那样是自己站点的搜索引擎）。

**其他**

Chrome 默认 Google 搜索会跳转 .hk，解决方法有进去 Chrome 内部 hack 的，最简单的是删掉默认的 Google 搜索，重新添加一个 `http://www.google.com/search?hl=zh_cn&q=%s`

Chrome 新添加的搜索引擎会列在其他搜索引擎窗口内，和自动添加的搜索引擎混在一起比较乱，可以通过设为默认值再取消的方法将其挪到默认搜索栏中。