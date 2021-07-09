---
title: vscode_ros_gdb
top: false
cover: false
toc: true
mathjax: true
date: 2021-07-09 16:14:53
password:
summary:
tags: vscode ros gdb
categories: knowledge
---

# 总结

１．在命令行执行命令：　　catkin_make -DCMAKE_EXPORT_COMPILE_COMMANDS=Yes
２．在c_cpp_properties.json文件添加一行：　"compileCommands": "${workspaceFolder}/build/compile_commands.json"
３．生成task.json文件　通过Ctrl+shift+P按键
４．在launch.json中更改可执行文件路径，即更改“program”项（需二进制可执行文件）
５．在launch.json中添加一行：　"preLaunchTask": "catkin_make", / 这个重要，需要与task中的label相同
６.在CMakeLists.txt文件中添加一行：　SET(CMAKE_BUILD_TYPE Debug)

[csdn上大佬的教程](https://blog.csdn.net/ABC_ORANGE/article/details/102665792)

c_cpp_properties.json ，主要修改includePath

~~~
{
    "configurations": [
        {
            "browse": {
                "databaseFilename": "",
                "limitSymbolsToIncludedHeaders": true
            },
            "includePath": [
            	"${workspaceFolder}/**"
            ],
            "name": "ROS",
            "intelliSenseMode": "gcc-x64",
            "compilerPath": "/usr/bin/gcc",
            "cStandard": "c11",
            "cppStandard": "c++17",
            "compileCommands": "${workspaceFolder}/build/compile_commands.json"
        }
    ],
    "version": 4
}

~~~

task.json

~~~
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "catkin_make", //代表提示的描述性信息
            "type": "shell",  //可以选择shell或者process,如果是shell代码是在shell里面运行一个命令，如果是process代表作为一个进程来运行
            "command": "catkin_make",//这个是我们需要运行的命令
            "args": [],//如果需要在命令后面加一些后缀，可以写在这里，比如-DCATKIN_WHITELIST_PACKAGES=“pac1;pac2”
            "group": {"kind":"build","isDefault":true},
            "presentation": {
                "reveal": "always"//可选always或者silence，代表是否输出信息
            },
            "problemMatcher": "$msCompile"
        }
    ]
}

~~~

launch.json，主要修改program可执行文件路径

~~~
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb) Launch",　　 // 配置名称，将会在调试配置下拉列表中显示
            "type": "cppdbg",　　　// 调试器类型 该值自动生成
            "request": "launch",　　 // 调试方式,还可以选择attach
            "program": "${workspaceFolder}/devel/lib/smart_car/smart_car",　　//要调试的程序（完整路径，支持相对路径）
            "args": [],　// 传递给上面程序的参数，没有参数留空即可
            "stopAtEntry": false,　// 是否停在程序入口点（停在main函数开始）
            "cwd": "${workspaceFolder}",　// 调试程序时的工作目录
            "environment": [],//针对调试的程序，要添加到环境中的环境变量. 例如: [ { "name": "squid", "value": "clam" } ]
            "externalConsole": false, //如果设置为true，则为应用程序启动外部控制台。 如果为false，则不会启动控制台，并使用VS Code的内置调试控制台。
            "MIMode": "gdb",　 // VSCode要使用的调试工具
            "preLaunchTask": "catkin_make", / 这个重要，需要与task中的label相同
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ]
        }
    ]
}

~~~

