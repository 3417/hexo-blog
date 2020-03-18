---
title: Mock
date: 2020-02-17 15:24:49
tags:
categories:
---


{% blockquote %}
生成随机数据，拦截 Ajax 请求(分为线上版本和本地版本)

线上版本参照：http://mockjs.com/ ==>https://www.easy-mock.com/docs
{% endblockquote %}

<!-- more -->
## 本地版本

### 安装

{% codeblock %}
npm install mockjs --save-dev OR yarn...pnpm...cnpm...
{% endcodeblock %}

### 创建文件

```
import Mock from 'mockjs'
Mock.mock('api',{
    "res":0,
    data:{
        "mtime": "@datetime",//随机生成日期时间
        "score|1-800": 800,//随机生成1-800的数字
        "rank|1-100":  100,//随机生成1-100的数字
        "stars|1-5": 5,//随机生成1-5的数字
        "nickname": "@cname",//随机生成中文名字
    }
})

在main,js中引入该JS文档
import './XXX/mock'

```

### 使用

{% codeblock %}
使用axios请求封装好的接口
axios.get(api).then(res=>{}).catch(err=>{})
{% endcodeblock %}

### 设置延时请求
{% codeblock %}
Mock.setup({
    //timeout:4000 第一种
    timeout:"2000-6000" 第二种
})
{% endcodeblock %}

