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

**安装Jsoncpp**

```c++
sudo apt-get install libjsoncpp-dev
```

静态库在系统：/usr/include；动态库在：/usr/lib/x84_64-linux-gnu ;在动态库里面会有libjsoncpp.a文件

在g++编译文件时，需要使用动态库;否则出现:`undefined reference to json::value`
需要将CmakeList.txt 修改：

```c++
target_link_libraries(${PROJECT_NAME}_node

   ${catkin_LIBRARIES}
                      
   jsoncpp
)
```

**Jsoncpp的使用**

头文件：

```c++
#include <jsoncpp/json/json.h> 
//#include "json/json.h"
```

Json::Value可以表示任一种数据类型

使用Json::Reader对Json文件进行解析：

```c++
#include <jsoncpp/json/json.h>
#include <fstream>
#include <std_msgs/String.h>
```



```c++
Json::Value root;
Json::StyledWriter s_writer;
Json::Value data;
ofstream ofs;

data["x"] = 123.4;
data["y"] = 234.5;
root["center_point"] = data;
sprintf(image_dst_file, "/home/xx/Pictures/maps/%d/%d.json", map_id, clean_area_id);
//ofs.open("/home/xx/Pictures/maps/5825655/25813.json");
ofs.open(image_dst_file);  //  image_dst_file表示.json文件名  char数组保存文件名
ofs << s_writer.write(root);
ofs.close();
```

结果：
```
{
   "center_point" : {
      "x" : 12.034999847412109,
      "y" : 14.795000076293945
   }
}
```

CSDN上有个大佬写的博文，[Json的使用方法](https://blog.csdn.net/yc461515457/article/details/52749575?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromMachineLearnPai2%7Edefault-1.control#commentBox)


