---
title: 乾坤微前端
date: 2021-04-20 22:13:00
tags: "微前端"
categories: ["微前端"]
---

## [文档地址](https://qiankun.umijs.org/zh)

### 安装

```
yarn add qiankun # 或者 npm i qiankun -S
```
<!-- more -->

### 1.主应用(不限技术栈)

```
import { registerMicroApps, start } from 'qiankun';
registerMicroApps([
  {
    name: 'react app', // app name registered
    entry: '//localhost:7100',
    container: '#yourContainer',
    activeRule: '/yourActiveRule',
    //entry为微应用项目启动的地址
    //container 为html页面上id相同的匹配标签
    //如果是hash模式则 activeRule:'#/yourActiveRule'
  },
  {
    name: 'vue app',
    entry: { scripts: ['//localhost:7100/main.js'] },
    container: '#yourContainer2',
    activeRule: '/yourActiveRule2',
  },
]);


start();

//如果主应用的技术栈是vue的话
vue.$nextTick(()=>{
   start() 
})
```


### 2微应用（vue/react/angular）==>当前Vue项目

```
Vue2.x  项目
1.在src目录新增public-path.js
if (window.__POWERED_BY_QIANKUN__) {
  __webpack_public_path__ = window.__INJECTED_PUBLIC_PATH_BY_QIANKUN__;
}


2入口文件main.js

+ import './public-path';
+ import VueRouter from 'vue-router';
+ import routes from './router';
+ let router = null,instance = null;
+function render(props = {}){
    const {container} = props;
    router = new VueRouter({
        base:window.__POWERED_BY_QIANKUN__ ? '前缀路径' :'/',
        mode:'hash'  //目前是主微都是hash模式
        routes
    })
    
    instance = new Vue({
        router,
        store,
        render:(h) =>h(App),
    }).$mount(container ? container.querySelector('#app') : '#app')
}
//独立运行时
if(!window.__POWERED_BY_QIANKUN__){
    render();
}

export async function bootstrap(){
    console.log('[vue] vue app bootstraped');
}

export async function mount(props){
    console.log('[vue] props form main framework',props);
    render(props);
}

export async function unmount(){
    instance.$destory();
    instance.$el.innerHTML = '';
    instace = null;
    router = null;
}


3.打包配置修改vue.config.js
const {name} =  require("./package");
module.exports = {
    devServer:{
        headers:{
            "Access-Control-Allow-Origin":"*"
        }
    },
    configureWebPack:{
        output:{
            library:`${name}-[name]`,
            libraryTarget:'umd', //把微应用打包成umd库格式
            jsonpFunction:`webpackJsonp_${name}`,
        }
    }
}

```

#### 微应用需要在路由前面添加base前缀Or遍历路由添加前缀