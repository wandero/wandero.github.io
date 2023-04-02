---
id: 237
title: 'Diablo3 AutoHotkey 脚本'
date: '2014-06-18T21:15:25+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/237'
permalink: /2014/06/18/diablo3-autohotkey-%e8%84%9a%e6%9c%ac/
duoshuo_thread_id:
    - '6275546027646780162'
mytory_md_visits_count:
    - '37'
    - '37'
categories:
    - Games
tags:
    - ahk
    - diablo
---

尽管有所改进，但 D3 仍和 D2 一样是一款凶残的鼠标杀手，为自己的右手着想，就不得不上AutoHotkey 这种虽然有一定风险，但可以减少大量操作的神器了

（郑重提醒，对于玻璃渣反外挂模块，AutoHotkey 这种带有颜色识别内存读取等功能的软件绝对属于外挂无误，虽然按键脚本并不涉及这一块，但风险还是不小的）

## 脚本功能

按一次{`}键触发按下鼠标右键功能，再按一次停止  
按一次{F1}键触发间隔（0.5s左右）点击鼠标左键功能，再按一次停止  
按一次{F4}挂起脚本，暂停所有功能，再按一次恢复

## 脚本代码

```
#IfWinActive, ahk_class D3 Main Window Class

cnt=0

$`::
cnt+=1
if(mod(cnt,2)=1) {
    click down right
}
if(mod(cnt,2)=0) {
    click up right
}
return

Random,time,523,557

$f1::SetTimer, Operation, % State :=  State = "On" ? "Off" : "On"
Operation:
click
Sleep,%time%
Return

$f4::
pause
return

```

## 按键设置

- 物品栏视窗 需要频繁换装备，可以设为C
- 技能视窗 需要频繁切节能，默认S
- 站在原地攻击 对于都用了 ahk 的懒人，默认 shift 够了
- 强制移动 对于这款左键承担了太多功能以至于最好用强制移动代替鼠标左键点击进行移动的游戏，此键非宽大的空格键莫属