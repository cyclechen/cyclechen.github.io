---
layout: post
title: vmware中修改ubuntu的分辨率
categories: [tips]
tags: [tips]
fullview: true
comments: true
---


vmware11.1.0中新安装好的ubuntu15.04,分辨率只有800*600,怎么看都不舒服,改之，具体如下：

<pre>
<code>#终端中执行
sudo gedit /etc/default/grub</code></pre>

<p>找到</p>

<pre>
<code>#GRUB_GFXMODE=640x480</code></pre>

<p>去掉注释,并改成自己想要的分辨率,小于主机的分辨率:</p>

<pre>
<code>GRUB_GFXMODE=1280x768</code></pre>

<p>保存,关闭,继续在终端中分别执行下面命令更新;</p>

<pre>
<code>echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-initramfs -u -k all 
sudo update-grub</code></pre>

<p>重启一下虚拟机,就可以看到分辨率已经变了;</p>
