因因为各种原因，不打算维护费事的 Wordpress（VPS） 了，放弃治疗，全部扔省事的 Jekyll（GitHub Pages），Jekyll 其实看网上的各种帖子也很费事，这显然不科学，懒人攻略码起来

## 导出 Wordpress 

  最省事的 WordPress to Jekyll Exporter，安装插件，运行插件，会将 wordpress 所有 blog 导出为符合 Jekyll 的 _posts 文件夹

  但是，万恶但是往往出现的但是，运行插件可能出现“此站点遇到了致命错误，请查看您站点管理员电子邮箱中收到的邮件来获得指引。”或者其他各种奇奇怪怪的问题，

那么要采取替代方案吗？千万别，什么 WordPress2Jekyll、wp2jekyll 还有各种年久失修的工具都是各种坑，最简单的方法，将原来 wordpress 的通过 工具-导出 导出所有内容，再在 VPS 或者本地新建一个临时 Wordpress 导入全部内容，安装 WordPress to Jekyll Exporter，导出

## 建立 Jekyll 

  （不需要本地安装 ruby，本地只和普通 git 库一样进行常规编辑操作）

  这一步也是各种坑，没看到有哪篇帖子说清楚的，直接说操作（代码盲的理解可能有问题，但操作绝对清晰明了，顺便，该操作使用 next 主题）

  打开 [jekyll-theme-next](https://github.com/Simpleyyt/jekyll-theme-next) 库，fork（右上）

  库名填写自己的gihutb用户名+github.io，如 cloudlet.github.io，其他不用管，点底部的 Create respository

  打开 GitHub Destop，点击（左上）Current respository，Add clone a respository ，选择刚fork的库 cloudlet/cloudlet.github.io

  修改 _config.yml，可以参考 [next 的使用文档](http://theme-next.simpleyyt.com/getting-started.html)，但实际上只需要修改 title:
    author: language:

  将 Wordpress 导出的 _posts 文件夹替换库里的  _posts 文件夹
  push orgin，完工，等几分钟，cloudlet.github.io 就可以看到帖子了

  blog 导航的分类、归档、标签也都会自动生效（github pages 会自动处理，可能隔几分钟才会完全更新好）

## 发布新帖

  那么怎么发布新帖呢，可以直接在 _posts 中建立新的 markdown（然后同步就完工了），但这样会缺少相关信息，不利于 blog 的组织

  建议 md 文件使用规范文件名 2023-04-02-WordPress-to-Jekyll-Simple-Guide

  在 md 头部添加 YAML

    ```
      ---
      layout: post
      title:  "Wordpress 转 Jekyll 简易指南"
      date:   2022-04-02 21:00:00 +0800
      categories: Notes
      tags: [blog, jekyll, wordpress]
      author: Zephur
      ---
      ```


​      