---
id: 1265
title: 'Inoreader 批量修改订阅源'
date: '2023-01-12T20:35:23+08:00'
author: Zephur
layout: post
guid: 'https://cloudlet.info/?p=1265'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/23/230112%20Inoreader%20%E6%89%B9%E9%87%8F%E4%BF%AE%E6%94%B9%E8%AE%A2%E9%98%85%E6%BA%90.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
categories:
    - 工具二三
tags:
    - RSS
    - Inoreader
excerpt_separator: <!-- more -->
---

- 偏好设置 – 导入、导出和备份 – 导出 – 仅下载 OPML 订阅文件

- 编辑下载的 xml 文件，批量替换需要修改的订阅源（xmlUrl）

- 偏好设置 – 内容 – 删除变化订阅源（如果用量充裕，也可以导入后操作）

- 偏好设置 – 导入、导出和备份 – 导入 – OPML 导入（默认文件夹 保持默认无）

- （导入 修改的 OPML 只会添加变化订阅源）

  <!-- more -->

BTW: rssfeed.today 停止服务了，(感谢 zgq354)。虽然可以自建服务，但怕麻烦还是先蹭下 rsshub.rssforever.com 的免费服务（感谢 rssforever）

RSSHub 目前抓取 Weibo 正常，只是排版会宽度截断不是很自然，图片异常可以使用 Referer Control 针对 Inoreader 页面（或其他需要显示微博图片的页面）自定义 referer 为 `https://weibo.com`