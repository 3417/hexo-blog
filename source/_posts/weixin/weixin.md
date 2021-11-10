---
title: 原生微信小程序
date: 2021-11-10 15:47:14
tags: weixin
categories: [weixin]
---


## [初始化](https://developers.weixin.qq.com/miniprogram/dev/devtools/devtools.html)
1. 访问微信开发者的网站下载微信开发工具，初始化小程序。
2. 小程序的项目结构包含了WXML,WXSS,JSON,JS等相关文件

<!-- more -->

## 项目结构解析
1. WXML---类似于html
2. WXSS---类似于css
3. JSON---相关配置文件
4. JS---相关方法和事件

## 注意事项
1. 微信小程序view类似div text类似于span之类的标签
2. 在微信里面只要是渲染数据都是带模版渲染.
3. 微信的导航栏跳转的地址，在页面跳转就不能进行跳转了。原因：规定如此并非BUG
4. 底部的tab切换菜单至少2个最多5个(官方文档规定)
5. 请求到数据进行渲染要注意this的指向

## 事件

```
//相关事件
touchstart	        手指触摸动作开始	
touchmove	        手指触摸后移动	
touchcancel	手指触摸动作被打断，如来电提醒，弹窗	
touchend	        手指触摸动作结束	
tap	        手指触摸后马上离开	
longpress	        手指触摸后，超过350ms再离开，如果指定了事件回调函数并触发了这个事件，tap事件将不被触发	
longtap	        手指触摸后，超过350ms再离开（推荐使用longpress事件代替）	
transitionend	会在 WXSS transition 或 wx.createAnimation 动画结束后触发	
animationstart	会在一个 WXSS animation 动画开始时触发	
animationiteration	会在一个 WXSS animation 一次迭代结束时触发	
animationend	会在一个 WXSS animation 动画完成时触发	
touchforcechange	在支持 3D Touch 的 iPhone 设备，重按时会触发

事例:
    //首次绑定事件用到 bindtap,阻止事件冒泡用到 catchtap 阻止事件冒泡
    <button size="mini" bindtap="getMsg">点击进行测试/button>
    //获取值
    this.data.xxx;
    //改变值
    this.setData({
        //改变的值，键值对的方式
    })
```

## 循环事件

```
<view wx:for="{{list}}">
    {{index}}-{{item}} //键名-键值
</view>

双重嵌套：
<view wx:for="{{list1}}">
    {{item.cate}}
    <view wx:for="{{list2}}">
        {{item.name}}
    </view>
</view>

使用 wx:for-item 可以指定数组当前元素的变量名，
使用 wx:for-index 可以指定数组当前下标的变量名：
<view wx:for="{{array}}" wx:for-index="key" wx:for-item="itemName">
    {{key}}--{{itemName.xxx}}
</view>
```

## 判断事件
```
<view wx:if="{{length > 4}}">1</view>
使用<block></block>组件包裹多个判断条件
<block wx:if="{{true}}">
  <view> view1 </view>
  <view> view2 </view>
</block>
```

## [小程序渲染HTML模版](https://github.com/icindy/wxParse)
```
//将相应的插件引入到项目中去，
// wxss最好引入到app.wxss里面去，js引入到需要用到的文件里面，HTML也一样

1.var WxParse = require('../../wxParse/wxParse.js');
2.@import "wxParse/wxParse.wxss";
3.var article = '<div>我是HTML代码</div>';

* WxParse.wxParse(bindName , type, data, target,imagePadding)
* 1.bindName绑定的数据名(必填)
* 2.type可以为html或者md(必填)
* 3.data为传入的具体数据(必填)
* 4.target为Page对象,一般为this(必填)
* 5.imagePadding为当图片自适应是左右的单一padding(默认为0,可选)
var that = this;
WxParse.wxParse('article', 'html', article, that, 5);

4.<import src="你的路径/wxParse/wxParse.wxml"/>
//这里data中article为bindName
<template is="wxParse" data="{{wxParseData:article.nodes}}"/>
```

## 微信定义公共办法

```
//定义
let config = {
    host:'www.xxxx.com'
}
//导出
module.exports=config;
//使用
let config = require('XXXXXX');
```