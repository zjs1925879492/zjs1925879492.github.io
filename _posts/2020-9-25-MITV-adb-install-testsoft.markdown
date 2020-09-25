---
layout: post
title:  "小米电视adb安装鲁大师跑分测试软件"
date:   2020-9-25 20:21:17 +0800
categories: Android
tags: Android 小米电视 ADB 测评
img: 
author: Xiang
describe: 你可能永远也想不到，有个人闲的无聊在电视上安装跑分软件测试处理器性能
---

> 普通人买电视看的应该是屏幕和分辨率吧，~~很少有人注意性能？~~ 屑巷子不仅要安装安兔兔，还要在小米电视上跑分（手动滑稽）

## 安装方法
安装方法约同此篇一样：[在小米电视上安装QQ]()

## 实际操控
怎么可能用遥控器控制呢？？？

adb提供了模拟触摸函数input tap

用法`adb shell input tap x y`

模拟点击屏幕上xy坐标的位置

具体数值根据实际情况，可能略有不同