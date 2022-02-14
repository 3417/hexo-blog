---
title: vite批量引入相关的文件
date: 2021-09-23 13:58:21
tags: [vite]
categories: [vite]
---


## Vite批量引入相关的文件(如vuex)


<!-- more -->

```
// 使用globEager直接引入
 const modulesFiles = import.meta.globEager('./modules/**/*.js');
 const modules = {}
 for(let key in modulesFiles){
   modules[key.replace(/(\.\/modules\/|\.js)/g,'')] = modulesFiles[key].default
 }
 Object.keys(modules).forEach(item=>{
   modules[item]['namespaced'] = true
 })

// 使用import.meta.glob动态引入(TODO:动态引入无法获取到数据???)
const modulesFiles = import.meta.glob('./modules/**/*.js');
const modules = {};
for(const path in modulesFiles){
  modulesFiles[path]().then((mod) => {
    modules[path.replace(/(\.\/modules\/|\.js)/g, '')] = mod.default
  })
}

```

## webpack的批量引入(全局注册组件)

```
//1.一个要搜索的目录，2.一个标记表示是否还搜索其子目录，3.以及一个匹配文件的正则表达式
const contexts = require.context('./components', true, /\.vue$/)
contexts.keys().forEach(component => { 
  let componentEntity = contexts(component).default // 使用内置的组件名称 进行全局组件注册 
  let cpn = component.replace(/^\.\//, '').replace(/\.\w+$/, '') //不存在name则以组件名称进行注册
  Vue.component(componentEntity.name || cpn, componentEntity) 
})
```