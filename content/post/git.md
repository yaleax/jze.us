---
title: Github或 Git命令使用
date: 2019-11-17T11:02:02.027Z
lastmod: 2019-11-17T11:02:04.017Z
tags:
  - GitHub
categories:
  - 工具分享
---
## 前言
使用了Hugo静态博客后，才开始正式使用GitHub，经过一段时间的使用，发现GitHub真好用，现在把一些关键信息记录下来。

## GitHub

### 1.生成密钥
生成密钥后，需要把密钥复制到GitHub的 SSH keys里

```
ssh-keygen -t rsa -C "`此处填写你的邮箱地址`"
```
### 2.初始化
进入想建立 Git 的文件夹
```
git init
git add .
git commit -m "first commit"
git remote add origin git@github.com:yaleax/jze.us.git #请更换城你自己的仓库
git push -u origin master
```
### 3. 推送更新到远程 GitHub仓库

```
git add <修改的文件>
git commit -m "填写更新备注"
git push
```
### 4. 下载远程 GitHub 仓库的更新
```
git pull
```

### 5. 生成页面然后上传到 GitHub仓库

```
hugo -D
git add .
git commit -m "update"
git push
```

### GitHub命令速查表

![](/img/git.png)



