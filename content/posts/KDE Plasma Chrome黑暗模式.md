---
title: "KDE Plasma + Chrome 黑暗模式"
date: 2022-05-20
draft: false
tags: ["KDE Plasma", "Chrome"]
categories: ["env"]
---

## 1. 使用Classic主题

切换为Classic主题，不要使用GTK+。

## 2. 替换启动命令

原始的启动命令是：
```bash
/usr/bin/google-chrome-stable %U
```

改为：
```bash
/usr/bin/google-chrome-stable %U --enable-features=WebUIDarkMode --force-dark-mode
```

## 3. 在chrome://flags中启用黑暗模式

访问`chrome://flags`，搜索`dark`，将`Auto Dark Mode for Web Contents`的选项改为`Enabled with selective inversion of everything`。