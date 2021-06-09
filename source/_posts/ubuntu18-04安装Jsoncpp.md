---
title: ubuntu18.04安装Jsoncpp
top: false
cover: false
toc: true
mathjax: true
date: 2021-06-09 15:31:19
password:
summary:
tags: Jsoncpp
categories: 教程
---

[网络资料安装Json](https://blog.csdn.net/qq_32418361/article/details/97391832?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162321023816780255216662%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162321023816780255216662&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~baidu_landing_v2~default-1-97391832.first_rank_v2_pc_rank_v29&utm_term=undefined+reference+to+%60Json%3A%3AValue%3A%3A%7EValue%28%29%27&spm=1018.2226.3001.4187#commentBox)

C++ CMake使用JSONCPP出现undefined reference to json::value解决方法

[Json的使用](https://www.cnblogs.com/kex1n/archive/2011/12/02/2272328.html)

细节[Json的使用方法](https://blog.csdn.net/yc461515457/article/details/52749575?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control#commentBox)

[头文件](https://blog.csdn.net/qq_29627051/article/details/102834030)

CmakeList.txt 修改：

```
```

target_link_libraries(${PROJECT_NAME}_node

   ${catkin_LIBRARIES}

   ${OpenCV_LIBS}

   jsoncpp

 )

```
```

