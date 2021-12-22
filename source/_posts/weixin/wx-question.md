---
title: 微信小程序爬坑记录
date: 2021-12-22 13:56:35
tags: weixin
categories: [weixin]
---


## 小程序在项目遇到的问题
<!-- more -->

1. IOS 启动白屏的原因

```
?<=、?<!、?!、?=  相关正则使用会导致该问题
使用相关的ES7语法
```

2. 滚动穿透
```
<!-- page-meta 只能是页面内的第一个节点 -->
<page-meta page-style="{{ show ? 'overflow: hidden;' : '' }}" />
```

3. 小程序原生input textarea 层级过高
```
弹层弹出的时候  将input 或 textarea用view 或者text替换  可以避免这个问题
```