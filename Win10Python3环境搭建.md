# Win10Python3环境搭建

## 1. 下载安装包

- 1.1 Sublime Text 3 [下载][st3]
- 1.2 Python 3 [下载][py3]

## 2. Sublime Text 3 插件安装

- 2.1 安装 Package Control  
> Tools -> install Package Control

- 2.2 Preferences -> Package Control -> Install Package

> SideBarEnhancements：扩展侧边栏功能  
SublimeCodeIntel：代码自动提示和自动补全插件  
AutoPEP8：按PEP8格式化 python代码 快捷键 Ctrl + Shift +8  
ConvertToUTF8:支持中文GB编码  
localizedMenu:中文插件  
SublimeREPL:文件无法input的问题  
Anaconda:代码提示等许多功能，必备

## 3. 构建配置 Tools-->Build System-->New Build System... 

```
{
"encoding": "utf-8",
"working_dir": "$file_path",
"shell_cmd": "C:/Users/tianjun/python3/python.exe -u \"$file\"", 
"file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
"env": {"PYTHONIOENCODING": "utf8"}, 
"selector": "source.python"
}
```
Ctrl+B执行  

## 4.中文乱码配置

> 安装ConvertToUTF8
File -> Save with Encoding -> UTF8    
File -> Set File Encoding to -> UTF8    
File -> Reload with Encoding -> UTF8  
Buid System 配置UTF8 ->"env": {"PYTHONIOENCODING": "utf8"}


## 5. python 库安装
> 例如 window python提示ModuleNotFoundError: No module named 'requests'的解决办法  
进入python 安装目录 Scripts 打开cmd 执行  
pip install requests  
pip install --user beautifulsoup4  


## 6. 重要快捷键

> Fn+Alt+F3 更改所有相同单词  
Ctrl+D（可重复按） 更改以后一到多个单词  
Ctrl+B执行  


## 7. 运算

> "/" 为浮点数除法，返回浮点结果  
"//" 表示整数除法，返回不大于结果的一个最大整数  
"\*\*" 幂运算   
4\*\*0.5 计算4的平方根   
4\*\*2 计算4的二次方  


---
[st3]:http://www.sublimetext.cn/3
[py3]:https://www.python.org/downloads/
