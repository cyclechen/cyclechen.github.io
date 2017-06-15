---
layout: post
title: 安装kotlin命令行编译器
categories: [kotlin]
tags: [kotlin,kotlin命令行]
fullview: true
comments: true
---


官方参考教程网址：[https://kotlinlang.org/docs/tutorials/command-line.html](https://kotlinlang.org/docs/tutorials/command-line.html)

本文主要是纪录一下在安装过程遇到的问题及解决办法。Let's go!

环境：win10，jdk1.8.0_91，已配置JAVA_HOME等java相关环境变量。

#安装过程

1.按照官网教程的说明，去github里下载了zip压缩包，解压到```` D:\Program Files ````

2.设置环境变量KOTLIN_HOME，值为```` D:\Program Files\kotlin-compiler-1.1.2-5\kotlinc ````

3.在环境变量变量Path最后增加```` %KOTLIN_HOME%\bin; ````

4.好了，到了第3步的时候貌似一切都没问题了。那么，验证一下是否安装正常。打开cmd，执行 ```` kotlinc -help ````

  结果：
  ```java
   C:\Users\cycle>kotlinc -help
   错误: 找不到或无法加载主类 org.jetbrains.kotlin.preloading.Preloader
  ```
  
  What？！难道是少执行了什么？又看了一次官网教程
  > Unzip the standalone compiler into a directory and optionally add the bin directory to the system path. The bin directory contains the scripts needed to compile and run Kotlin on Windows, OS X and Linux.
  
 大概可以理解为解压独立编辑器到一个目录中，然后，可以将bin目录增加到系统path中，这个bin里包括了一些在window,osx和linux下需要编译和执行的脚本。
  
  漏了初始化？打开bin目录，看到有几个kotlin.bat,kotlinc.bat,kotlinc-js.bat,kotlinc-jvm.bat等几个文件。
  
  都用notepad++打开看了下，kotlin.bat,kotlinc-js.bat,kotlinc-jvm.bat三个都是调用kotlinc.bat的。唔，试一下直接执行kotlinc.bat看看，结果，返回了同样的错误。
  
  google了下错误信息，然后并没有得到以什么有效信息，再看了下错误信息，突然想，不会和路径有关吧。
  
  删除目录，然后，重新压缩到```` D:\ ````下
  
  将KOTLIN_HOME改为```` D:\kotlin-compiler ````
  
  重新打开一个cmd，重新执行```` kotlinc -help ````
  
  结果，返回正常了！
  
  对比了一下前后的目录，只能发现只是一个空格的问题，难道就是空格了吗？为了验证这个假设，再一次重新解压到另外一个带空格和不带空格的目录路径下，
  
  结果，不带空格下的正常！而不带空格的，仍报同样的错误！
  
  在小密圈里看到ZeroyiQ童鞋也遇到了同样的问题，他改用git bash 可以正常执行，由于本机没有git bash，就没测试了。如果大伙有其他的解决办法欢迎提出。