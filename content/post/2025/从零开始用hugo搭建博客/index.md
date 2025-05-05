---
date : '2025-04-18T00:09:31+08:00'
title : '从零开始用hugo搭建博客'
categories : ['教学干货']
tags : ['博客搭建']
toc : false
---

# 为什么使用Hugo

- 性能好

  - **Hugo**：Hugo是采用 Go 语言编写的静态网站生成器，编译速度极快。在处理大量页面时，优势明显。比如构建拥有数千篇文章的大型博客，Hugo 可能在几秒内完成，不会因网站规模扩大而显著增加构建时间

  - **Hexo**：基于 Node.js的静态网页生成器，构建速度相对较慢。处理大型项目时，构建时间会明显变长。不过，对于小型网站，构建速度的影响不大
- 弊端
  - 静态网站的通病：没有后端。所有搜索、评论、在线写文章都需要通过插件（或主题）配置


# 参考

- 视频
  - [【大学生提高课】3 hexo与hugo博客搭建与github自动化推送和服务器推送_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fNNreEEDi/?spm_id_from=333.337.search-card.all.click&vd_source=7382d11a54f8a0e8a3163cc36fe6f157)

- 文档
  - [手把手学习 Hugo 博客的搭建:从入门到进阶](https://blog.eimoon.com/p/learn-hugo-blog-building-from-beginner-to-advanced/)

- 其他
  - [个人选择主题的作者的博客](https://blog.fiveth.cc/p/cybe/)

# 第一部分：环境搭建

[快速入门 | Hugo官方文档](https://hugo.opendocs.io/getting-started/quick-start/)

根据官方文档的「快速入门」，安装hugo（我直接下载预编译的二进制文件，具体方法参考官方文档或者[【大学生提高课】3 hexo与hugo博客搭建与github自动化推送和服务器推送_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fNNreEEDi/?spm_id_from=333.337.search-card.all.click&vd_source=7382d11a54f8a0e8a3163cc36fe6f157)的10:22-11:40）

# 第二部分：创建Hugo站点

## 创建Hugo新站点

```bash
hugo new site my-blog
```

其中 my-blog 是站点目录名称，可修改

# 第三部分：配置主题

## 选择主题

[官方主题仓库 ](https://themes.gohugo.io/)

[hugo-theme · GitHub Topics](https://github.com/topics/hugo-theme)（第三方主题仓库）

---

选择喜欢的主题，按照对应的文档进行操作（[【大学生提高课】3 hexo与hugo博客搭建与github自动化推送和服务器推送_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fNNreEEDi/?spm_id_from=333.337.search-card.all.click&vd_source=7382d11a54f8a0e8a3163cc36fe6f157)13:10-18:30，视频使用的是官方主题的「stack」）

我个人使用主题是：[hugo-theme-cybe](https://github.com/kmeykranz/hugo-theme-cybe)别人基于「stack」修改的主题，按照文档进行配置。可能遇到的问题：

- 1.删掉默认的配置文件`config.toml`，以前创建的站点目录中的文件叫做`config.toml`，现在叫做`hugo.toml`，删除它

- 2.获取主题文件，如果不能用git命令，直接下载源文件，把文件名删去最后的main，直接拖入themes中

- 3.不知道为什么，我直接用hugo-theme-cybe搜索功能用不了，所以我是先放入了原本的「hugo-theme-stack」主题，然后放入「hugo-theme-cybe」把一些内容覆盖，之后再修改，就能正常使用搜索了

---

**根目录下`layouts`和`themes/<theme name>/layouts/`的区别**

`layouts/`目录里保存是 Hugo 的模板文件。`layouts/`是站点级别的模板

`themes/<theme name>/layouts/`是主题级别的模板，**一般来说，站点级别模板的设置优先于主题级别的模板（*可修改优先级*）**

## 应用主题

**1.按照文档下载主题**

- 如果***使用git命令***，自动生成在站点目录的`themes`中
- 如果***手动下载源文件***，需要手动拖入`themes`中

**2.配置主题名称**

下载完成后在 `hugo.yaml` 文件中配置主题名称（这个hugo-theme-cybe是我使用的主题）：

```bash
theme: hugo-theme-cybe
```

# 第四部分：内容创建与管理

## 了解Hugo目录结构

> 目录可能不一样，但文件夹作用是一致的

```markdown
my-blog/
├── content              # 存放所有内容文件
│   ├── _index.md        # 博客首页内容
│   ├── post            # 博客文章
│   │   ├── first-post.md
│   │   └── second-post.md
│   └── pages            # 博客页面
│       └── about.md     # 关于页面
├── data                 # 存放站点数据
│   ├── authors.yml      # 作者信息
│   └── config.toml      # 站点配置文件
├── i18n                 # 国际化语言文件
│   ├── en.toml          # 英文语言文件
│   └── zh.toml          # 中文语言文件
├── layouts              # 存放页面模板
│   ├── _default         # 默认模板
│   ├── partials         # 模板片段
│   └── index.html       # 首页模板
├── assets               # 存放编译前的资源文件
│   ├── css              # 存放 CSS 源文件
│   ├── js               # 存放 JavaScript 源文件
│   └── images           # 存放图片源文件
├── resources            # 存放生成的资源文件
│   └── _gen             # 生成的资源文件
├── static               # 存放静态资源（如图片、CSS、JS）
│   ├── css              # 存放编译后的 CSS 文件
│   ├── js               # 存放编译后的 JavaScript 文件
│   └── images           # 存放图片文件
├── public               # 生成的网站文件
├── themes               # 存放主题文件
│   └── my-theme         # 自定义主题文件
│       ├── layouts      # 存放页面模板
│       ├── static       # 存放主题静态资源
│       └── theme.toml   # 主题配置文件
├── archetypes           # 内容模板文件
│   ├── default.md       # 默认内容模板
│   └── post.md          # 博客文章模板
└── hugo_build.lock      # Hugo 包管理文件
```

## 添加内容

在`content/post`目录中创建`my-first-post.md`（*文件名，可更改*）文件：

```bash
hugo new content/post/my-first-post.md
```

>hugo new 什么，这是固定的。在我的目录中，content文件夹是存放所有内容的文件夹，post是存放博客文章的文件夹。然后想要在post文件夹下直接创建文章，所以这么输入命令
>
>可以多添加几个文件夹（可中文/英文），或者修改md文档的名称（可中文/英文），比如：hugo new content/post/2025/样例.md
>
>不过博客还有image，文章预览图。想要使用image，文章必须命名成index.md。我个人的习惯是：hugo new content/post/文章的标题当作文件夹名/index.md
>
>index.md不影响文章的标题名

### Front-matter

[官网](https://stack.jimmycai.com/writing/frontmatter)

`Front-matter` 是 markdown 文件最上方以`---`分隔的区域，用于指定个别档案的变数。`---`下方使用markdown语法添加内容

基本：

```markdown
---
title: 这是标题
description: 这是一个副标题
date: 2020-09-09
darft: true
slug: test-chinese
image: helena-hertz-wWZzXlDpMog-unsplash.jpg
categories:
    - Test
    - 测试
tags:
    - 中文
toc: true
---
```

>  draft 是操作，值为 true。Hugo 在构建网站时不会发布草稿内容。如果删除，默认发布，类似draft是false
>
>  slug用来生成网页URL的路径部分。如果没有，网页路径的名字就是标题名
>
>  image是文章预览图。注意：想要使用image，文章必须命名成index.md（可以是像`index-zh-cn`这样带语言的，但必须是index），同时文章和图片在同一个文件夹
>
>  categories是分类。可以用数组的写法，如：categories: ['分类1'，‘分类2']
>
>  tags是标签。可以用数组的写法
>
>  toc是页面内容表，即标题

# 第五部分：本地预览与配置

## 博客本地预览

在对内容和主题进行修改后，您可以使用以下命令进行本地预览：

```bash
hugo serve
```

这将在你的浏览器中打开一个本地服务器，访问`http://localhost:1313`来查看博客页面（本地预览默认是不渲染草稿）

# 第六部分：GitHub推送自动化和博客托管优化指南

可以使用***GitHub Pages***，将Hugo博客部署到互联网上，它是GitHub提供的免费静态网站托管服务

 如果使用，GitHub Page，需要在GitHub上创建一个新的仓库，仓库名称遵循`your-github-username.github.io`的格式（*your-github-username是你的github用户名*）。这将是你博客的主域名

我使用***Netlify***托管

---

在使用Github Pages构建并托管博客时，我们面临一个常见问题：**如何在保持源码安全的同时，将构建好的`public`文件用于页面展示。**

可以通过**创建两个GitHub仓库来实现不同用途的分离和自动化管理**

## GitHub推送自动化

### 源码仓库（source）

- 用于存储博客相关的源码，包括Markdown文件、配置信息等未构建的内容
- 设为Private（私有）仓库，确保源码安全

### 展示仓库（show）

- 用于存储构建后的文件（如public文件夹），供Github Pages或其他托管服务使用
- 设为Public（公开）仓库，确保可以正常访问页面

步骤：

[【大学生提高课】3 hexo与hugo博客搭建与github自动化推送和服务器推送_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fNNreEEDi/?spm_id_from=333.337.search-card.all.click&vd_source=7382d11a54f8a0e8a3163cc36fe6f157)20:47-35:05的视频

通过自动化工作流，把源码推送到私人仓库后，自动触发，推送到公开仓库

### 发布文章

这里已经按照视频里的步骤配置好了，发布文章的代码也是最基本的三个，用终端打开博客所在的文件夹，然后依次输入：

```bash
git add .
git commit -m "备注信息"
git push -u origin main
```

## 使用Netlify托管

[Netlify官网](https://www.netlify.com/)

虽然GitHub Pages可以直接托管展示仓库的内容，但其二级域名（username.github.io）不够美观，也不满足个性化需求

可以使用Netlify这样的免费静态网页托管平台

### 为什么选择Netlify？

**1.自定义域名支持**

Netlify允许用户免费绑定自定义域名（*免费绑定，但域名要去阿里云等付费买*）

**2.免费托管服务**

提供免费、高效的静态网站托管服务，支持全球CDN

**3.自动化部署**

Netlify可与GitHub仓库继承，自动从展示仓库拉取最新的构建内容并部署

**4.HTTPS支持**

Netlify提供免费的HTTPS证书，默认启用HTTPS，提升网站安全性

# 第七部分：Typora+PicGo图床配置

[【大学生提高课】3 hexo与hugo博客搭建与github自动化推送和服务器推送_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fNNreEEDi/?spm_id_from=333.337.search-card.all.click&vd_source=7382d11a54f8a0e8a3163cc36fe6f157)34:29-44:55的视频

# 第八部分：自定义域名

在***阿里云***或者***腾讯云***等购买一个域名。在GitHub仓库的`Settings`->`Pages`中配置自定义域名

# 第九部分：其余更改

## hugo.yaml

`hugo.yaml`中：

```markdown
baseurl: https://example.com/
languageCode: zh-cn
theme: hugo-theme-cybe
title: Example Site
copyright: Example Person
```

> baseurl修改成你的网站域名，在主页，点击文章，会根据你的域名跳转文章的内容
>
> title是网站的名字
>
> copyright是版权

`hugo.yaml`中其余文字和emoji内容，按情况修改

## categories文件夹

`categories`存放分类，自己定义，文档名称是`_index.md`（我也不知道为什么加_）

## 头像、网站页签，代码块顶部图标

头像我放在了`themes/hugo-theme-cybe/assets/img`里

网站页签和代码块顶部，我直接从[kmeykranz/blog-file: Hugo博客源文件](https://github.com/kmeykranz/blog-file)作者源文件里，把`static`整个文件复制过来

把自己的图片变成页签，需要把图片转成**ico**格式，可以看[【教程】jpg转ico,将桌面软件图标更换为任意自己喜欢的图片！_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1uD4y1e78D/?spm_id_from=333.337.search-card.all.click))