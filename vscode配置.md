<!--
 * @Description: 
 * @Author: luoxu
 * @Date: 2022-07-10 22:33:08
 * @LastEditTime: 2022-07-14 21:02:07
 * @LastEditors: luoxu
 * @Reference: 
-->
## 自动添加头部消息
## 快捷键设置
设置多光标插入快捷键为：Ctrl+单击，解决办法:在setting.json中添加一行"editor.multiCursorModifier": "ctrlCmd"

另外所有用户设置的快捷键都会在keybinding.json中记录，如果有的快捷键命令在某个系统上没有，可以参考另外一个操作系统写入该文件中，比如jeston中没有cursorUp等
## 自动格式规范

## 配置C/C++的调试环境
**方式一：手动配置**
launch.json文件
```bash
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "g++ - 生成和调试活动文件",
            "type": "cppdbg",
            "request": "launch",
            "program": "${fileDirname}\\${fileBasenameNoExtension}",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${fileDirname}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "/usr/bin/gdb",
            "setupCommands": [
                {
                    "description": "为 gdb 启用整齐打印",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                },
                {
                    "description": "将反汇编风格设置为 Intel",
                    "text": "-gdb-set disassembly-flavor intel",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "C/C++: g++ 生成活动文件"
        }
    ]
}
```


task.json文件：launch.json文件调用此文件做一个预任务，即生成可执行文件
```bash
{
    "tasks": [
        {
            "type": "cppbuild",
            "label": "C/C++: g++ 生成活动文件",
            "command": "/usr/bin/g++",
            "args": [
                "-fdiagnostics-color=always",
                "-g",
                "${file}",
                "-o",
                "${fileDirname}/${fileBasenameNoExtension}"
            ],
            "options": {
                "cwd": "${fileDirname}"
            },
            "problemMatcher": [
                "$gcc"
            ],
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "detail": "调试器生成的任务。"
        }
    ],
    "version": "2.0.0"
}
```

**方式二：自动生成**
这种方法是否生效取决于C/C++扩展的版本，有时候最新的版本并不能自动适配成功，将版本回退一下就可以。
1、扩展1.9.8：新建.c或.cpp的文件，就可以自动生成.vscode/c_cpp_properties.json、.vscode/settings.json、.vscode/tasks.json三个文件
2、点击最左侧的运行与调试的图标（虫子图标）或者直接f5（两种方法选其一），会出来launch.json文件的配置选择，
(1)点击最左侧的运行与调试的图标（虫子图标）：
a.create a launch.json file 
b.选择环境：c++(GDB/LIDB)
c.选择配置:g++-生成和调试活文件（不同机器上显示不一样，先选一个跟g++相关的，这样才能生成大致的模板，后续再手动参照方式1改一些参数也可）
(2)直接f5(这种情况下一般是点击最左侧的运行与调试的图标没有create a launch.json file ),会自动提示要创建launch.json文件，步骤与上面的b,c两步差不多

**总结**：
选择环境与选择配置上的差异跟vscode以及自带插件的版本还有类型有关