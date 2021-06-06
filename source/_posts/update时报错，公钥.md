---
layout: apt
title: update时报错，公钥
date: 2021-06-02 20:59:09
tags: method
categories: 问题-解决
---
**sudo apt-get update报错，NO_PUBKEY F42ED6FBAB17C654**

由于没有公钥，无法验证下列签名

解决方案
打开终端，去下载公钥：

```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F42ED6FBAB17C654

```

其他的公钥有问题，则替换相应的公钥
