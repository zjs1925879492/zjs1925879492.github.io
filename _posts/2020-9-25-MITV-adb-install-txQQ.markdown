---
layout: post
title:  "小米电视adb安装腾讯QQ"
date:   2020-9-25 20:21:24 +0800
categories: Android
tags: Android 小米电视 ADB
img: 
author: Xiang
describe: 你可能永远也想不到，有个人闲的无聊在电视上安装手机QQ 
---

> 小米电视是Android系统并支持adb连接，所以一个大胆的想法在巷子脑海里浮现了！！！<br>使用adb为小米电视安装本不能正常安装的应用！<br>[如何在小米电视上开启adb调试](https://blog.csdn.net/qq_46922792/article/details/107830176)<br>[如何安装adb——安卓调试桥](https://www.bilibili.com/video/av95334789)

## 在电脑上下载QQ安装包
[QQ手机版下载官网](https://im.qq.com/download/)

将apk安装包下载至本地

## adb连接小米电视
win+r运行cmd

输入```adb connect 小米电视内网ip```即可

## adb远程安装QQ
cd到安装包的下载目录

`adb install QQ安装包名.apk`

等待出现success字样即可

此时去遥控器操作小米电视，进入我的应用，即可看到QQ

## 结语
仅仅把QQ安装上是无法操控的（至少无法进行遥控器操作~~adb shell input tap除外~~

若想要遥控操作，得先让巷子瞅瞅小米电视遥控SDK开发文档

但是目前超出巷子的能力范围了

**……**