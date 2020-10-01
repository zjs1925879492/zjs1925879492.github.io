---
layout: post
title:  "ssh连接失败——公钥改变"
date:   2020-10-2 01:44:02 +0800
categories: 常用 备忘录
tags: Linux ssh rsa
img: 
author: Xiang
describe: 换系统导致的公钥变更，ssh连接报错
---

## 起因
> 换了个系统，ssh发现连接不上，报<br>```WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!……man-in-the-middle attack……It is also possible that the RSA host key has just been changed……Host key verification failed.```

**粗略翻译一下就是**：

远程主机认证被更改

中间人攻击或rsa认证公钥改变

主机密钥认证失败

## 解决方法
如果确定100%不是中间人攻击的话
`ssh-keygen -R 要连接的主机的IP`

输入yes 即可

之后`ssh user@ip`

输入yes

输入密码即可登录