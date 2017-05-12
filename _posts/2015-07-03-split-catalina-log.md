---
layout: post
title: 分割catalina.log日志文件
categories: [tomcat]
tags: [java,tomcat]
fullview: true
comments: true
---


为了避免文件过大影响tomcat性能，同时方便查看日志，故分割该日志文件是很有必要的。

方法有很多，可以上网搜索一下，下面亲测可行的方法；

环境：centos5.9-64, tomcat7.0

打开tomcat/bin/catalina.sh，找到
```java
CATALINA_OUT="$CATALINA_BASE"/logs/catalina.out
```

修改为：
```java
CATALINA_OUT="$CATALINA_BASE"/logs/catalina"-`date "+%Y-%m-%d"`".out
```

重启tomcat。done