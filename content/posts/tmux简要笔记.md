---
title: "tmux简要笔记"
date: 2022-05-13
draft: false
tags: [tmux]
categories: ["notes"]
---

# tmux简要笔记

## 安装tmux
Debian可以使用apt命令直接安装。

```bash
sudo apt install tmux
```

## tmux概念
`Ctrl-b`是默认的快捷键和指令的入口。

## 窗格Pane
首先输入`tmux`，进入tmux，并尝试创建窗格、切换窗格、调整窗格大小和关闭窗格等操作。

创建窗格：使用快捷键`Ctrl-b "`可以将当前窗格上下平分为两个窗格，`Ctrl-b %`将当前窗格左右平分为两个窗格。

切换窗格：使用快捷键`Ctrl-b Up`可以切换到当前窗格“上”方向的窗格，“下/左/右”同理。也可以使用快捷键`Ctrl-b q`提示当前窗口各个窗格的编号，在编号显示时，按下对应的数字，如`0`，即可切换到对应窗格。

调整窗格的大小：切换到对应窗格后，使用快捷键`Ctrl-b-Up`将窗格向“上”拉，“下/左/右”同理。或者可以使用`Ctrl-b Space`切换不同的布局。

聚焦到当前窗格：聚焦到当前窗格后，当前窗格会占满整个终端程序。使用快捷键`Ctrl-b z
`可以聚焦或取消聚焦到当前窗口。

在所有窗格同步输入：使用快捷键`Ctrl-b :`输入命令`setw synchronize-panes`。

关闭窗格：在窗格内显式输入`exit`或按下`Ctrl-d`，或使用快捷键`Ctrl-b x`关闭当前窗格。

经过以上的尝试，对于如何在tmux中操作窗格就有基本的了解了，接下来尝试对窗口的操作。

## 窗口Window
还是使用`tmux`命令进入tmux，然后尝试创建窗口、重命名窗口、切换窗口和关闭窗口。

创建窗口：使用快捷键`Ctrl-b c`创建窗口。

重命名窗口：使用快捷键`Ctrl-b ,`重命名当前窗口。重启

切换窗口：使用快捷键`Ctrl-b p`切换到前一个窗口或`Ctrl-b n`切换到下一个窗口，也可
以使用快捷键`Ctrl-b Num`切换到对应数字的窗口，比如`Ctrl-b 1`切换到编号为1的窗口。

关闭窗口：使用快捷键`Ctrl-b &`关闭窗口。

经过以上的尝试，窗口的基本操作也有所了解了，接下来会对会话做解释。

## 会话Session
先前使用的`tmux`命令，就是使用默认的会话名称（数字）创建了会话。可以通过`tmux new -s session_name`创建指定名称的会话。接下来尝试脱离、重新进入、重名杀死会话等操作。

脱离当前会话：使用快捷键`Ctrl-b d`脱离当前会话。命令行会提示`[detached (from session session_name)]`

进入会话：`tmux attach -t session_name`。

列出所有tmux会话：在终端中输入`tmux list-sessions`，也可以简写为`tmux ls`。

重命名会话：`tmux rename-session [-t target-session] new-name`。

杀死会话：`tmux kill-session -t session_name`。使用`tmux kill-ses -a`杀死除当前会话外的所有会话。

## 安装Tmux Resurrect以保存tmux环境。

首先安装[`Tmux Plugin Manager`](https://github.com/tmux-plugins/tpm)，然后配置[`Tmux Resurrect`](https://github.com/tmux-plugins/tmux-resurrect)插件。

使用快捷键`Ctrl-b Ctrl-s`保存当前环境，`Ctrl-b Ctrl-r`恢复上次保存的环境。

## 推荐资源：
[Tmux Cheat Sheet & Quick Reference](https://tmuxcheatsheet.com/)