---
layout: post
title:  "Windows 窗口句柄实战 Python脚本自动发送信息——维持QQ群聊炽焰"
date:   2020-9-7 00:54:16 +0800
categories: Python
tags: Python 脚本 自动化 Windows 
img: https://s1.ax1x.com/2020/09/13/w0zbWT.jpg
author: Xiang
describe: QQ龙王抢不到，群聊炽焰总是断断续续怎么破？放心，巷子这里有好康的
---

> 又是一年开学季，有多少学子被迫囚禁了一星期/一个月<br>无法与外界通信<br>本来的龙王标识&群聊炽焰拱手他让<br>是多么不甘，却又无奈啊

所以，在我也有这个自动挂机发送脚本的需求下，我开发出了一款能自动发送文字的QQ脚本

~~webQQ早凉透了，各大QQ机器人也差不多都凉了，所以只有这个方法能实现需求了~~

~~代码较乱，但简单粗暴，一看就懂~~

## 代 码 详 解 
*依赖于pywin32，请记得`pip install pywin32`*

- 实现思路：<br>操作windows的剪贴板，定时按句柄调出QQ聊天页面并粘贴文字发送（简单粗暴）

1. 第一段代码：写入windows剪贴板函数
```
def setText(aString):
    '''将要发送的文字复制'''
    w.OpenClipboard()
    w.EmptyClipboard()
    w.SetClipboardData(win32con.CF_UNICODETEXT, aString)
    w.CloseClipboard()
```
非常滴通俗易懂

2. 第二段代码：粘贴并按下回车发送
```
def send_Mess(hwnd):
    '''粘贴并回车发送'''
    win32gui.PostMessage(hwnd,win32con.WM_PASTE, 0, 0)
    time.sleep(0.3)
    win32gui.PostMessage(hwnd,win32con.WM_KEYDOWN,win32con.VK_RETURN,0)  
    win32gui.PostMessage(hwnd,win32con.WM_KEYUP,win32con.VK_RETURN,0)
```
其中hwnd参数是传入的windows窗口句柄
<br>一般情况下，脚本会自动寻找QQ聊天窗口的句柄<br>
3. 第三段代码：脚本主体
<br>

```
windowtitle = '生产龙王无限公司'        #窗口标题，修改成你QQ群聊的名字（注意！！！打开多个聊天窗口时标题会变成xx等x个会话）
hwnd = win32gui.FindWindow(None, windowtitle)         #按窗口标题寻找窗口句柄
while True:
    if hwnd>0:
        print('找到%s'%windowtitle)
        now= time.strftime('%Y-%m-%d %H:%M:%S',time.localtime(time.time()))            #此条信息发送的时间
        setText('定时发送信息（维持群聊炽焰） 测试时间：'+now)
        send_Mess(hwnd)
        time.sleep(3600)       #等待3600秒，即1小时
    else:
        print('没找到%s'%windowtitle)

```

windowtitle是窗口标题，修改为你想发送信息的群聊名称即可

hwnd会按windowtitle寻找句柄

如果hwnd非零则会进行下一步：打印找到xxxx并操作剪贴板并复制
```定时发送信息（维持群聊炽焰） 测试时间：xxxx-xx-xx xx：xx：xx```

然后调起xxxx窗口，并粘贴发送

接下来进入等待时间

等待结束后继续循环发送

即可达到延续群聊炽焰的需求

## 全部代码 

```
#依赖于pywin32库，请记得pip install pywin32

import time
import win32clipboard as w 
import win32gui,win32con

def setText(aString):
    '''将要发送的文字复制'''
    w.OpenClipboard()
    w.EmptyClipboard()
    w.SetClipboardData(win32con.CF_UNICODETEXT, aString)
    w.CloseClipboard()

def send_Mess(hwnd):
    '''粘贴并回车发送'''
    win32gui.PostMessage(hwnd,win32con.WM_PASTE, 0, 0)
    time.sleep(0.3)
    win32gui.PostMessage(hwnd,win32con.WM_KEYDOWN,win32con.VK_RETURN,0)  
    win32gui.PostMessage(hwnd,win32con.WM_KEYUP,win32con.VK_RETURN,0)

windowtitle = '生产龙王无限公司'        #窗口标题，修改成你QQ群聊的名字（注意！！！打开多个聊天窗口时标题会变成xx等x个会话）
hwnd = win32gui.FindWindow(None, windowtitle)         #按窗口标题寻找窗口句柄
while True:
    if hwnd>0:
        print('找到%s'%windowtitle)
        now= time.strftime('%Y-%m-%d %H:%M:%S',time.localtime(time.time()))            #此条信息发送的时间
        setText('定时发送信息（维持群聊炽焰） 测试时间：'+now)
        send_Mess(hwnd)
        time.sleep(3600)       #等待3600秒，即1小时
    else:
        print('没找到%s'%windowtitle)

'''
hwnd_title = dict()
def get_all_hwnd(hwnd,mouse):
    if win32gui.IsWindow(hwnd) and win32gui.IsWindowEnabled(hwnd) and win32gui.IsWindowVisible(hwnd):
        hwnd_title.update({hwnd:win32gui.GetWindowText(hwnd)})
win32gui.EnumWindows(get_all_hwnd, 0)
   
for h,t in hwnd_title.items():
    if t is not "":
        print(h, t)
'''
#如果你仍然没有成功获得窗口句柄，可以使用此段代码打印出当前所有窗口标题名与句柄
```

复制粘贴即可完美运行

## 备注（一定要看）

当你的聊天窗口打开了多个会话时，其窗口标题会变为当前群聊名称等当前群聊数量个会话

例：我打开了5个群聊一个好友聊天，我现在打开的是五个群聊之中的一个名为巷子的粉丝群，那么其窗口标题则会变为“**巷子的粉丝群等6个会话**”

如图所示

![w0xiAx.png](https://s1.ax1x.com/2020/09/13/w0xiAx.png)

所以我建议只保留一个会话，否则尽量不要修改windowtitle


若脚本自动寻找句柄的代码不正常工作，你可以运行
```
hwnd_title = dict()
def get_all_hwnd(hwnd,mouse):
    if win32gui.IsWindow(hwnd) and win32gui.IsWindowEnabled(hwnd) and win32gui.IsWindowVisible(hwnd):
        hwnd_title.update({hwnd:win32gui.GetWindowText(hwnd)})
win32gui.EnumWindows(get_all_hwnd, 0)
   
for h,t in hwnd_title.items():
    if t is not "":
        print(h, t)
```
它会输出所有窗口标题和窗口句柄，一一对应

当把等待时间设置的够低时，你甚至可以抢到龙王

按道理来说本脚本适用于所有能回车发送消息的聊天软件