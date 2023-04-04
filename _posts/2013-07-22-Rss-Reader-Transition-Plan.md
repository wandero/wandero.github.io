---
id: 188
title: 'Rss Reader 过渡方案'
date: '2013-07-22T11:09:40+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/188'
duoshuo_thread_id:
    - '6275546007103079170'
mytory_md_visits_count:
    - '47'
categories:
    - Notes
tags:
    - read
    - RSS
---

Greader 倒下之后，各色 Rss 阅读器如雨后春笋纷纷冒泡，但多少都有不足，经过一段时间的折腾，暂时使用 Feedly（Web 端） &amp; Reeder （移动端） &amp; Local Rss Reader for Chrome （补充）组合过渡。

<!-- more -->

## Feedly（Web 端）

Greader 之后相对靠谱的继承者，拥有比较完善的平台解决方案，相对成熟的功能界面等等。但对于墙内用户，Web 端访问困难，移动端无法使用；另外没有搜索和存档服务长远来看也是一个巨大的缺陷。

没有平台需求的用户也可以尝试 The old Reader（来历不明） 、Inoreader（服务器够呛）和 Digger reader (非常奇葩的无法筛选未读条目）

## Reeder （移动端）

Reeder 就不用多介绍了，值得一提的是在墙内还能完美支持 Feedly ，自身支持本地 Rss 源，移动端的当然选择。

## Local Rss Reader （补充）

可能还是因为墙的原因，目前各种国外服务都无法抓取某些 Rss 源，这个时候就需要一个本地服务来处理，虽然软件方面有曾经经典的 FeedDemon 和 Greatnews，但因其发展早已停滞（坑爹的 Google），UI和操作实在够呛。而这款 Local Rss Reader （Chrome）和已故的 Greader同学（变身小清新装嫩之前）长得一模一样，快捷键也完全相同，就是非常理想的选择了。

怀旧控可以直接使用，风格控可以也可以使用Greader老界面时代的各种Stylish 风格 hack。个人使用的 Pure Reader （默认修改后会有些错位，但阅读体验还是不错）。

- - - - - -

**Feedly 风格修改（Stylish）**

```
.entryBody {
    color: #444444;
    font-size: 18px !important;
    line-height: 2 !important;
    max-width: 960px !important;
}

.u100entry {
    max-width: 960px !important;
    margin-left: auto;
    margin-right: auto;
}

div[style="opacity:0.65"] {
    display: none !important;
}

```

**Local Rss Reader 风格修改**

在`%User Data%\Default\Extensions\cemddjmmnfebpkpkonmbkdmakilpkcid\0.1.8_0\reader\ui\en-scroll.css`末尾添加 Pure Reader 的Stylish代码，保存刷新即可。