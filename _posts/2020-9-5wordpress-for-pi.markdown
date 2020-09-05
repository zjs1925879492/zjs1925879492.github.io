---
layout: post
title:  "树莓派搭建LAMP环境并部署WordPress博客网站"
date:   2020-8-20 09:47:41 +0800
categories: 树莓派
tags: 树莓派 建站 WordPress
img: https://s.w.org/images/home/screen-themes.png
author: Xiang
describe: 在arm64架构的树莓派上安装LAMP环境并部署WordPress
---

##安装 LAMP依赖
1. 
`sudo apt-get install php php-mysql php-gd apache2`
安装Apache，PHP
![wAxz6S.png](https://s1.ax1x.com/2020/09/05/wAxz6S.png)
等待安装完成
![wAzCwj.png](https://s1.ax1x.com/2020/09/05/wAzCwj.png)
`sudo service apache2 start`启用Apache
浏览器输入树莓派的内网ip~~(本人有公网IP和ddns网址故从外网访问)~~
若看到如下界面即为Apache安装成功
![wAzDht.png](https://s1.ax1x.com/2020/09/05/wAzDht.png)

2. 
	sudo touch /var/www/html/testphp.php
    sudo vim /var/www/html/testphp.php
    输入<?php phpinfo();?>
	esc+:wq保存并退出
浏览器输入树莓派的内网ip并加+`testphp.php`查看php是否安装成功
如图，即为成功
![wESiuD.png](https://s1.ax1x.com/2020/09/05/wESiuD.png)

3. 安装mariadb
`sudo apt -y install default-mysql-client default-mysql-server`将会安装mariadb~~因为MySQL已经被mariadb替代并放弃支持~~

如图即为成功
![wE9aBF.png](https://s1.ax1x.com/2020/09/05/wE9aBF.png)

`sudo mysql -u root -p`会进入数据库配置命令行
`create database wordpress;`在命令行内输入会新建一个名为wordpress的数据库

4. 下载WordPress
[WordPress中文官网](https://cn.wordpress.org "官网")
`cd /var/www &&sudo wget https://cn.wordpress.org/latest-zh_CN.tar.gz`下载gz包
`sudo tar zxvf latest-zh_CN.tar.gz`解压
`sudo rm -rf html`删除Apache的默认html文件
`sudo mv wordpress html`将解压的WordPress目录改为html
即可访问WordPress界面
![wEkaFg.png](https://s1.ax1x.com/2020/09/05/wEkaFg.png)
点击“现在就开始”
会跳转到此界面以修改配置文件
![wEkDln.png](https://s1.ax1x.com/2020/09/05/wEkDln.png)

确认数据后点击提交
![wEkoOx.png](https://s1.ax1x.com/2020/09/05/wEkoOx.png)
跳转到此界面，不用担心，给予权限即可
`sudo chmod -R 777 /var/www`

之后便可完成配置
![wEkz6I.png](https://s1.ax1x.com/2020/09/05/wEkz6I.png)
点击“现在安装”

之后按照个人需求填写站点标题，邮箱，密码等

然后跳转到站长登录页，填写邮箱或用户名和密码即可登录后台
![wEEQKI.png](https://s1.ax1x.com/2020/09/05/wEEQKI.png)

至此，WordPress成功安装
