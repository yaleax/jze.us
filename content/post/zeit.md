---
title: "Zeit反代 v2ray 加速"
date: 2020-03-22T23:08:34+08:00
draft: true
---

### 1.注册 zeit帐号

可以[https://zeit.co/](https://zeit.co/)官网直接使用 github帐号登录

### 2. 在电脑上登录 zeit

安装Now CLI命令行工具并登录，需要nodejs运行环境 参考官方文档 https://zeit.co/docs

```bash
npm i -g now
now login
```

### 3.在电脑上新建一个文件夹

可以把 proxy 改成自己想要的名字

```bash
mkdir proxy
cd proxy
```

### 4.编辑now.json文件，写入以下内容，相关内容改成你自己的

```bash
nano now.json
```

```json
{
  "name": "你的应用名字",
  "version": 2,
  "routes": [
    {"src": "/$1(.*)","dest": "https://这里中文替换成上面的域名/$1"}
  ]
}
```

### 5.上传

```bash
now --prod
```

-----

[参考]：[https://mjjj.run/archives/44.html](https://mjjj.run/archives/44.html)

