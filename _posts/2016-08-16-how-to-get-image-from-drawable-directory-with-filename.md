---
layout: post
title: 如何通过文件名从drawable文件夹中获取图片文件。
categories: [android]
tags: [android, drawable]
fullview: true
comments: true
---

{% highlight yaml %}

    /**
     * 从assets文件夹中异步加载图片
     *
     * @param imageName 图片名称，不带后缀的，例如：test
     * @param imageView
     */
    public static void loadLocalImage(String imageName, ImageView imageView, Context context) {
        //得到application对象
        ApplicationInfo appInfo = context.getApplicationInfo();
//得到该图片的id(name 是该图片的名字，"drawable"是该图片存放的目录，appInfo.packageName是包名)
        int resID = context.getResources().getIdentifier(imageName, "drawable", appInfo.packageName);
        imageView.setBackgroundResource((resID));
    }
{% endhighlight %}
