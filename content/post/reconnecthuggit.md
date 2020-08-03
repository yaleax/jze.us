---
title: " 让目录重新连接 Github"
date: 2020-07-28T00:07:38+08:00
tags:
  - GitHub
categories:
  - 工具分享
---

### 1.前言

有两台电脑，一台在家，另外一台在公司，通过 Dropbox 可以让两个目录文件一致。如果想上传修改到 Github 还需要重新连接一下。这个教程的前提是，你已经复制了id_rsa.pub文件到正确的位置。

### 2.获得当前目录Github 地址

```bash
git config -l | grep url
```

你将获得类似下面这样的地址，复制后面的: `yaleax/jze.us.git`

`remote.origin.url=https://github.com/yaleax/jze.us.git`

### 3.重新连接目录到 Github

```bash
git remote set-url origin git@github.com:yaleax/jze.us.git
```

完成，祝你好运。

