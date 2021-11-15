---
title: Vue.observable
date: 2021-11-15 09:59:11
tags: [Vue]
categories: [Vue]
---

## 序言
>让一个对象可响应。Vue 内部会用它来处理 data 函数返回的对象。
>返回的对象可以直接用于渲染函数和计算属性内，并且会在发生变更时触发相应的更新。也可以作为最小化的跨组件状态存储器，用于简单的场景。

<!-- more -->
## 注册

```
import Vue from 'vue';
export let store = Vue.observable({
    count:0,
    xxx...
})


export let mutations = {
    fnMethods(props){
        store.count = props;
    },
    xxx...
}
```

## 使用

```
//引入组件
import {store,mutations} from '@/文件夹地址';
//computed 里面显示store里面定义的数据
//methods里面执行mutations定义的方法
```