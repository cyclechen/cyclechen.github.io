---
layout: post
title: 切换到前台时FragmentViewPager内容缺失问题
categories: [android]
tags: [viewpager,FragmentViewPager]
fullview: true
comments: true
---

继续整理笔记。。。。。

#切换到前台时FragmentViewPager内容缺失问题

````java
recomandAdapter = new RecomandFragmentPagerAdapter(getActivity().getSupportFragmentManager(), fragmentList);
````
改成

````java
recomandAdapter = new RecomandFragmentPagerAdapter(getChildFragmentManager(), fragmentList);

````

原因需要继续查资料

