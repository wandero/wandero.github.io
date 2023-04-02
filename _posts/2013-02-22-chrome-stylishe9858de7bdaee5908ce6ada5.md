---
id: 140
title: 'Chrome Stylish 配置同步'
date: '2013-02-22T09:20:04+08:00'
author: Zephur
layout: post
guid: 'http://foro.cloudlet.info/t/140'
permalink: /2013/02/22/chrome-stylish%e9%85%8d%e7%bd%ae%e5%90%8c%e6%ad%a5/
duoshuo_thread_id:
    - '6275545987066888961'
mytory_md_visits_count:
    - '75'
categories:
    - Notes
tags:
    - Chrome
    - sync
---

Chrome 可以使用自带工具同步，但因为某种地球人都知道的原因，可靠度不高，另外对于某些扩展配置也无能为力

而用 Dropbox 同步整个 User Data 的话，一方面文件数量过多，一方面几个状态文件会一直被锁定有点碍眼。

然后，就是本文要提到的了

**同步文件夹**: \\User Data\\Default\\databases\\

**同步方法**： [Dropbox Folder Sync ](http://satyadeepk.in/dropbox-folder-sync/)

**使用限制**：

Windows 系统 NTFS 格式（对于其他用户，相信符号链接、命令行之类的小把戏不用煞有介事的介绍）

**软件使用**：

其实 Dropbox Folder Sync 只是把原来符号链接命令行什么的打包成右键菜单更清晰直观而已

Dropbox Folder Sync 会将你选定的（即右键 Sync with Dropbox）的文件夹移动到 Dropbox 文件夹中，并在原位置留下一个镜像什么的，在操作上来说，对这两处文件夹做的改动都会生效（包括删除）

剩下的就很简单了，选定 \\User Data\\Default\\databases\\，右键 Sync with Dropbox，完毕

**其他**

最后，通过 Dropbox Folder Sync 可以方便的利用 Dropbox 同步各类配置文件，但因为用户无法控制链接在 Dropbox 文件夹中的位置，可以在 Dropbox 中新建特定的文件夹来同步其他文件，而根目录专门针对各种配置文件件以避免目录混乱。

**Update**

1、 似乎 databases 中的其他文件没有同步的需求，可以直接同步

`\databases\chrome-extension_fjnbnpbmkenffdnngjfgmeleoegfcffe_0\`

2、Dropbox Folder Sync v2.7在 Win7x64 上可能会出现无法显示右键子菜单问题，换回v2.5正常