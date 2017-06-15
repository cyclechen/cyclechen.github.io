---
layout: post
title: 自定义全屏透明dialog
categories: [tips]
tags: [tips]
fullview: true
comments: true
---

最近在一个比较简洁的屏保，屏幕中间只显示当前日期和时间
其中时间需要特别大的字号，但是用系统默认的会发现当设置了大字号后，字体变得非常粗，严重影响美观。

网上搜索了下，决定换一个字体,下面是部分代码：

````java

        Typeface typeface  = Typeface.createFromAsset(getAssets(),"font/PingFang ExtraLight.ttf");
        
        mTextViewTime = (TextView) findViewById(R.id.tv_time);
       
        mTextViewTime.setTypeface(typeface);

````


需要注意一点：字体本身都带有一定的padding值！所以布局中设置比较大字号的时候，可能会受此影响，导致文字显示不出来，或者影响布局。
解决办法：设置android:includeFontPadding="false",用来设置文本框是否包含顶部和底部留白（左右两侧默认没有留白），将其设置为false，TextView就会取消留白。这样就避免了TextView导致UI出现差异！