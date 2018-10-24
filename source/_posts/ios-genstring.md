---
title: ios-genstring
tags:
- iOS
categories:
- iOS
thumbnail: 'https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=3769399397,1385121564&fm=26&gp=0.jpg'
date: 2018-10-24 14:40:12
---

# 用Genstring生成Localizable.strings

我们使用字符串，必须用NSLocalizedString(key,comment)，这样我们在不同的Localizable.strings对key指定不同的值，系统会根据当前系统语言，去不同的lproj找不同的字符串

但是如果每次加了一个本地化字符串，就得手动去Localizable.strings添加对应的key，那就太麻烦了，幸好苹果提供了快捷生成本地化key的命令。下面以en.lproj的生成为例：

首先，我们进入程序工程所在的目录，用命令建立en.lproj 
```sh
mkdir en.lproj
```
然后我们遍历所有的子目录文件，不包括头文件，去生成Localizable.strings，命令如下：
```sh
find ./ -name *.m -print0 | xargs -0 genstrings -o en.lproj
```
遍历所有目录及子目录，包括头文件，去生成Localizable.strings，命令如下：
```sh
find . −name′∗.m′−o−name′∗.h′ -print0 | xargs -0 genstrings -o en.lproj
```
如果只生成当前目录下文件的Localizable.strings，不会遍历，命令如下：
```sh
genstrings -o en.lproj *.m
```
如果想给zh.lproj添加Localizable.strings文件一样，命令如下：
```sh
find . −name′∗.m′−o−name′∗.h′ -print0 | xargs -0 genstrings -o zh-lproj
```

`1. Note:需要注意的是，NSLocalizedString(key,comment)，用这个函数时，key不能是宏定义或者一些动态字符串，否则用上面的命令会报错。`
`2. 最后补一句，规范化还是很必须的。假如你以前的代码都没用到NSLocalizedString，那就麻烦了，只能手动添加了。`
