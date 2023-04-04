---
id: 312
title: 什么值得买条目关键字过滤脚本
date: '2015-11-13T13:59:56+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/312'
duoshuo_thread_id:
    - '6275546054746178306'
mytory_md_visits_count:
    - '70'
    - '70'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/15/151113%E4%BB%80%E4%B9%88%E5%80%BC%E5%BE%97%E4%B9%B0%E6%9D%A1%E7%9B%AE%E5%85%B3%E9%94%AE%E5%AD%97%E8%BF%87%E6%BB%A4%E8%84%9A%E6%9C%AC.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/15/151113%E4%BB%80%E4%B9%88%E5%80%BC%E5%BE%97%E4%B9%B0%E6%9D%A1%E7%9B%AE%E5%85%B3%E9%94%AE%E5%AD%97%E8%BF%87%E6%BB%A4%E8%84%9A%E6%9C%AC.md'
dotGood:
    - '1'
categories:
    - Notes
tags:
    - Userscript
---

刚刚过去的双11想必各位值友刷张大妈刷的十分辛苦，但是张大妈本身没有多重筛选功能，从用户角度来说包含了较多无效信息，还好现在有无限可能的浏览器脚本，我们自己来改(山)造(寨）……

<!-- more -->

## 功能

根据设定关键字过滤张大妈页面上标题、标签、站点中包含指定文本的条目（刷新、空格触发）

## 代码

代码山寨自 [P233](https://www.v2ex.com/member/P233) 的 [又一个 V2EX userscript](https://www.v2ex.com/t/173858) ，Tampermonky Chrome 实测正常，自用分享兼抛砖引玉（代码盲，达人多指点）

```
// ==UserScript==
// @name       0 Smzdm Filter
// @namespace
// @version    0.1.2.6
// @description  关键字过滤
// @include      http://www.smzdm.com/jingxuan/*
// ==/UserScript==

// 添加关键字
var block = /关键字填到这|路人甲|宋兵乙/;

var parent1 = '#feed-main-list'
var child11 = '.feed-block-info>span'  // 标签
var child12 = '.feed-block-title>a' // 标题
var child13 = '.feed-block-extras>a' // 站点

// html
$(document).ready(function(){
    $(child11).each(function() {
        var tag = $(this).text();
        if (tag.search(block) >= 0) {
            $(this).parentsUntil(parent1).hide();
        }
    });
    $(child12).each(function() {
        var tag = $(this).text();
        if (tag.search(block) >= 0) {
            $(this).parentsUntil(parent1).hide();
        }
    });
    $(child13).each(function() {
        var tag = $(this).text();
        if (tag.search(block) >= 0) {
            $(this).parentsUntil(parent1).hide();
        }
    });
});

// 滚动
$(document).keypress(function(e) {
    if(e.which == 32) {
        $(child11).each(function() {
            var tag = $(this).text();
            if (tag.search(block) >= 0) {
                $(this).parentsUntil(parent1).hide();
            }
        });
        $(child12).each(function() {
            var tag = $(this).text();
            if (tag.search(block) >= 0) {
                $(this).parentsUntil(parent1).hide();
            }
        });
        $(child13).each(function() {
            var tag = $(this).text();
            if (tag.search(block) >= 0) {
                $(this).parentsUntil(parent1).hide();
            }
        });
    }
});
```