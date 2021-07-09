---
title: 解决删除git远程分支后依然存在的问题
top: false
cover: false
toc: true
mathjax: true
date: 2021-06-10 17:22:44
password:
summary:
tags: git
categories: knowledge
---

# 删除本地和云端分支，解决删除git远程分支后依然存在的问题

## 1、删除`dev_test`分支，先切换到其他的分支上(如，master)

```c++
git checkout master
```

## 2、删除本地分支

若已经merge，则:

```c++
 git branch -d dev_test
```

强制删除分支，则:

```c++
 git branch -D dev_test
```

## 3、删除远程分支（谨慎！！）

```c++
git push origin --delete dev_test
```

## 4、查看分支
```c++
git branch -a
```

如果依然还是有这个远程分支，则：

```c++
git remote show origin //查看remote地址，远程分支，以及是否已经删除等信息

git remote prune origin // 删除不存在的分支
```

OJBK
