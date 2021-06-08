---
title: windows系统安装
top: false
cover: false
toc: true
mathjax: true
date: 2021-06-07 23:04:55
password:
summary:
tags: windows系统安装
categories: 教程
---

# 一、安装系统的准备阶段
+ 最好是8G以上的U盘
+ 系统镜像文件[windows10全](http) 链接暂时不能分享
+ 软件工具[UltraISO](http) 链接暂时不能分享
## 1、安装UltraISO
基本上是一直默认点下一步

![UltraISO安装1](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%851.png)
![UltraISO安装2](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%852.png)
![UltraISO安装3](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%853.png)
![UltraISO安装4](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%854.png)
![UltraISO安装5](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%855.png)
![UltraISO安装6](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%856.png)
![UltraISO注册](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%857.png)
点击输入注册码，来源网上分享

```
用户名：王涛
注册码：7C81-1689-4046-626F
```
成功后再次打开软件，出现这个画面就成功了
![UltraISO安装](http://qu24y78fl.hn-bkt.clouddn.com/windows%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%858.png)

## 2、制作U盘为启动盘
将U盘插入电脑，注意：**接下来的操作会清空U盘所有文件**
打开UltraISO，依次执行：

点击文件，打开

![打开ISO文件](http://qu24y78fl.hn-bkt.clouddn.com/%E6%89%93%E5%BC%80ISO%E6%96%87%E4%BB%B6.png)

选择对应的windows ISO文件

![选择ISO文件](http://qu24y78fl.hn-bkt.clouddn.com/%E9%80%89%E6%8B%A9ISO%E6%96%87%E4%BB%B6.png)

![选择ISO文件](http://qu24y78fl.hn-bkt.clouddn.com/%E9%80%89%E6%8B%A9ISO%E6%96%87%E4%BB%B62.png)

点击启动，写入硬盘镜像

![写入硬盘映像](http://qu24y78fl.hn-bkt.clouddn.com/%E5%86%99%E5%85%A5%E7%A1%AC%E7%9B%98%E6%98%A0%E5%83%8F.png)

选择对应的U盘

![选择U盘](http://qu24y78fl.hn-bkt.clouddn.com/%E9%80%89%E6%8B%A9U%E7%9B%98.png)

点击写入，将会清空U盘

![写入U盘](http://qu24y78fl.hn-bkt.clouddn.com/%E5%86%99%E5%85%A5U%E7%9B%98.png)

等待写入完毕

# 二、安装windows系统
## 1、进入BIOS
不同厂家的电脑进入方式不一致，下面列举出一些常见的，如果不行，直接百度查
开机时按： ESC、F2、F8、F12、Delete，其中之一（建议不明白具体那个键时，都疯狂按）

用方向键选择boot，找到U盘并设置优先级最高。按F10保存退出。

重启即可进入系统安装。

系统安装完成后拔下U盘，重新启动

进入系统后，右键点击此电脑，选择管理：
![管理](http://qu24y78fl.hn-bkt.clouddn.com/%E6%AD%A4%E7%94%B5%E8%84%91.png)

选择磁盘管理，对磁盘进行分区（我这电脑已经分好）

![](http://qu24y78fl.hn-bkt.clouddn.com/%E7%A3%81%E7%9B%98%E7%AE%A1%E7%90%86.png)

选择压缩卷

![压缩卷](http://qu24y78fl.hn-bkt.clouddn.com/%E5%8E%8B%E7%BC%A9%E5%8D%B7.png)

然后输入卷的大小，即可（以M为单位）

## 2、常用软件安装
直接双击.exe文件，运行即可。但是这些软件默认是安装在C盘，需要修改安装到其他盘里面。
软件都会占用C盘的空间，需要修改软件的缓冲位置，文件的下载保存位置

