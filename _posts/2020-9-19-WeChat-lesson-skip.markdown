---
layout: post
title:  "微信内置JavaScript调试台跳过青年大学习团课"
date:   2020-9-19 13:33:02 +0800
categories: 常用
tags: JavaScript 前端
img: https://s1.ax1x.com/2020/08/17/dnKew6.png
author: Xiang
describe: 记录方法，以备自己以后用到 
---


> 团课教育很重要！必须要好好学，不可投机取巧，此方法仅用学习分享

## 打开微信内置JavaScript调试台

```
debugmm.qq.com/?forcex5=true 
http://debugtbs.qq.com 
http://debugx5.qq.com
```

在微信里分别打开这几个网址

在第三个网址中启用vconsole调试选项

![w54lbF.png](https://s1.ax1x.com/2020/09/19/w54lbF.png)

启用后会发现右下角有绿色长方形控制台图标

点开即是内置JavaScript控制台

## JavaScript代码调整视频时间

1. 转到青年大学习

2. 签到

3. 等待播放视频

4. 在视频播放时，打开vconsole控制台输入```document.getElementById('Bvideo').currentTime=此视频时长秒数```
其中此视频时长秒数据实际填写

5. 答题

6. 完成学习

## 备注

若需要截屏，防止引起怀疑

可以把右下角的绿色框框截掉

或输入```vconsole.style.display="none"```
暂时隐藏