---
layout: post
title:  "TF外置储存卡融合本机ROM"
date:   2021-9-11 19:24:31+0800
categories: Android
tags: Android
img: 
author: Xiang
describe: 存储空间不够用，但是储存卡却只能储存视频照片之类的，面对打应用还是派不上用场……
---

手机：华为荣耀9（备用机）
系统 Android9 EMUI9

华为的EMUI阉割过的系统无法使用Android自带的“将应用移至SD卡”（据说是Android6以上的版本移除了功能），华为的系统也出了名的严格，几乎找不到破解的方法……

其他厂商如一加，小米等刷机方便的系统还好，可以root之后强制操作……

我探索到两条路，几乎都是使用ADB命令实现的……

## ADB直接将SD卡与ROM融合

1. ADB 手机连接电脑

2. 输入命令adb shell sm list-disks

3. 将回显中的数字记录，如179,384等

4. adb shell sm partition disk:179,384 private

5. 将上方命令中的179,384替换成你记录下的数字

6. 等待命令执行完成

- 优点： 无论什么手机都可以用这个方法强制融合成功

- 缺点： 极其不稳定，我试了之后所有安装的APP打开全部闪退，桌面出现两个相同图标，adb monitor查看所有安装的应用全部报错

不排除SD卡本身的问题，垃圾朗科64g标u3实际速度16mb都跑不到

#ADB曲线救国法

无意间翻Google ADB DOCs翻到的

[文档链接](https://developer.android.google.cn/studio/command-line/adb#pm)

如图

[![hzHcoq.png](https://z3.ax1x.com/2021/09/11/hzHcoq.png)](https://imgtu.com/i/hzHcoq)

首先
`adb shell pm get-install-location`

此命令可以获取到安装位置

我显示的是0

然后 `adb shell pm set-install-location `更改默认安装位置

之后再用`adb shell pm get-install-location`
检测是否修改成功即可

不出所料，我失败了

……

但是[![hzbikt.png](https://z3.ax1x.com/2021/09/11/hzbikt.png)](https://imgtu.com/i/hzbikt)

我们还可以在安装时进行选择……

注意！当使用pm安装APP时，需要将apk文件下载到手机在使用命令安装

我测试时报错找不到对应的APK包，但是路径没有输错，不知道什么问题……

### 没辙了

华为系统设置中 储存一项里可以更改默认储存位置……

可以把默认储存位置改到SD卡，设置完成后手机会重启，之后一部分APP缓存似乎可以放到SD卡里了，也算个成功吧

忙碌了一整天的巷师傅选择了最简单粗暴的方法……

收工！走！