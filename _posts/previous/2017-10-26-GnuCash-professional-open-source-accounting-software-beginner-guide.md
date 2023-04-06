---
id: 806
title: '专业开源记账软件 GnuCash 简易上手指南'
date: '2017-10-26T21:37:44+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/?p=806'
mytory_md_path:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/171026%20%E4%B8%93%E4%B8%9A%E5%BC%80%E6%BA%90%E8%AE%B0%E8%B4%A6%E8%BD%AF%E4%BB%B6%20GnuCash%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
mytory_md_text:
    - ''
mytory_md_mode:
    - url
mytory_md_path_old:
    - 'https://raw.githubusercontent.com/wandero/blog/master/17/171026%20%E4%B8%93%E4%B8%9A%E5%BC%80%E6%BA%90%E8%AE%B0%E8%B4%A6%E8%BD%AF%E4%BB%B6%20GnuCash%20%E7%AE%80%E6%98%93%E4%B8%8A%E6%89%8B%E6%8C%87%E5%8D%97.md'
dotGood:
    - '26'
categories:
    - 方法一二
tags:
    - Tally
---

## 背景

最开始记账的时候使用的某著名记账应用，软件本身也算中规中矩，后来一方面因为卖用户信息的传闻闹得沸沸扬扬，一方面觉得输入太慢，也远不如 Excel 灵活，于是改用 Excel。

Excel 的好处就比较多了，输入快捷，统计方便，扩展灵活。但因为当时记得是简单的流水账，虽然可以分类统计开销之类，但各种账户之间的情况一团乱麻，最近接触到复式记账法，打算尝试下，而支持复式记账的软件可供选择的就不多了。

<!-- more -->

GnuCash 免费开源、支持 Windows、支持复式记账，相比 Excel，麻烦的就是需要记录的东西比较多（其实 Excel 也可以复式记账，不过功能实现上相对麻烦，不如专业软件省心） ，好处是你可以精确知道自己有多少钱了（或者，钱在哪了？或者，有没有钱了？或者，欠多少钱了？）

目前使用的是 GnuCash 2.6.18 版本（中文界面）。

## 复式记账概念

对于普通用户来说，GnuCash 涉及到大量财务方面的专业词汇，本身的汉化也不全，上手可能略有麻烦，建议使用之前简单了解一下复式记账法。

（笔者也才上手，以下说法仅供参考）因为复式记账是以公司为主体的，所以有些概念套到个人、家庭账目上会很别扭，像借记、贷记的说法也比较绕，开始可以略过，基本上了解「一切皆科目，数字在科目中流动」即可。具体来说，任何一笔账目，都会至少对应两个科目——点个外卖，「支出」会变化，如果信用卡付账，「负债」会变化，如果现金付账，「资产」会变化。至于左列、右列、加还是减这些也可以等具体记账时实践。此外的两大科目，「收入」很好理解，发工资了，「收入」和「资产」都会变化；「权益」这个概念因为也是主要针对公司的（谁出了多少本钱？），个人使用的时候，可以简单理解为最开始记账的时刻各个账户（科目）有多少钱（「所有者权益」-「期初余额」）

## 软件的使用

### 科目设置

装好软件后会首先要求设置科目层次（不清楚设置的话一路前进即可），因为后面要提到的快速补全不支持中文的问题，可以先选择「通用科目」，之后根据实际情况修改成英文或拼音，不同科目大类的设定多有不同，不熟悉复式记账的最好直接修改「通用科目」中特定或类似的科目。科目大类一般为默认的「权益」、「资产」、「负债」、「收入」、「支出」。

账目不对的时候系统会自动生成「不平衡的」科目，这是因为复式记账任何账目至少涉及两大科目而实际录入的账目不平的关系，改好账目后「不平衡的」科目金额会归零（「孤立的」科目情况类似）

### 存储格式

GnuCash 提供了四种存储格式，xml 格式有定期的数据备份（sqlite3 似乎没有），数据库放在云同步软件（Dropbox 或者坚果云）中就可以轻松实现多终端同步使用了。

### 快速录入

#### 科目快速补全（Quickfill）

对中文用户来说有点尴尬，中文版默认创建中文科目，而该功能仅支持英文（不包括数字），所以为了使用该功能，建议使用英文（或拼音）命名所有科目。例如 Assets:Cash（ZiChan:XianJin） 可以在任意科目类单元格里使用 A:C （Z:X）快速补全（中间的冒号可以在设置「编辑-首选项-科目-分隔字符」中修改为其他符号，如填入 slash 可修改为 `/`）

注意，「自动提升列表」（功能编辑-首选项-账簿-动作）和科目快速补全功能有点冲突，可以关闭该功能（或者使用每次打冒号之前按下 Esc 键关闭提示列表，再用子科目的首字母补全）。

#### 日期快速切换

在日期类单元格，可以使用

- `-` `=` 切换至前一天和后一天
- `_` `+` 切换至前一周和后一周
- `m` `h` 切换至本月的第一天和最后一天
- `y` `r` 切换至本年的第一天和最后一天
- `t` 切换至今天

#### 金额简单计算

作为一款记账软件，GnuCash 在金额类单元格里提供了简单的计算功能，例如可以直接输入 30\*2 这类表达式（不需要输入 `=` 号）

#### 交易记忆补全

在描述单元格输入之前输入过的内容时，会出现自动补全提示，TAB 执行补全会根据匹配历史交易自动补全整个交易（包括相关科目和金额），这个功能极大的减轻了频繁发生的日常开支记账的工作量。

### 账簿模式

GnuCash 提供了「基本分类账」、「自动拆分分类账」和「交易日记账」三种账簿模式（「查看」菜单），新手建议一般情况下使用「基本分类账」模式方便账目录入，需要拆分交易的时候切换到「交易日记账」模式方便分割交易。另外可以通过 工具-总分类账 菜单调出「总分类账」页面，熟练的话直接在该页面记账更方便（不需要打开或者选择科目页面）。

### 拆分交易

因为关系到交易涉及各科目的准确记录，拆分交易这种操作就很有必要了（购买记录根据物品拆分，支出记录根据付款方式拆分等）。Gnucash 的拆分交易操作刚接触有点绕，新手建议切换至「交易日记账」模式中操作。

具体操作（根据物品拆分的情况），（「交易日记账」下），每笔交易在选中状态时至少包括四行内容：

- 第一行为交易描述，可以在描述单元格中填入交易梗概（因为在其他模式中无法直接看到具体分割条目的备注，所以梗概建议有一定信息量方便查阅）
- （之后 TAB 转入）第二行开始记录具体分割条目，首先记录资金去向，依次填入（可通过 TAB 切换）备注（物品名）、科目（消费类别）、资金收入（物品价格）、资金支出（应为空）。（之后 TAB 转入）第三行重复，直至分项物品记录完毕。
- （之后 TAB 转入）最后一行记录资金来源，依次填入备注（可为空）、科目（支出账户）、资金收入（应为空）、资金支出（支出总金额），其中资金支出一栏已由系统自动计算，可与实际支出金额对照校验。

### 对账

对于个人用户来说，涉及存在清晰账单（银行卡、支付宝之类）的科目，对账功能比较好用。下面以具体操作说明：

选择特定科目，右键 – 对账，选择日期（如信用卡的账单日期），期末余额（信用卡的账单金额）- 确定，对账窗口会列出所有对账期间的收入和支出明细，分别全选（Crtl + A，空格），账目无误的话右下角的差额会为 0，否则表示账目与实际不符，需要手动修正（补充）具体账目或者通过「面板菜单栏-余额」自动添加条目修正，修正无误后点击「选中项对账」即可。（对账操作后，对过账的条目的第五列内容会由「未」变为「对」）

### 修改界面语言

在 `\gnucash\etc\gnucash\environment` 任意位置中添加

```
LANG=ll_LL
LANGUAGE={LANG}
```

可将界面修改为英文，将 `ll_LL` 替换为 `zh_CN` 可切换回中文

### 美化界面字体

Windows 界面下没做中文处理的软件界面体验太差，可用 MacType 进行字体替换及渲染（可参考 [Windows 字体美化神器 MacType 简易上手指南](/t/821) )

### 其他

对于个人用户来说，GnuCash 还提供了强大的导入导出、计划交易、预算、报表等功能，感兴趣的可自行探索。而最重要的无疑还是主界面底部的概要栏，设置好所有选项，录入你的全部账目后，好好地看看那个「Net Assets」（净资产）吧，那个代表你当前全部身家的数字，希望你的位数比较多，并且前面不要是负号……