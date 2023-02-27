---
title: ssh
date: 2023-02-26 15:36:04
tags:
---

## 生成ssh key

1. 生成秘钥

``` bash
$ ssh-keygen -t rsa -C "xxxx@xxxx.com"
```
2、查看密钥

``` bash
$ cat /root/.ssh/id_rsa.pub
```
