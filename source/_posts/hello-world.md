---
title: hexo搭建个人博客官方示例
date: 2019-01-04
---
Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

## Quick Start

<!-- more -->

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```


### 如何在hexo引入本地图片

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
{% img http://hd.wallpaperswide.com/thumbs/beast_2-t2.jpg 一个网络图片%}

5、关于图片放大的效果(基于nexT主题)
{% blockquote %}
1、图片弹出效果（鼠标移到图片上显示放大镜效果）请参考：https://github.com/theme-next/theme-next-fancybox3.
2、进入next主题目录下执行git clone https://github.com/theme-next/theme-next-fancybox3 source/lib/fancybox
3、配置fancybox，注意是clone到主题下面的source/lib/fancybox的主题配置_config.yml,fancybox: true
{% endblockquote %}

More info: [Deployment](https://hexo.io/docs/one-command-deployment.html)
