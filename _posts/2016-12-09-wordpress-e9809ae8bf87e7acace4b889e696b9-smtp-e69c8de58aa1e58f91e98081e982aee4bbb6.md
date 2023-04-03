---
id: 412
title: 'WordPress 通过第三方 smtp 服务发送邮件'
date: '2016-12-09T14:32:48+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/412'
permalink: /2016/12/09/wordpress-%e9%80%9a%e8%bf%87%e7%ac%ac%e4%b8%89%e6%96%b9-smtp-%e6%9c%8d%e5%8a%a1%e5%8f%91%e9%80%81%e9%82%ae%e4%bb%b6/
duoshuo_thread_id:
    - '6361985458628461314'
mytory_md_visits_count:
    - '63'
    - '63'
    - '63'
mytory_md_path:
    - 'https://github.com/wandero/blog/raw/master/16/161209WordPress%20%E9%80%9A%E8%BF%87%E7%AC%AC%E4%B8%89%E6%96%B9%20smtp%20%E6%9C%8D%E5%8A%A1%E5%8F%91%E9%80%81%E9%82%AE%E4%BB%B6.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://github.com/wandero/blog/raw/master/161209WordPress%20%E9%80%9A%E8%BF%87%E7%AC%AC%E4%B8%89%E6%96%B9%20smtp%20%E6%9C%8D%E5%8A%A1%E5%8F%91%E9%80%81%E9%82%AE%E4%BB%B6.md'
categories:
    - Notes
tags:
    - WordPress
---

最近碰到 500 问题才发现定期数据库备份的邮件断了大半年了，试了网上说的比较多的 phpinfo 和 mail.php 检测方法似乎 mail() 功能正常，再问主机商……果然禁掉了邮件功能……最后选了 **WP-Mail-SMTP** 插件来解决问题，记录如下：

<!-- more -->

- **SMTP Host**：smtp.gmail.com（通过 Google 的 smtp 服务）
- **SMTP Port**：465（注意 587 测试失败）
- **Encryption**：Use SSL encryption （这里开始以为 ssl 需要服务器支持，实际不需要）
- **Authentication**：Yes: Use SMTP authentication.（不验证选择情况不详……）
- Username、Password：为了安全起见，使用的独立的邮箱

设置完成后，可以通过 Send Test 来检测，设置好后之前无辜背锅的 **WordPress Database Backup** 沉冤昭雪（btw：BackWPup 不好用，界面复杂，定期似乎还要设置 API）