---
id: 379
title: 'Inoreader @ stylish'
date: '2016-05-26T16:12:44+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/379'
permalink: /2016/05/26/inoreader-stylish/
duoshuo_thread_id:
    - '6288907429044290305'
mytory_md_visits_count:
    - '62'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/160526Inoreader%20%40%20stylish.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/160526Inoreader%20%40%20stylish.md'
categories:
    - Notes
tags:
    - read
    - RSS
---

在和 Feedly 的鏖战中，Inoreader 的界面恐怕是最大的失分项，网上能找到的样式稀少且大多不适用，只好自己动手，东拼西凑的弄出了一个还能用的样式。

<!--more-->

# 说明：

- Inoreader 的左栏宽度是可以自行调整的，在订阅源右侧齿轮-左栏宽度中
- 使用本样式前，请先调整为列表视图
- 本样式会隐藏顶部导航条导致无法全局搜索，不想隐藏顶部导航条可删除相应代码
- 本样式适配 1920 1080 与 1440 900 分辨率，其他分辨率效果不详
- 因为技术原因或者 css 本身的机制问题，Inoreader 弹出消息后版面会出现小问题，关闭样式后关闭消息面板即可  
    # 代码

```

#subscriptions_buttons {display: none !important;}/*不想隐藏顶部导航条请删掉这行代码*/

/*ad*/
.block_article_ad
,.ad_title
,.ad_title_centered
{display: none !important;}

/*nav*/
#sb_rp_upgrade {display: none !important;}

#sb_rp_tools
,#sb_rp_notifications
,#sb_rp_gear
{opacity: 0;}

#sb_rp_tools:hover
,#sb_rp_notifications:hover
,#sb_rp_gear:hover
{opacity: 1;}

/*subscriptions_nav*/
#parent_dashboard
,#parent_channel
,#parent_teams
,#parent_web_pages
{display: none !important;}

/*1440*/
#splitter,
#tree_pane,
#reader_pane
 {height: 666px !important}

/*buttons*/
.icon-new_tab,
.icon-more_horizontal_dots
{opacity: 0}

.icon-star_empty
{opacity: 0;}

.article_stripe {
    opacity: 0 !important;
}

.article_full_contents {
    padding: 2% 8% !important;
    width:720px !important;
}

.article_content {
    font-size: 16px !important;
    text-indent: 2em !important;
    padding: 4%  1% !important;
    line-height:2em !important;
}

.article_sub_title {opacity: 0;}
.article_sub_title:hover {opacity: 0;}

.article_tags {opacity: 0;}
.article_footer {opacity: 0;}

#sinner_container {display: none !important;}

.article_header>.arrow_div {opacity: 0;}

.artcle_header_text
,.article_header_text_read
 {width: 400px !important;}

 .article_short_contents
{opacity: 0 !important;}

img {max-width: 576px !important}

/*link color*/
.bluelink:visited {
  color: #444 !important;
}

.bluelink:link {
  color: #000 !important;
}

.bluelink:visited,.bluelink:link {
    text-decoration: none !important;
    border-bottom: 1px solid #ddd;
}

.bluelink:hover {
    border-bottom: 1px solid #999;
}

.sinner_under_footer {display: none !important;}
```