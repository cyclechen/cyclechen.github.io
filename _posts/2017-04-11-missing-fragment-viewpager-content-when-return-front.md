---
layout: post
title: 使用jekyll过程中遇到的一些问题
categories: [android]
tags: [viewpager,FragmentViewPager]
fullview: true
comments: true
---

APP从后台回到前台时首页推荐内容缺失问题：

````java
recomandAdapter = new RecomandFragmentPagerAdapter(getActivity().getSupportFragmentManager(), fragmentList);
````
改成

````java
recomandAdapter = new RecomandFragmentPagerAdapter(getChildFragmentManager(), fragmentList);

````

原因需要继续查资料

