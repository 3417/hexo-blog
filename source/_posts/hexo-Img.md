---
title: hexo如何使用本地图片和线上图片
date: 2019-03-17 16:22:46
tags: 
categories: [hexo]
---

## 如何在hexo引入本地图片

1、设置根目录下的_config.yml的post_asset_folder: true
2、执行hexo new post_name的时候就会生成对应的文件夹和文件名称
3、将图片资源放在post_name文件夹中，文章就可以使用相对路径引用图片资源了
<!-- more -->

{% codeblock %}
post_asset_folder: true //设置为true

hexo new post_name //生成对应的文件夹和文件名称
{% endcodeblock %}
```
a. 本地资源不限制大小
![](img.jpg)
b. 网络图片资源，限制图片显示尺寸
{% img [class names] /path/to/image [width] [height] '"title text" "alt text"' %}
```
4、插入网络图片
{% img http://t2.ituba.cc/201811/12/0o3lbrquilc.gif 一个网络图片%}
5、关于图片放大的效果
{% blockquote %}
1、图片弹出效果（鼠标移到图片上显示放大镜效果）请参考：https://github.com/theme-next/theme-next-fancybox3.
2、进入next主题目录下执行git clone https://github.com/theme-next/theme-next-fancybox3 source/lib/fancybox
3、配置fancybox，注意是clone到主题下面的source/lib/fancybox的主题配置_config.yml,fancybox: true
{% endblockquote %}





