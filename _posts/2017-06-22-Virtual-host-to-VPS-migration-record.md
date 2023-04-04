---
id: 637
title: '虚拟主机至 VPS 迁移记录'
date: '2017-06-22T12:20:23+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/?p=637'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170622%20%E8%99%9A%E6%8B%9F%E4%B8%BB%E6%9C%BA%E8%87%B3%20VPS%20%E8%BF%81%E7%A7%BB%E8%AE%B0%E5%BD%95.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_visits_count:
    - '252'
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/170622%20%E8%99%9A%E6%8B%9F%E4%B8%BB%E6%9C%BA%E8%87%B3%20VPS%20%E8%BF%81%E7%A7%BB%E8%AE%B0%E5%BD%95.md'
categories:
    - 工具二三
tags:
    - VPS
---

> 新手主观视角，达人多指正
> 
> 受吕立青 Blog 的影响，觉得 Jekyll 的 Markdown 编辑发布一体化系统很赞，但又不习惯把页面放在容易被墙的平台上，所以决定自己搭一个类似的系统，然后，开始了……漫长的趟坑之路……

<!-- more -->

## VPS 选择

随手选了 Vultr，之后发现选择无大问题，未找优惠较亏

服务商选择不必太纠结，VPS 一般都支持月结，国外网络环境不同服务商之间迁移内容也非常方便

### 优点

- **镜像功能（Snapshot）免费** 方便备份，以及在不同区域服务器间转移
- **按 VPS 使用时间收费** 即可同时开多台服务器，也可以通过摧毁服务器来停止使用（有镜像可以方便的重建）
- **通过 Paypal 即可付款** 据说 Linnode 要审核身份
- **节点较多** 虽然国外连接质量都够呛，但至少还能折腾着换下不是
- **促销活动较多** 同时会造成一定超售或服务器被滥用

### 趟坑心得

- VPS 操作基本通过 SSH，掉包严重影响使用感受
- VPS 至国内网络连接质量和服务器质量基本无关，视实际线路、运气和天气而定
- PingInfoView 可以方便的获取批量 IP 的 ping 和掉包率
- PingInfoView 获得的 ping 和掉包率仅供参考，实际 VPS 效果会打折
- 有些节点虽然 ping 和掉包看上去不错，实际使用却很糟糕，可能是因为同服务器其他 VPS 的影响
- 服务器的网络质量指标波动很大，请于国内晚高峰测试
- 同一节点不同 IP 网络连接质量可能大不相同，可多开 VPS 直至获得理想 IP

### 免责观点

- Linode 被用（滥用）的太狠（大量 IP 被……），区域节点比 Vultr 少，免费功能比 Vultr 少（关键的镜像服务收费），墙内不推荐
- DigitalOcean 的各类教程真心赞，步骤详实考虑周到，获益匪浅

## 环境选择

### Linux 系统

最终选了 Ubuntu 16.04

（新手）珍惜生命，远离 Centos

（新手）开包即食，请用 Ubuntu

初以生产环境多用 Centos 入坑，结果 Centos 系统保守（陈旧）而应用环境要求较高，平趟深坑无数，谋杀脑细胞无算，而成果惨淡，后遇 Ubuntu，拨云见日……

### 是否上 Docker

使用有一定门槛，新手不建议

### 环境 Lemp

坊间传言 Lemp 更适合平民配置，大户请 Lamp

不推荐使用一键安装包，使用一键包之后，因为用户规模的原因，遇到问题能够查询的信息太少，且安全性存疑

### PHP 版本

建议一步到 7

长痛不如短痛，辛辛苦苦以 PHP 5 为基础配置好全部站点，突然因为一个 WordPress 主题的要求升到 PHP7 结果趟雷无数的经过回想下都……

### 是否上 SSL

见仁见智，对安全性要求不高不建议上

据说 Google 有加成，据说国内引擎都不收录

**安装 SSL 务必注意 HTS 深坑**

简单来说，如果 SSL 模式不小心设置成了 HTS 且被广泛使用，那么就基本无法切换回非 SSL 了（几乎所有访问过 https 域名的浏览器都会强制使用 SSL 模式直至声明过期似乎是几个月或者更久）

个人教训，使用 Certbot 部署 Letsencrypt 证书时似乎未经选择就使用了 HTS 模式（还好处于测试阶段）

### 是否上 phpmyadmin

据说极不安全，看到的安全方案也是五花八门，基于安全考虑不建议上，可以先命令行凑合下

## 其他选择

### Gitlab

低配 VPS 够呛，个人使用也无多大必要，Github Bitbucket 效果更佳

### Huginn

低配 VPS 够呛，爬虫这类坑也比较深，新手不建议

## VPS 和 虚拟主机的区别

如果只用 WordPress 的话……从虚拟主机换到 VPS 在功能上几乎没有区别，但性能上区别较为明显，另外 VPS 还需要一定的配置和维护，上手多少有些麻烦

如果不只是用或不准备只用 WordPress 而又还能接受一定程度的折腾的话，先花个五刀体验下吧，VPS 能做的太多了