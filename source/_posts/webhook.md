---
title: webhook
date: 2023-02-26 15:39:44
tags:
---

## 自动化部署

因为webhook是Go语言开发的，所以要先安装Go语言。

``` bash
$ yum install -y golang
```
然后就可以用go命令安装webhook了。

``` bash
$ go install github.com/adnanh/webhook@latest
```
新手在玩go的时候 编译或者安装插件的时候会提示：

go get: module github.com/rogpeppe/godef: Get "https://proxy.golang.org/github.com/rogpeppe/godef/@v/list": dial tcp 172.217.160.113:443: connectex: A connection attempt failed because the connected party did not properly respond after a period of time, or established connection failed because connected host has failed to respond.

解决方法：改成我们国内可用的代理地址

在命令提示符输入： go env -w GOPROXY=https://goproxy.cn

使用go env 查看webhook位置

```
[root@VM-16-11-centos ~]# go env
GOOS="linux"
GOPATH="/root/go"
```

```
/root/go/bin/webhook -hooks hooks.json -verbose
```

You can now run webhook using

``` bash
$ /path/to/webhook -hooks hooks.json -verbose
```

[
  {
    "id": "myblog-hook",
    "execute-command": "/scripts/myblog.sh",
    "command-working-directory": "/myProject/scripts"
  }
]

部署脚本编写

``` bash

#!/bin/bash

cd /home/www/website

if [ ! -d "go-home" ]; then
  git clone https://github.com/pingyeaa/go-home.git
fi

cd go-home
git pull

```

##webhook配置与启动

编写配置文件hooks.json，格式如下。

chmod a+x block.sh 文件授权

https://github.com/adnanh/webhook

http://124.222.170.102:9000/hooks/myblog-hook