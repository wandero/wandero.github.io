---
id: 64
title: WOW多开小结
date: '2012-10-03T19:54:13+08:00'
author: Zephur
layout: post
guid: 'http://foro.cloudlet.info/t/64'
duoshuo_thread_id:
    - '6275545947904672514'
mytory_md_visits_count:
    - '36'
    - '36'
dotGood:
    - '13'
categories:
    - Games
tags:
    - wow
---

# wow多开小结

## 1.原理

通过keyclone传递按键动作，通过jamba、宏及按键设置解决其他事件同步

<!-- more -->

## 2.KeyClone

这是一款为wow定制的按键动作同步软件。

setup-general  
勾选auto add window titled，其后内容改为“魔兽世界”

do-not-pass

这里是设置忽略按键的，但从wow具体情况看，勾选whitelist用白名单来设置反而更方便。

选中直接输入加入白名单的按键

个人设置为1-0，shift+x（坐骑），F1-F8（宏和动作按键，后述）

设定好keyclone之后，两角色的键盘动作就会基本同步，但要进行实际游戏还有不少的工作，具体来说，跟随和攻击通过宏来实现，拾取和交接任务通过按键动作来实现，任务分享和监控等通过jamba来实现

注：KeyClone 的功能很容易用 Autohotkey 实现，并非多开必备

## 3.jamba

这是一款为多开定制的wow插件。功能比较丰富，这里用到的主要是半自动任务交接、自动任务分享、跟随监控等，其他的作用不大，可以自行在设置中关掉。

\*：在core：team里设定好主号和小号（主号和小号均需设置）后，主号的jamba设定都可以通过push setting传递给小号

具体设置见[Jamba 简明设置指南](http://cloudlet.info/t/174)

## 4.宏

战斗宏

`/assist \[主号\]

/castsequence \[法术序列\]

/follow \[主号\]`

战斗宏实现攻击和跟随功能，可置于动作条1-4，从而通过keyclone实现小号协助主号攻击并在战斗结束后继续跟随

目标的目标宏

`/target \[主号\]  
/target targettarget

目标的目标宏作用是选取任务npc，可设定为小号的F2

## 5.按键设置

在键盘设置中有两个按键功能：上一个敌对目标、与目标互动，可分别设置为小号的F3、F4

## 6.完工

完成以上设定，基本就能实现较为流畅的双开操作了

主号接任务，小号会通过jamba自动分享  
shift+x召唤坐骑，1-4攻击目标，主号拾取后再按F3、F4操作小号loot（当前版本5.05拾取机制已改成任务掉落见者有份了）  
交任务时，主号选定npc，小号F2选定目标，F4接近目标（界面-鼠标-点击移动需勾选）,F4打开任务交接界面，之后主号的任务奖励和交接动作会通过jamba同步给小号

## 7.BTW

最后，再加上好友招募……