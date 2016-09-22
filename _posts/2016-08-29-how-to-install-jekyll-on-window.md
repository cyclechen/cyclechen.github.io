---
layout: post
title: 如何在window上安装jekyll。
categories: [jekyll]
tags: [jekyll]
fullview: true
comments: true
---


## 简介
**Jekyll**，一个静态网页生成器，支持html,mardown或者texttile文件格式，通过markdown或者liquid模板引擎，生成apache,nginx或者其他web服务器所支持的完整网页文件。

##依赖：
 
- **Rubyinstaller** ：必须
- **RubyDevKit**  ：必须
- **Python** : 必须。2.0版本，3.0里面在一些机子上可能会有问题。


## 安装
### 安装Ruby

1）前往 http://rubyinstaller.org/downloads/

2）在 “RubyInstallers” 部分，选择某个版本点击下载。这里我选择了2.3.1-64，适用于64位系统。

3）下载完之后双击安装包安装，注意：
 - 安装路径里不要出现空格，比如Program Files。
 - 勾选 “Add Ruby executables to your PATH”，这样执行程序会被自动添加至 PATH 而避免不必要的头疼。

4）测试安装是否成功，打开cmd命令行，执行

    ruby -v
    


    ruby 2.3.1p112 (2016-04-26 revision 54768) [x64-mingw32]

 证明安装成功。

### 安装RubyDevKit
