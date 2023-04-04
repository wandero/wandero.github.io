---
id: 238
title: '一个诡异的 Excel 文本型数值问题'
date: '2014-06-20T11:43:20+08:00'
author: Zephur
layout: post
guid: 'http://cloudlet.info/t/238'
duoshuo_thread_id:
    - '6275546027772609282'
mytory_md_visits_count:
    - '38'
categories:
    - Notes
tags:
    - excel
---

某些 csv 转 xls 过程中，会出现一些真实数据为`“            ”`和`“1.234     ”`而显示为空白和 `1.234`之类的单元格

对于这类诡异的单元格，用笨方法粘贴到记事本替换掉空格和双引号固然可以搞定，但是效率……

直接使用VALUE TRIM SUBSTITUTE 等等函数也都毫无效果……

然后终于折腾出通过 LEFT 截掉最末位符号再通过 VALUE 取值的方法解决掉了1.234 这类情况，而显示为空格的仍然无解……

无奈转换思路，祭出 IFERROR 直接将无解单元格归零……

代码： `=IFERROR(VALUE(LEFT(A1,LEN(A1)-1)),0)`