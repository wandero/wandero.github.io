---
layout: post
title: "Logseq 快速剪辑截图"
date: 2023-05-02 21:00:00 +0800
categories: 工具二三
tags:
    - Logseq
---

严格来说，是使用 Autohotkey 写脚本，调用 IrfanView 的功能（需要先安装 IrfanView），将 Snipaste 的截图一键复制到 Logseq 的 assets 文件夹并且在 Journals 中写入图片路径，从而平替常规笔记软件热键截图的功能，当然，还是在 Chatgpt 的指导下完成……

实现效果：热键触发 Snipaste 截图（框选范围，然后双击结束），这个时候截取的图片会自动进入剪贴板（Snipaste 设置后还可以自动保存）。热键触发脚本，该截图会同时保存到 Logseq 的 assets 中，并且会自动显示在 Journals 里（这些都还是在后台完成的，不影响当前工作）

<!-- more -->

```AHK
#NoEnv
#SingleInstance Force
SendMode Input
SetWorkingDir %A_ScriptDir%

#e::
    ; Check if clipboard contains an image
    if !DllCall("IsClipboardFormatAvailable", "UInt", 2) ; CF_BITMAP = 2
        return

    ; Save image with timestamp
    FormatTime, imgName, A_Now, yyMMddHHmmss
    imgPath := "C:\\cloudlet.info\\assets\\snp" . imgName . ".png"

    ; Save clipboard image using IrfanView
    RunWait, "C:\O\IrfanView\i_view64.exe" /clippaste /convert=%imgPath%

    ; Create image reference in Markdown format
    imgRef := "![" . "snp" . imgName . ".png](../assets/snp" . imgName . ".png)"

    ; Append image reference to the Markdown file
    FormatTime, fileName, A_Now, yyyy_MM_dd
    journalsPath := "C:\\cloudlet.info\\journals\\" . fileName . ".md"
    FileAppend, `n%imgRef%`n, %journalsPath%

return

```

