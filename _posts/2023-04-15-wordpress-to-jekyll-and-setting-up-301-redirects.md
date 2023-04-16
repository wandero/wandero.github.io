---
  layout: post
  title:  "Wordpress 转 Jekyll 设置 301 重定向"
  date:   2023-04-15 21:00:00 +0800
  categories: 工具二三
  tags:
    - Jekyll
---

## 前言

Wordpress 转 Jekyll 后 帖子地址都变了，Google 搜索各种 404，之前以为是短时间情况，然而我还是低估了 Google……

那怎么办呢？有问题找 ChatGPT……

#### Z:

> 我的blog改了结构包括帖子的permallink，google搜索结果都无法访问了帖子了，怎么办

#### ChatGPT:

> 当你更改了博客的结构和 permalinks 时，确实可能导致 Google 搜索结果中的旧链接失效。为了解决这个问题，你可以采取以下措施：
>
> 1.重新提交 Sitemap：在更改结构和 permalinks 后，生成一个新的 Sitemap 并提交给 Google Search Console。这有助于 Google 更快地重新抓取你的网站并更新索引。
>
> 2.301 重定向：为旧链接设置 301 重定向，将其指向新的 permalinks。这样，当用户点击 Google 搜索结果中的旧链接时，他们将被自动重定向到新的链接。同时，301 重定向还有助于保留原有页面的 SEO 价值。
>
> 3.更新内部链接：检查你博客中的内部链接，确保它们都指向新的 permalinks。这将有助于提高网站的内部链接结构和用户体验。
>
> 4.耐心等待：更改结构和 permalinks 后，需要一定时间才能使 Google 搜索引擎更新其索引。在此期间，确保你的博客内容质量高、更新频繁，以便更快地被搜索引擎重新抓取和索引。
>
> 5.监控 Google Search Console：密切关注 Google Search Console 中的“覆盖”报告，以了解网站的抓取和索引状况。如有必要，解决出现的任何问题，以提高你博客在搜索结果中的表现。
>
> 通过采取这些措施，你可以减轻结构和 permalinks 更改对 Google 搜索结果的影响，并确保用户能够顺利访问你的博客帖子。

然后我告诉 ChatGPT 1 已经操作了，3、4、5……看上去可以处理的之用 2 了

301 重定向以前经常听说，但总觉得操作太复杂也用不上，于是继续代码不决问 ChatGPT

## 操作

Z:

> 我用的 github pages jekyll，怎么做301重定向

……以下省略 N  轮，总之在艰苦的搬运工作后（搬运代码运行，搬运报错反馈，还时不时的陷入死循环），终于在 ChatGPT 的帮（主）助（导）下解决了问题，结果如下：

编写 Python 脚本 `cope301.py`

分析 Jekyll 的 _posts 文件夹，获取 YAML 中的 id 信息，并根据当前 Jekyll 的 permarlink 规则建立新旧地址的字典。

在 `_layouts` 文件夹中创建 `redirect.html` 文件。

生成一个 t 文件夹，内部包含所有原 id 为名称，md 为后缀的文件，文件内容如

```
---
layout: redirect
redirect_url: https://cloudlet.info/2023/logseq-clean-unused-attachments
---
```

推送 build 后 blog 就完成 301 设置了，可以自动将原来 https://cloudlet.info/t/1270 的链接 301 重定向至 https://cloudlet.info/2023/logseq-clean-unused-attachments

最后，有点疑惑这篇 blog 存在的价值……

## 代码

### redirect.html

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Redirecting...</title>
  <link rel="canonical" href="{{ page.redirect_url }}" />
  <meta http-equiv="refresh" content="0; url={{ page.redirect_url }}">
</head>
<body>
  <h1>Redirecting...</h1>
  <a href="{{ page.redirect_url }}">Click here if you are not redirected.</a>
  <script>location='{{ page.redirect_url }}'</script>
</body>
</html>
```

### cope301.py

```python
import os
import re
import yaml

def parse_yaml(file_path):
    with open(file_path, 'r', encoding='utf-8') as f:
        content = f.read()
        yaml_content = re.search(r'^---\s*\n(.*?)\n---', content, re.MULTILINE | re.DOTALL)
        if yaml_content:
            try:
                yaml_data = yaml.safe_load(yaml_content.group(1))
                return yaml_data
            except yaml.YAMLError:
                print(f"Error parsing YAML in file: {file_path}")
                return None
        else:
            print(f"No YAML data found in file: {file_path}")
            return None

def main():
    script_path = os.path.dirname(os.path.realpath(__file__))
    markdown_folder = os.path.join(script_path, '_posts')
    redirects_folder = os.path.join(script_path, 't')
    
    if not os.path.exists(redirects_folder):
        os.makedirs(redirects_folder)
    
    for file in os.listdir(markdown_folder):
        if file.endswith('.md'):
            file_path = os.path.join(markdown_folder, file)
            yaml_data = parse_yaml(file_path)
            if yaml_data and 'id' in yaml_data:
                post_id = yaml_data['id']
                date_pattern = re.compile(r'\d{4}-\d{2}-\d{2}-')
                new_slug = date_pattern.sub('', file).replace('.md', '').lower()
                year = file[:4]
                new_url = f'https://cloudlet.info/{year}/{new_slug}'
                redirect_file = os.path.join(redirects_folder, f'{post_id}.md')
                with open(redirect_file, 'w', encoding='utf-8') as f:
                    f.write(f'---\nlayout: redirect\nredirect_url: {new_url}\n---\n')

if __name__ == '__main__':
    main()

```

