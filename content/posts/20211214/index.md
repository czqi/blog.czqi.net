---
title: "我如何写blog.czqi.net"
subtitle: "github.dev + Vercel + Hugo + LoveIt"
date: 2021-12-14
draft: false

tags: ["Hugo"]
categories: ["notes"]

toc:
  enable: true
---

### 内容管理
根据`LoveIt`主题的文档：
1. 文章放到`/content/posts`文件夹
2. 其他页面放到`/content`文件夹
3. 静态资源存放在以下路径，使用**相对路径**进行引用，优先级依次为：
    - 为每篇文章在`/content`下创建一个文件夹（称为`Page Bundle`），存放文章及其相关资源，Bundle内的资源只能用于Bundle内的文章
    - 静态资源存放到`/asset`文件夹
    - 静态资源存放到`/static`文件夹


### 文件头
文件头写在每个.md文件的最前，我常用的格式为：
```
---
title: "我如何写blog.czqi.net"
subtitle: "github.dev + Vercel + Hugo + LoveIt"
date: 2021-12-14
draft: false

tags: ["Hugo"]
categories: ["notes"]

toc:
  enable: true
---
```