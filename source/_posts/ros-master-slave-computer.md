---
title: ros_master_slave_computer
top: false
cover: false
toc: true
mathjax: true
date: 2021-07-09 16:08:58
password:
summary:
tags: master and slave configure
categories: knowledge
---

# 本机（从机）配置

查看本机IP

~~~c++
ifconfig
~~~

我的ip为：

~~~c++
192.168.10.133
~~~

输入

~~~
vim .bashrc
~~~

在末尾添加

~~~
export ROS_HOSTNAME=zsj-pc    // hostname
export ROS_MASTER_URI=http://192.168.10.5:11311 #(主机的ip：11311)
export ROS_IP=192.168.10.133  #(本机的IP)
~~~

其中hostname可在command中输入显示

# 主机（ROS端）配置

输入

~~~
vim .bashrc
~~~

在末尾添加

~~~
export ROS_HOSTNAME=pros-pc    // hostname
export ROS_MASTER_URI=http://192.168.10.5:11311 #(主机的ip：11311)
export ROS_IP=192.168.10.133  #(本机的IP)
~~~

从机的ROS_MASTER_URI需要与主机的ROS_MASTER_URI保持一致

**建议主机从机都要将对方的IP hostname添加到自己的 /etc/hosts 中**，如果不填加，将无法反向控制。

如：主机的hosts文件中没有添加从机的信息，从机只能接收到从主机发来的信息，而无法向主机发送信息

~~~c++
sudo vim /etc/hosts
~~~

eg，在#号上写

```
192.168.10.133  zsj-pc
```







