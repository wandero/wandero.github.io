---
id: 1018
title: 'Chrome 配置同步 2019'
date: '2019-01-31T18:05:08+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1018'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/19/190131%20Chrome%20%E9%85%8D%E7%BD%AE%E5%90%8C%E6%AD%A5%202019.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - 工具二三
tags:
    - Chrome
    - Sync
---

没错，又是 Chomre 的配置同步问题……

目前我使用 Chrome 需要同步的文件夹有 `User DataDefault` 中的 Databases、IndexedDB、Local Storage、Local Extension Settings 四个文件夹（似乎还有一个 Sync Extension Settings ，但没同步未见异常），主要是 Tampermonky、Stylus 和 OneTab 等扩展。之前都是用坚果云同步，但似乎是因为 Chrome 机制的变化，免费版的坚果云流量扛不住了……于是将 Local Storage、Local Extension Settings 改为 Dropbox 同步。

<!-- more -->

这里再提一下 Dropbox 和坚果云的同步机制，之前帖子的说法有误，坚果云原生支持多文件夹同步，但是该功能要求该同步文件夹的名称不能超过 30 个字符。而两者都支持目录和文件的符号链接（mklink），此处没有文件名长度之类的限制，只有坚果云有一个文件路径长度不能超过 255 个字符的限制，但一般情况是达不到这个长度的。

需要注意的是，符号链接的时候需要将源文件剪切至 Dropbox 和 坚果云的主文件夹内，再通过 mklink 将符号链接置于 Chrome 的配置文件夹内，这样才能正确同步，反过来是无法生效的。

具体语法上，文件是 `mklink 「链接地址」 「源文件地址」`，目录是 `mklink /D「链接地址」「源目录地址」`。

针对上文遇到的情况，在 Dropbox 同步（代理）速度有限时，Databases、IndexedDB（也可以加上 Sync Extension Settings ）这类体积和变化较小的文件夹，可以通过坚果云「新建同步文件夹」来同步。在坚果云流量不够时，Local Storage、Local Extension Settings 可以建立符号链接通过 Dropbox 来同步。该方案可能碰到的问题是 Chrome 隔几天就需要重新登录（目前没有发现解决办法）

参考代码如下，类似代码还可以保存为批处理文件（bat），需要的时候直接运行。注意先将配置文件中的文件夹剪切至 Dropbox 中。

```bat
mklink /D "C:Program FilescentbrowserUser DataDefaultLocal Storage" "d:DropboxmklinkLocal Storage"

mklink /D "C:Program FilescentbrowserUser DataDefaultLocal Extension Settings" "d:DropboxmklinkLocal Extension Settings"
```

如果需要同步的扩展很少，可以通过扩展的标识符搜索相关的配置文件夹，针对单个扩展的配置文件直接建立符号链接，这样同步效率最高，但目前来看，Tampermonkey 和 Stylus 这两个无法避开的扩展就涉及到前面提的大部分文件夹，单独操作太过麻烦。