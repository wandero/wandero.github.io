---
layout: post
title: "Jekyll 快速生成新文章模板 "
date: 2023-04-28 21:00:00 +0800
categories: 工具二三
tags:
    - Jekyll
    - AHK
---



继续暴殄天物，大佬用 ChatGPT 改变世界，我用 ChatGPT 偷懒？……

上回说到 Jekyll 快捷发布，那是码完字之后的事情，那么码完字之前建立文件填写 YAML 的各种繁琐操作能不能依此类推呢？

ChatGPT：Of course

## 功能

直接运行脚本（不是热键触发，可以建立快捷方式然后 Win+R 调用），弹出输入框，依次输入 blog 标题、分类、标签（支持逗号分隔）、slug，脚本会在指定目录生成新文档并自动打开

顺便，ChatGPT 在写代码方面容易卡住，这段代码第二行的 ` % A_Now - 1000000` 它原本生成的是 `% A_Now - 86400` ，无法实现效果，但是它自己又检查不出来，如果只是将报错提交给它让它自己改，基本会进入死循环，并且越改越错。试验了下感觉可以让它保持其他部分不变来避免这种情况，但也可能是 Autohotkey 它不太熟，死循环的概率似乎大于其他语言

## 代码

```AHK
; 生成昨天日期，格式为：yyyy-mm-dd
FormatTime, yesterdaysDate, % A_Now - 1000000, yyyy-MM-dd
yesterdaysDate .= " 21:00:00 +0800"

; 弹出输入框，让用户输入标题、分类和标签
InputBox, postTitle, Blog Post, Enter the post title:, , 418,120
InputBox, postCategories, Blog Post, Enter the post categories:, , 418,120
InputBox, postTags, Blog Post, Enter the post tags (comma-separated):, , 418,120
InputBox, postSlug, Blog Post, Enter the post slug, , 418,120

; 转换标签为适当的格式
tagsArray := StrSplit(postTags, ",")
tagList := ""
Loop, % tagsArray.MaxIndex()
{
	tagList .= "`n    - " . Trim(tagsArray[A_Index])
}

; 创建文件内容
fileContent =
(
---
layout: post
title: "%postTitle%"
date: %yesterdaysDate%
categories: %postCategories%
tags:%tagList%
---
)

; 生成文件名（在路径 c:\cloudlet.info\ 下）
FormatTime, fileName, % A_Now - 1000000, yyyy-MM-dd
fileName := "c:\cloudlet.info\" . fileName . "-" . StrReplace(postSlug, " ", "-") . ".md"

; 将文件内容写入文件
FileAppend, %fileContent%, %fileName%,UTF-8

; 打开新创建的文件
Run, %fileName%
```

