---
  layout: post
  title:  "Jekyll 快捷发布"
  date:   2023-04-06 21:01:00 +0800
  categories: 工具二三
  tags:
    - Jekyll
    - Blog
---

## 背景

理论上静态 blog 的发布非常繁琐，但优化以后其实还好。当然对 Jekyll 来说，命名 post 文件和填写 YAML 要花点时间，不过这些信息实际上动态 Blog 也避免不了，而新发布和编辑后发布，就是 Git Bash 的主场了。

<!-- more -->

## 效果

编辑好 blog md ，打开 Git Bash，输入 git pub，回车，收工

如果还有修改或者新帖，在 Git Bash 中方向键 UP，回车，搞定

（更简单的是做成 BAT 文件直接执行，但是似乎 bat 文件调用的 git 没有魔法加持，不过这个也足够简单了）

## 实现

- 安装 Git Bash（[官网](https://git-scm.com/download/win)），似乎可以全程 next

- 运行

  ```
  git config --global user.name "cloudlet"
  git config --global user.email "cloudlet@users.noreply.github.com"
  ```

- （有必要可以参考 Git Bash 魔法设置）

- 在 c:\cloudlet 中新建 gitpub.sh 文件

  ```
  #!/bin/bash
  cd /c/cloudlet.info # repo位置
  git add .           # 添加所有更改文件
  git commit -am "m"  # commit 均设置为 m
  git push
  ```

- 在 Git 中运行 （pub 可随意更改）

  ```
  chmod +x /c/n/mis/sh/gitpub.sh
  git config --global alias.pub '!/c/cloudlet/gitpub.sh'
  ```

- 设置完成，之后在 Git 中运行 git pub 即可完成推送，等2、3分钟即可在 blog 看到更新

