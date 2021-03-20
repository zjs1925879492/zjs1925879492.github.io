---
layout: post
title:  "电脑使用手机免费代理上网"
date:   2021-2-25 10:52:03 +0800
categories: VPN
tags: Android VPN Network
img: https://s1.ax1x.com/2020/09/26/0Pdomd.png
author: Xiang
describe: 手机上有些免费的代理软件还挺好用，电脑上却很少，巷子找到了电脑白嫖手机vpn的方法 
---

> 手机上有很多免费的代理软件，如某王，某王也自带有连线码，只不过连线码vmess服务器是不是抽风，不是特别好用

所以巷子就在想：能不能共享手机上的网络让电脑科学上网呢

答案是**可以**

## 实现思路
实现目标的大致思路有两种

- **代理模式**
1. 手机创建本地代理服务器
2. 电脑连接手机代理服务器
3. 手机启用VPN
4. 电脑即可共享VPN

- **共享模式**
1. 手机启用VPN
2. 手机开启热点

经测试两种思路都可行

那么现在开始介绍具体方法

---

## 教程
#### 代理模式
1. 手机下载本地代理软件
如every proxy，v2rayng等
<br>当然有能力也可以自己写，但没必要没事造轮子

2. 在手机上启用本地代理服务器
以every proxy和v2rayng为例

- every proxy
[![yjcfzQ.jpg](https://s3.ax1x.com/2021/02/25/yjcfzQ.jpg)](https://imgtu.com/i/yjcfzQ)

主界面长这样

[![yjc4Mj.jpg](https://s3.ax1x.com/2021/02/25/yjc4Mj.jpg)](https://imgtu.com/i/yjc4Mj)

只需要开启HTTP代理开关即可

[![yjc4Mj.jpg](https://s3.ax1x.com/2021/02/25/yjc4Mj.jpg)](https://imgtu.com/i/yjc4Mj)

可以监控流量，网速等

- v2rayng

[![yjc2i8.jpg](https://s3.ax1x.com/2021/02/25/yjc2i8.jpg)](https://imgtu.com/i/yjc2i8)

主界面长这样

点击左上角打开菜单

[![yjcWRg.jpg](https://s3.ax1x.com/2021/02/25/yjcWRg.jpg)](https://imgtu.com/i/yjcWRg)

如图，选择**设置**

[![yjc5ss.jpg](https://s3.ax1x.com/2021/02/25/yjc5ss.jpg)](https://imgtu.com/i/yjc5ss)

下滑找到 *允许来自局域网的连接*并勾选

#### 共享模式
手机打开热点，开启VPN，电脑连接热点即可

## 连接

以window10为例

右键右下角网络图标，选择 *打开网络和Internet设置*

新窗口中选择代理

[![yvngKI.png](https://s3.ax1x.com/2021/02/25/yvngKI.png)](https://imgtu.com/i/yvngKI)

打开手动代理开关

根据实际情况填写ip及端口号（