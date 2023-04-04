---
  layout: post
  title:  "Wordpress 转 Jekyll 简易指南"
  date:   2023-04-02 10:00:00 +0800
  categories: 工具二三
  tags: [Blog, Jekyll, WordPress, VPS]
  author: Zephur
  excerpt_separator: <!-- more -->
---
因为各种原因，不打算维护费事的 Wordpress（VPS） 了，放弃治疗，全部扔省事的 Jekyll（GitHub Pages），Jekyll 其实看网上的各种帖子也很费事，这显然不科学，懒人攻略码起来

## 导出 Wordpress 

 WordPress to Jekyll Exporter，最省事的方案，安装插件，运行插件，会将 wordpress 所有 blog 导出为符合 Jekyll 的 _posts 文件夹

<!-- more -->

  但是，万恶但是往往出现的但是，运行插件可能出现“此站点遇到了致命错误，请查看您站点管理员电子邮箱中收到的邮件来获得指引”或者其他各种奇奇怪怪的问题……那么要采取替代方案吗？千万别，什么 WordPress2Jekyll、wp2jekyll 还有各种年久失修的工具都是各种坑，最简单的方法，将原来 wordpress 的通过 工具-导出 导出所有内容，再在 VPS 或者本地新建一个临时 Wordpress 导入全部内容，安装 WordPress to Jekyll Exporter，导出

## 建立 Jekyll 

  （懒人方案不在本地预览调试，不需要本地安装 ruby 之类环境，如果不是本地编辑推送更方便，甚至可以全过程在 GitHub 网页端处理，GitHub Desktop 也不需要安装。顺便说下，网上的很多帖子第一句就是安装 ruby 环境，第二句就是 windows 不建议安装 ruby 环境……）

建立 Jekyll 也是各种坑，没看到有哪篇帖子说清楚的，这里直接说操作（代码盲的理解可能有问题，但操作绝对清晰明了，顺便，该操作绑定使用 next 主题，其实就一句话，fork 一个 Jekyll 主题 repo，按照 githubuser.github.io 的规范命名 repo，修改下  _config.yml 的几处内容，清空 _posts 中的 md，粘贴自己的 _posts）

  打开 [jekyll-theme-next](https://github.com/Simpleyyt/jekyll-theme-next) 库，fork（右上）

  库名填写自己的gihutb用户名+github.io（如 cloudlet.github.io，注意这里用户名不要填错了，io 后缀也不要填成 com了，否则这个库就是普通库，无法识别成 GitHub Pages），其他不用管，点底部的 Create respository

  （本地）打开 GitHub Destop，点击（左上）Current respository，Add clone a respository ，选择刚fork的库 cloudlet/cloudlet.github.io

  修改 _config.yml，可以参考 [next 的使用文档](http://theme-next.simpleyyt.com/getting-started.html)，但实际上只需要修改 title:
    author: language: 等很少几处内容

  将 Wordpress 导出的 _posts 文件夹替换库里的  _posts 文件夹

  push orgin，完工，等几分钟，cloudlet.github.io 就可以看到帖子了（在 github web 端库的 Settings Pages 中可以看到 Your site is live at https://cloudlet.github.io/ ，Last deployed by @zephur  1 minutes ago，注意 GitHub Pages 各种响应都有延迟）

  blog 导航的分类、归档、标签也都会自动生效（github pages 会自动处理，可能隔几分钟才会完全更新好）

## 发布新帖

  那怎么发布新帖呢，直接在 _posts 中建立新的 markdown，使用规范文件名 2023-04-02-WordPress-to-Jekyll-Simple-Guide，日期前缀似乎必须，文件名使用中文也可以，但英文有利于 SEO？……然后同步就可以了。但这样会缺少相关信息，不利于 blog 的组织，所以需要在 md 头部添加 YAML

      ---
      layout: post
      title:  "Wordpress 转 Jekyll 简易指南"
      date:   2023-04-02 21:00:00 +0800
      categories: 工具二三
      tags: [blog, jekyll, wordpress]
      author: Zephur
      ---

## 摘要

next 支持 3 种摘要方式，需要在 _config.yml 设置

自动摘要：摘要文档第一段内容指定字数（如果第一段只是一个标题，那么抱歉，只会摘要这个标题，太傻了……）

```
#config
auto_excerpt:
  enable: true
  length: 200
```

手动标记：摘要文档 ` <!-- more -->`之前内容，可以自定义符号，可以在 front-matter 中单独指定`excerpt_separator: <!-- more -->`， 也可以在全局指定，如果开启全局指定，没有  `<!-- more -->`的文档会摘要全文……

```
#config
excerpt_separator: <!-- more -->
```

手动摘要：在  front-matter 中自己写摘要……

```
#config
excerpt_description: true
```

```
description：摘要功能实在太傻……
```

## 修改主题

直接在 `_sass\_variables\custom.scss` 中添加代码，普通 CSS 代码也可以

注意代码有错误会导致 pages build and deployment 无法完成。repo 的 Actions 页面可以查看，前面显示叉。报错 github-pages can't satisfy your Gemfile's dependencies. 但实际上可能是由 CSS 语法错误引起的。

## 自定义域名

将域名解析至 cloudlet.github.io 即可实现 https 访问（不需要额外进行证书等设置）

在域名网站选择 manage dns，设置 CNAME 记录指向  wandero.github.io，注意 www 可以设置，apex 域名 （根域名）设置 cname 可能报错（不符合域名管理规则？……），需要设置 4条 A 记录分别指向  185.199.108.153、185.199.109.153、185.199.110.153、185.199.111.153，设置完成后可能要过几个小时才会生效 

在 repo 根目录新建 cname 文件，内容为 cloudlet.info

在 repo setting 中的 Pages 页面 Custom domain 板块填入 cloudlet.info，保存会自动检查，一般 dns 生效后会通过，勾选下方的 Enforce HTTPS  打开 https 访问

## 404 自动跳转

Jekyll 和之前 WordPress 的页面结构大不相同，过度期间搜索引擎跳转会出现大量 404，可以修改 repo 根目录下的 404.html，清空内容，添加

```
<meta http-equiv="refresh" content="0; URL='https://cloudlet.info'" />
```

404页面会自动跳转主页或其他设置页面

## 永久链接

permalink 决定 post 地址，使用了转换插件的话会增加这个属性（但是中文标题会转换为ASCII 字符，可以使用 VSC 批量删除`permalink:.*\n`（正则），删除后可以使用批处理工具将原来的中文标题批量转换为英文标题（增强 SEO？……）

Next _config.yaml 中默认的永久链接设置为 permalink: pretty（`/:categories/:year/:month/:day/:title/`） ，建议修改为 `permalink: /:year/:slug`（文件名转换的 URL 友好的字符串）

## YAML



date 决定发帖时间，似乎还能预定时间发帖

tags 区分大小写

