---
title: "我如何写blog.czqi.net"
subtitle: "github.dev + Vercel + Hugo + LoveIt"
date: 2021-12-14
draft: true
tags: ["Hugo"]
categories: ["notes"]

toc:
  enable: true
---

## Why `github.dev + Vercel + Hugo + LoveIt`

[LoveIt](https://hugoloveit.com/):Hugo的主题

## 如何部署

## 内容管理
根据`LoveIt`主题的文档：
1. 文章放到`/content/posts`文件夹
2. 其他页面放到`/content`文件夹
3. 静态资源放到如下位置，使用**相对路径**进行引用，优先级依次为：
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

## 写作流程
1. 打开[`github.dev`](https://github.dev/)blog项目对应地址，即可进入编辑器
2. 在`/content/posts`下新建`.md`文档，复制头文件，开始写作
3. 编辑结束后，使用git commit到仓库，Vercel会自动同步，在数秒后部署完成。
