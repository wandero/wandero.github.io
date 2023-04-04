---
id: 1270
title: 'Logseq 清理未使用附件'
date: '2023-01-16T09:52:51+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1270'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/23/230116%20Logseq%20%E6%B8%85%E7%90%86%E6%9C%AA%E4%BD%BF%E7%94%A8%E9%99%84%E4%BB%B6.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
dotGood:
    - '1'
categories:
    - 工具二三
tags:
    - Logseq
excerpt_separator: <!-- more -->
---

## 问题

Logseq 目前删除 block 并不会删除引用的文件（图片），日积月累 assets 文件夹里无效附件非常多


## 解决

目前搜索到的有效方案是 [Frederic 写的一段 pyphon 代码](https://an.admirable.pro/logseq-delete-unused-assets/) ，但这段代码在涉及中文文件时会报错 `UnicodeDecodeError: 'gbk' codec can't decode byte ... illegal multibyte sequence`

<!-- more -->

解决办法是将代码中的 `open(os.path.join(dirname, filename))` 修改为 `open(os.path.join(dirname, filename),encoding="UTF-8")`

## 代码

```python
import os
import shutil

# 指定图谱文件夹
os.chdir('c:\cloudlet.info\log')

assets_dir = './assets'
journal_dir = './journals'
pages_dir = './pages'
to_delete_dir = './to_delete'

if not os.path.exists(to_delete_dir):
    os.makedirs(to_delete_dir)

referenced_files = set()

for dirname in [journal_dir, pages_dir]:
    for filename in os.listdir(dirname):
        if filename.endswith('.md'):
            # 打开 .md 文件
            with open(os.path.join(dirname, filename), encoding="UTF-8") as f:
                # 遍历文件中的每一行
                for line in f:
                    # 遍历 assets 目录中的所有文件
                    for asset in os.listdir(assets_dir):
                        # 如果这一行包含了 assets 目录中的某个文件的名称，则将这个文件的名称加入到 referenced_files 集合中
                        if asset in line:
                            referenced_files.add(asset)

for asset in os.listdir(assets_dir):
    if asset not in referenced_files and not asset.endswith(".edn"):
        print(asset)
        shutil.move(os.path.join(assets_dir, asset), to_delete_dir)

```

（安装 python3 环境后，将代码保存为 check\_asset\_reference.py <del>复制到 logseq 需整理图谱的根文件夹中</del>，使用 cmd <del>在当前文件夹</del>运行 `python3 c:\cloudlet.info\check_asset_reference.py` 即可将无效附件移动至自动建立的 to\_delete 文件夹中）

（代码默认处理 journal\_dir 和 pages\_dir 中文本涉及的 assets\_dir 中的文件，可以结合实际情况修改）

## 其他

- 注意上述代码中的 `encoding="UTF-8"` 若是改为 `encoding="gb18030"` 代码会正常运行但会误删文件
- 有相关的插件 [logseq-plugin-file-manager](https://github.com/haydenull/logseq-plugin-file-manager)，但据说会误删文件未修正
- 有相关的删除未使用图片代码 [qbosen](https://gist.github.com/qbosen)/[backup\_unref\_images.sh](https://gist.github.com/qbosen/dd6d66255cd225e3daa7f3563737a01c)，但只清理图片并不能解决无效附件问题
- 如果是从 Evernote 等其他笔记软件迁移至 Logseq 等情况，会出现其他附件库（如 cloudlet.info），需要先改代码清理 cloudlet.ino 文件夹，之后将 cloudlet.info 文件夹内剩余有效附件剪切至 assets ，再使用 Visual Studio Code 之类软件批量替换相关 journal 和 page 中的路径代码