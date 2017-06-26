---
layout: post
title: centos7中安装andrdoid编译环境
categories: [kotlin]
tags: [kotlin,kotlin命令行]
fullview: true
comments: true
---

继续纪录~~~~
本文描述了大centos7.0中如何部署andrdoid编译环境，附件下载连接：链接：http://pan.baidu.com/s/1dEBMKed 密码：mz6v
附件包括：
- android-sdk-linux.tar： androidSDK压缩包，包括了extra，platform（21，22），build tools(21.0.0，21.1.1，22.0.0，22.0.1)。其他版本的platform，build tools需要另外下载安装;
- gradle-2.14.1-all.zip：当前使用的gradle版本，其他版本需要另外下载安装; 
- gradleDemo.zip：用于测试android编译环境是否正常安装; 
- HOW-TO-USE.md：安装说明文档。


Step 1. 安装android SDK
1）android sdk 工具包的一些命令行工具是基于32位系统的，在64为平台运行32程序必须安装 一些依赖库,方法如下：
```` java
	yum install glibc*.i686
    yum install zlib*.i686
    yum install libstdc++.so.6
````
2）解压android-sdk-linux.tar；
3）将android-sdk-linux目录添加到环境变量中，确保终端能调用android SDK的一些命令，在/etc/profile中末尾增加下面内容：
```` java
	ANDROID_HOME=$HOME/android-sdk-linux  --当前android-sdk-linux目录
    export PATH="$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools"
    export ANDROID_HOME
````
4）使环境变量生效:
```` java
	source /etc/profile
````
5）验证是否安装正常
```` java
	android list sdk --all 
````
正常输出：
```` java
   1- Android SDK Tools, revision 24.4.1
   2- Android SDK Platform-tools, revision 23.0.1
   3- Android SDK Platform-tools, revision 23.1 rc1
   4- Android SDK Build-tools, revision 23.0.1
   5- Android SDK Build-tools, revision 23 (Obsolete)
   6- Android SDK Build-tools, revision 22.0.1
   7- Android SDK Build-tools, revision 22 (Obsolete)
   8- Android SDK Build-tools, revision 21.1.2
   9- Android SDK Build-tools, revision 21.1.1 (Obsolete)
  10- Android SDK Build-tools, revision 21.1 (Obsolete)
  11- Android SDK Build-tools, revision 21.0.2 (Obsolete)
  12- Android SDK Build-tools, revision 21.0.1 (Obsolete)
````

Step 2.安装Gradle工具
1）解压gradle-2.14.1-all.zip，并创建一个软连接gradle：
```` java
	ln -s gradle-2.14.1 gradle
````

2）将gradle目录添加到环境变量中，确定终端能调用gradle：
```` java
	GRADLE_HOME=$HOME/gradle
    export PATH=$PATH:$GRADLE_HOME/bin
````

3）使环境变量生效：
```` java
	source /etc/profile
````

4）验证是否安装正常：
```` java
	gradle -v 
````
能看到gradle版本信息即为安装正常；

Step3.验证android编译环境是否正常安装
1）解压gradleDemo.zip，进入gradleDemo
2）运行：
```` java
gradle build 
````
3）进入 ```` app/build/outputs/apk ````，检查是否有apk文件，有则下载安装到手机，如果能正常安装，则说明android编译环境正常。