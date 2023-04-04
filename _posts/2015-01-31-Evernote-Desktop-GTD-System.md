---
id: 284
title: '使用 Evernote 构建桌面 GTD 系统'
date: '2015-01-31T09:52:06+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/284'
duoshuo_thread_id:
    - '6275546041425068802'
v2press_who_bookmarked_me:
    - 'a:1:{i:0;i:333;}'
mytory_md_visits_count:
    - '382'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/15/150131%E4%BD%BF%E7%94%A8%20Evernote%20%E6%9E%84%E5%BB%BA%E6%A1%8C%E9%9D%A2%20GTD%20%E7%B3%BB%E7%BB%9F.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/15/150131%E4%BD%BF%E7%94%A8%20Evernote%20%E6%9E%84%E5%BB%BA%E6%A1%8C%E9%9D%A2%20GTD%20%E7%B3%BB%E7%BB%9F.md'
dotGood:
    - '1'
categories:
    - Evernote
tags:
    - Evernote
    - GTD
---

## **为什么要用 Evernote 来建构 GTD 系统**

- **GTD 系统的性质决定了收集篮越少越好**
- （工作内容基本在电脑上的话）**绝大部分未尽事宜的捕获都可以通过 Evernote 完成**（因为是自定义剪辑，除了任务本身还可以包含足够的相关信息）；
- **Evernote 作为信息管理中枢的强大能力**

<!-- more -->

## **系统设定**

作为信息管理软件的 Evernote 和作为行动管理软件的 GTD 表面上看似乎很难整合在一起，虽然之前也有不少达人做过这方面的尝试，例如 Esor Huang 的《Evernote超效率数字笔记术》（这种结构在前面的 [Evernote 的信息组织结构](http://cloudlet.info/t/279) 提到），以及ET民工和塞壬的 [GTD系列教程3：顶级知识管理工具Evernote的GTD应用详细指南](http://xbeta.info/gtd-evernote.htm)，但实际应用起来却多少有些别扭。究其原因，主要是 Evernote 的内容分类干扰了 GTD 的清单和场景系统。

如 [Getting Things Done 读书笔记](http://cloudlet.info/t/282) 提到的，GTD 系统呈现在软件中的内容主要是清单和场景两种元素，虽然看起来刚好和 Evernote 笔记本、标签系统对应，但在笔记软件中，大家更习惯将笔记本用作内容分类，这样清单系统或者会与内容分类混淆，或者会与场景系统混淆，最后就形成了前面说的别扭情况。

经过各种尝试，个人最后选择将场景系统和内容系统融合，这样可以用标签元素同时体现行动管理和信息管理两方面内容，具体结构如下（注意前面的数字是功能性的而非装饰性的，可以辅助快速选定笔记本和标签。对应的也可以自己设定以字母开头的笔记本和标签使用首字母快速选定）。

> **笔记本** 0.stuff 1.actions 2.project 3.info 4.plan 5.waitting 6.someday 7.material 8.refining 9.archive
> 
> **标签** 1.work 2.office 3.home 4.out 5.ego 6.logo 7.dolo 8.colo 9.live

笔记本系统在 GTD 系统的清单（事宜向）之外增加了 material （素材）refining （提炼）以及 archive （存档） 三个资料向的笔记本。

标签系统结合场景细化与原有的内容分类系统，将工作事宜分为 work（工作） 和 office（其他需要在办公室处理的或者跟工作有关系的事项），常见的 home 和 out 保持不变，将其他的个人事宜根据具体内容和性质细分。

在界面设定方面，选择摘要视图，笔记排序方式选择标签，这样每个清单都会（是的，没法单独设置）自动根据场景标签顺序来呈现任务（这里标签又起到了标示优先级的作用）

## 具体操作

下面从具体的操作来介绍

### **事宜的添加**

1. **Ctrl+N** 新建笔记
2. 输入事宜内容
3. **F2** 自动修改笔记名称
4. **F3** 添加场景标签
5. **F1** 弹出移动至笔记本面板
6. **1** 自动选定 1.actions
7. **Enter** 完成笔记本调整

（操作需要的 ahk 实现详见 [自己动手对 Evernote 进行一些小增强](http://cloudlet.info/t/280)）

### **任务完成**

任务完成后，可以在笔记内添加一个特殊的表示任务完成的自定义标签（见 [Evernote 的信息组织结构](http://cloudlet.info/t/279)），例如我现在用的 cc，之后 **F1-9-Enter** 将其调整至 9.archive 归档，有需要说明的还可以直接在笔记内备注，方便之后的检视回顾（可以通过自定义标签内容便签和 cc）迅速定位）。

### **日程提醒**

目前的 Evernote 自带提醒功能，已经足够一般的日程提醒使用（4.plan）（这点也是 Evernote 能够直接替代专业 GTD 软件的重要原因)，如果觉得原生的提醒功能不够强大，还可以利用 RTM（Remember the Mlik）之类带日程提醒服务的 [同步功能](https://www.rememberthemilk.com/services/evernote/) 来加强。

### **材料的处理**

（稍后阅读的文章可以先扔 Pocket）有用的资料，剪辑后添加自定义标签，添加内容标签（**F3-7-Enter**），移动至对应笔记本 7.material（**F1-7-回车**）

有些时候，我们可能需要对原始材料进行处理（而非仅仅查询），例如将素材提炼总结，这类笔记可以归入8.refining，这个分类实际上并不是必需（可以加特定自定义标签来实现），但是想象一下 7.material 中的笔记不断的流向 8.refinning，应该还是比较有成就感的事情。

### **移动端**

相对桌面端，移动端的界面因为信息量的问题效果会差一些，但一般 actions 清单和 plan 清单任务不多，同时可以利用 Evernote 的自定义搜索保存为快捷方式的功能进行快速筛选（清单场景组合）。虽然没有 RTM 类专业软件的华丽流畅，也基本能够满足使用了。