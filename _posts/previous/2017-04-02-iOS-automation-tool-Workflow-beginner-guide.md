---
id: 441
title: "iOS 流程自动化工具\_Workflow 简易上手指南"
date: '2017-04-02T21:29:49+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/441'
mytory_md_visits_count:
    - '129'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170402iOS%20%E6%B5%81%E7%A8%8B%E8%87%AA%E5%8A%A8%E5%8C%96%E5%B7%A5%E5%85%B7%C2%A0Workflow%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170402iOS%20%E6%B5%81%E7%A8%8B%E8%87%AA%E5%8A%A8%E5%8C%96%E5%B7%A5%E5%85%B7%C2%A0Workflow%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
categories:
    - 工具二三

---

—— 用 Workflow 速记 Evernote 笔记

Workflow 闻名已久，之前的印象：对于手机重度使用者来说，Workflow 算得上神器级的应用，不过对于不喜欢手机操作的同学（比如我）来说，多少有点鸡肋。这次被苹果收购之后免费，Workflow 又被大大安利了一波，上手体验了下，才发现对于不喜欢手机操作的同学，Workflow 一样有不小的使用价值。

<!-- more -->

## 如何上手

网上关于 Workflow 的指南比较多，但是因为 Workflow 有些类似 Autohotkey，各种实例是五花八门华丽至极，不一定有正好符合用户需求的实例，建议在搜索无果的情况下参照类似的或者更复杂的实例的框架了解 Workflow 的大致工作流程，然后自己动手。

推荐 Workflow 官方的实例库（App 主窗口中的 Gallery），几乎涉及了 iOS 的各类原生应用和 Workflow 的各种功能，也方便查看和获取。

## 实例参考

身为 Evernote 的重（中）度（毒）用户，针对 iOS 端还是严重不够顺手的 Evernote，个人的第一个实例自然就是关于 Evernote。最初的设想是 Evernote 的快速记事，在了解了一些 Workflow 的功能后，目前设定了如下实例。

**Evernote 快速记账**

（这个实例效果最赞，如果各类实例都有如此体验，那 Workflow 就是当之无愧的神器了）在 Widget 中点击实例，Workflow 的 Widget 窗口自动改变为数字输入界面，点击数字输入，点击 ok，数字键盘自动收起。（后台）Evernote 的指定笔记内会添加一行包含时间和输入数字的文本，整个操作和实现过程全部在 Workflow 的 Widget 窗口内完成，不切换或弹出其他任何窗口。

代码流程也很简单

- 使用 Ask for input – Set Variable 录入金额
- 使用 Date – Format Date – Set Variable 获取时间
- 使用 Text 接受金额和时间参数
- 通过 Make Rich Text from HTML 格式化
- 通过 Append to Note 导入 Evernote。

实例链接：https://workflow.is/workflows/2c4ad8957ba044fbafb78e031b188cca

## 补充说明

这个实例是针对 Excel 记账的补充，所以只选择了必须的内容输入以保证输入效率（其实是不想在低效的手机端操作），本来还想自动获取地理位置，但发现实现比较麻烦，意义也不是很大就没放弃了。

将快速记账的实例中金额的 Ask for input 的 Input Type 改成 Text 就是另外一个实例快速记事了，这个实例的使用效果就要没那么理想，启动后会进入 Workflow 界面，运行结束后窗口仍然停留在 Workflow 中。

实际体验后发现快速记事可以将 Append to Note 中的 Note Title 也设定为录入内容，这样录入的内容会生成独立的笔记，方便 Evernote 的后续处理，而快速记账则将 Note Title 指定为静态内容而非动态参数，这样多次录入的开支记录均位于一则笔记中。

Workflow 的实例是可以添加到桌面的，在实例窗口的右上角设置中，还可以编辑实例的图标，有些实例放在桌面会更方便。

另外 Workflow 是支持印象笔记的，Evernote 登陆窗口左上角点击可切换 Evernote 和印象笔记的登陆面板。