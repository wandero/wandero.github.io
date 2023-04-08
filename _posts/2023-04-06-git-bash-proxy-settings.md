---
  layout: post
  title:  "Git Bash 魔法设置"
  date:   2023-04-06 21:00:00 +0800
  categories: 工具二三
  tags:
    - Git
---

这块代码盲不是非常清楚，姑且算作操作记录吧，据说 SSH 代理要靠谱一些，但我有些没明白这套操作是不是 SSH 通道

## Proxy 设置

在 c:\users\cloudlet.info\\.gitconfig 中添加类似代理信息，http 代理只需要填写一条 http，不需要填第二条 https，代理用户名密码（user:password）可省略，端口记得修改

<!-- more -->

```
[http]
	proxy = http://user:password@127.0.0.1:1080
```

## SSH 设置

- Git 运行 ssh-keygen

- 打开 c:\users\cloudlet.info\\.ssh\id_rsa.pub，复制全部内容（包括开头的 ssh-rsa）

- Github -  Setting - SSH keys - New SSH key ，粘贴，Add SSH key

- Git 运行 ssh -T git@github.com

- 第一次会显示

  ```
  The authenticity of host 'github.com (140.82.121.3)' can't be established.
  ...
  This key is not known by any other names.
  Are you sure you want to continue connecting (yes/no/[fingerprint])?
  ```

- 输入 yes 回车，会显示成功认证

  ```
  Hi Cloudlet! You've successfully authenticated, but GitHub does not provide shell access.
  ```

  

  