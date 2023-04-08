---
  layout: post
  title:  "Readwise Reader 使用体验"
  date:   2023-04-07 21:01:00 +0800
  categories: 工具二三
  tags:
    - Reading
---

作为一款月费8美刀的阅读器，Readwise Reader 不能说便宜，特别是简陋的 RSS 订阅功能、糟糕的中文支持、莫名其妙的 Readwise 本体……当然能接受这些以后，Readwise Reader 还是相当让人惊艳的

<!-- more -->

## 吊打竞品的阅读体验

Readwise Reader 阅读体验非常优秀，界面养眼，创造性的段落切换和段落标记功能极大的改善了阅读翻页和笔记体验，而云端同步进一步扩展了服务的实用性。网页内容的抓取和标注功能也做得中规中矩（Simpread，你看看人家）

## 简陋寒碜的 RSS 阅读功能

至少在目前，Readwise Reader 的 RSS 阅读体验是远逊于 Inoreader （的免费版！！），订阅源组织、视图呈现、功能集成等都几乎没法使用，这方面唯一的优点可能还是在内容标记上

## 糟糕的中文支持

这个问题似乎存在很久了，不过看官方的架势也是放弃治疗了，中文支持不利最严重的结果是瞎算中文材料阅读时间，甚至导致材料的组织布局变化……

## 谜之 Readwise 本体

似乎是谜之自信的 Readwise 开发者使用了一种谜之间隔重复逻辑，导致的结果是习惯了 Supermemo 逻辑的我觉得 Readwise 完全没法用（一直在重复固定的卡片），本来 Readwise 可以结合 Readwise Reader 标记功能实现完美的阅读记忆消化回路。这个谜之操作让 Readwise 直接残废，还好还有一些抢救手段，可以通过插件将 Readwise 连接至 Logseq 等笔记软件，日常同步标注，再用 Logseq 的 Flashcard 系统来处理 Readwise Reader 的笔记。

## 延伸玩法

Readwise Reader 是基于 web 的，可以方便的集成各种服务

- Edge 的大声朗读，接近完美的听读体验，不过 Edge 不怎么好用也不支持 Mactype，所以我一般听读时同时开两个浏览器，还可以写段 AHK，方便按 Tab 暂停朗读

  ```
  #IfWinActive, Readwise
  {
  $tab::
      WinActivate, Microsoft​ Edge
      ControlSend, ,{CtrlDown}{ShiftDown}u{shiftup}{CtrlUp}, Microsoft​ Edge
      WinActivate,Cent Browser
  return
  }
  ```

- 沉浸式翻译（Chrome 扩展），英文再烂也不慌了，不过因为技术实现的原因，开了沉浸式翻译以后标注功能会有点小问题

## 样式修改

惯例要放上 Stylus 的样式修改 css，进一步净化页面

```
[class^="_trialMessageContainer"]
,[class^="_progressBarContainer"]
{display:none}

[class^="_inboxNav"]
,[class^="_bottomNav"]
,[class^="_docHeaderContent"]
,[class^="_returnToReadingButton"]
{opacity:0 !important}

[class^="_inboxNav"]:hover
,[class^="_bottomNav"]:hover
,[class^="_docHeaderContent"]:hover
,[class^="_returnToReadingButton"]:hover
{opacity:1 !important}

.theme--dark {
    --reading-editable-font-family: "Source Sans VF", sans-serif;
    --reading-editable-font-size: 18;
    --reading-editable-line-height: 32;

    /*   648   */   
    --reading-editable-line-length: 848px !important;
}
```

## 其他

BUG 体积较大的 epub 上传后可能会消失

最后放上邀请链接 [https://readwise.io/i/wandero](https://readwise.io/i/wandero)，链接注册可以获得额外一个月免费试用

