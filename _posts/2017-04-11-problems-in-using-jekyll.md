---
layout: post
title: 使用jekyll过程中遇到的一些问题
categories: [tips]
tags: [tips]
fullview: true
comments: true
---
 
 在使用jekyll过程中遇到的一些问题及解决方法
 
 # #1.依赖的版本号不对：
 ````
 You have already activated json 2.0.3, but your Gemfile requires json 1.8.6. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
 ````
 
 这个问题是在下载了别人的jekyll后，运行```` jekyll s ```` 后出现的。
 大概就是说，你已经在用2.0.3了，但是你的gemfile里却要1.8.6。所以在你的命令前增加```` bundle exec ````,
 即```` bundle exec jekyll s````可以就可以解决这个问题了。
 试了一下，的确是可以将jekyll运行起来了，但是根目录下却多了个GemFile.lock。打开后看到：
 ````
 GEM
   remote: https://rubygems.org/
   specs:
     activesupport (4.2.7)
       i18n (~> 0.7)
       json (~> 1.7, >= 1.7.7)
       minitest (~> 5.1)
       thread_safe (~> 0.3, >= 0.3.4)
       tzinfo (~> 1.1)
     addressable (2.5.1)
       public_suffix (~> 2.0, >= 2.0.2)
     coffee-script (2.4.1)
       coffee-script-source
       execjs
     coffee-script-source (1.12.2)
     colorator (1.1.0)
     ethon (0.10.1)
       ffi (>= 1.3.0)
     execjs (2.7.0)
     faraday (0.12.0.1)
 ......
   json (1.8.6)
     kramdown (1.13.2)
     liquid (3.0.6)
     listen (3.0.6)
       rb-fsevent (>= 0.9.3)
       rb-inotify (>= 0.9.7)
 
 ````
 留意后面的```` json (1.8.6) ````,到这里就开始猜测是否就是这个版本号问题？将它改成````sh json (2.0.3) ```` 
 再重新运行jekyll，行了！
 