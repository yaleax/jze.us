---
title: "Filebrowser"
date: 2019-12-04T11:42:12+08:00
draft: true
---
### 简介
File Browser 是一个基于 Web 的文件管理器。它可以使你随时随地的对设备的文件进行基本的管理操作，如：创建、删除、移动、复制等。它除了可以让你进行文件管理之外，还有一些其他的功能。它支持多个用户的管理，而且每个用户可以拥有自己可以访问的文件和权限。它还支持文件分享，就行网盘那样，你可以通过它来向你的朋友分享文件。你还可以用它来执行一些 Linux 命令，比如你想要在当前目录下克隆一个代码库，就可以用它来执行git等命令。

### 1.安装 Filebrowser

```bash
curl -fsSL https://filebrowser.xyz/get.sh | bash
```

安装目录：`/usr/local/bin/filebrowser`

### 2.创建 Filebrowser配置文件

```bash
mkdir /etc/filebrowser
mkdir /etc/filebrowser/filebrowser
nano /etc/filebrowser/filebrowser.json
```

### 3.配置文件

```bash
{
  "port": 18888,
  "baseURL": "/admin", //后缀名字例如：www.yale.ga/admin
  "address": "0.0.0.0",
  "log": "stdout",
  "database": "/var/www/yale/database.db", //数据存放地址
  "root": "/var/www/yale"  //你想管理的目录
}
```



### 4.设置系统服务

```bash
nano /etc/systemd/system/filebrowser.service
```

### 5.系统服务配置文件

```bash
[Unit]
Description=File Browser
After=network.target

[Service]
ExecStart=/usr/local/bin/filebrowser -c /etc/filebrowser/filebrowser.json

[Install]
WantedBy=multi-user.target

```

### 6.重新载入 system

```bash
systemctl daemon-reload
```

### 7.服务管理

```bash
状态：systemctl status filebrowser
启动：systemctl start filebrowser
停止：systemctl stop filebrowser
重启：systemctl restart filebrowser
```
### 8.登录地址
http://你的ip:1888/admin   
帐号:`admin`  
密码:`admin`  

### 9.启动 https
启动 https后面会介绍，利用 Caddy 反代,添加一句，后面 Caddy 配置文件我会加进去。  
`proxy /admin 127.0.0.1:18888`

### 10.通过 caddy 建立 ssl

```bash
www.yale.ga
{
  gzip
  tls 123456212@mail.com
  log /var/log/caddy/access.log
  root /var/www/yale/public
  proxy /admin 127.0.0.1:18888 \\反代 filebreowser

}
```
-----
[参考1]<https://ljc.space/post/website-caddy-hugo-filebrowser/>  
[参考2]<https://233blog.com/post/26/>  
[参考3]<https://www.mivm.cn/filebrowser/>  