---
layout: post
title:  "ssh免密码登录"
date:   2020-10-2 01:44:02 +0800
categories: 常用 备忘录
tags: Linux ssh rsa
img: 
author: Xiang
describe: 使用rsa密钥对来进行ssh免密登录
---

`ssh-keygen`

一路回车

之后

`ssh-copy-id username@ip`

输入对应用户的密码即可

`ssh username@ip`

来测试是否成功

[非常有用的ssh命令](https://blog.csdn.net/alifrank/article/details/48241699)