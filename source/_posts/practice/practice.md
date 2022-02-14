---
title: 项目中遇到的问题集合
date: 2021-09-03 16:35:42
index_img: /img/practice/practice.jpg
banner_img: /img/practice/practice.jpg
tags: []
categories: ['project']
---

## Vue代理问题

1. Vue proxy代理 服务端cookies Path多级路径问题
```
解决方法:
1. 将代理名称配置为Path目录名称一致
2. 配置axios的baseUrl
```
2. VueCli3.xx以上引入静态的css和Js文件
```
//统一放在public文件夹下
src="<%= BASE_URL %>XXX.js" 方式引入

//在vue.config.js中使用
module.exports = {
    configureWebpack:{
        externals:{
            'jquery':'$'
        }
    }
}
```

<!-- more -->

## 快速将表单转换为对象

```
const formdata = new FormData();
formdata.append("user","jack");
formdata.append("pwd",'admin123');
formdata.appned('file',new Blob(),'png')
console.log(Object.fromEntries(formdata))
// VM4738:1 {user: "jack", pwd: "123123", file: ....file}
```

## 查询字符串快速转换为对象

```
//快速将URL参数转换为对象
Object.fromEntries(new URLSearchParams("?foo=bar&baz=qux&test=demo"))
//{foo: "bar", baz: "qux", test: "demo"}

//快速实现数字累计--通过prototype
function numCount(){
    return numCount.prototype.num = numCount.prototype.num ? ++numCount.prototype.num : 1
}

console.log(numCount()) //1
console.log(numCount()) //2
console.log(numCount()) //3
```

## Vant框架 H5页面问题

1. h5中的IOS不支持横线的时间格式，如：2020-02-08 19:52:59
2. h5中使用了vant组件的van-search，要显示搜索按钮，如下设置
```
<form action="/">
    <van-search />
</form>
```

## 项目场景根据物流公司的首字母去匹配对应的数据分类
```
for循环版本：
let data = {};
for (let i = 0; i < res.length; i++) {
    if (!data[res[i].e_letter]) {
        let arr = [];
    arr.push(res[i]);
        data[res[i].e_letter] = arr;
    } else {
        data[res[i].e_letter].push(res[i]);
    }
}
```


## 数组对象的替换
```
let arr =[
    {id:1,name:"test"},
    {id:2,name:"test1"},
    {id:3,name:"test2"},
]
let obj = {id:2,name:"hahah"}

arr = arr.map(item=>item.id === obj.id ? obj :item)
```

## 删除两个数组对象中相同的对象
```
let arr1 = [{id:'1',name:'json'},{id:'2',name:'book'} ]
let arr2 = [{id:'1',name:'json',age:'15'},{id:'2',name:'book',age:'16'},{id:'3',name:'ani',age:'17'}] 

//ES6的方法
let add = arr2.filter(item => !arr1.some(ele=>ele.id===item.id));
console.log(add)
```

## 关于腾讯云下载的问题(视频)
  腾讯云：window.open(url?download_name=xxxx.mp4)


## flex布局文字换行

```
包裹文字的div
overflow-wrap: break-word;
word-break: break-word;  //兼容IE

顶层父级加上hidden
overflow:hidden
```

...后续更新