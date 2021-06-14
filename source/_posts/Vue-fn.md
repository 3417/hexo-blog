---
title: Vue-fn
date: 2021-06-14 17:12:07
tags: Vue
categories: ["Vue"]
---


## Vue3.安装

```
vue create <project_name> (根据提示进行选择)
```

## 关于Vite
序言：比肩webpack的打包工具，Vite能够显著提升前端开发体验
[地址](https://cn.vitejs.dev/guide/#command-line-interface)
<!-- more -->

## Vite工具+Vue3.xx
### Vite
1. 安装（node版本需要大于等于12.0.0）
```
npm init @vitejs/app
OR
yarn create @vitejs/app
...会有相关的提示信息
```
2. 启动+打包
```
npm dev OR yarn dev

npm build OR yarn build
```
3. 关于 vite.config.js
```
地址：https://cn.vitejs.dev/config/

默认配置：(简单配置)
export default{
    root:"",  //
    base:'',
    mode:'',
    publicDir:'',
    server:{
        host:'',  //主机IP地址
        port:'', //端口地址
        open:'' //自动打开--当此值微字符串时，会被当作URL的路径名
    }
    ....
}

```

### Vite+vue3.xx
1. 通过vite工具构建
npm init @vitejs/app OR yarn create @vitejs/app

2. vue方式构建
npm create vite-app <project-name>
OR
yarn create vite-app <project-name>

3. 当然自己要装vue-router vuex 新建vite.config.js



## UI 组件库的引入（element-plus）
1. 安装
```
npm install element-plus --save
OR
yarn add element-plus -S
```

2. 使用

```
import { createApp } from 'vue'
import ElementPlus from 'element-plus';
import 'element-plus/lib/theme-chalk/index.css';
import App from './App.vue';
const app = createApp(App)
app.use(ElementPlus)
app.mount('#app')
```

3. 基于webpack的按需引入
```
1. 安装按需引入的插件
npm install babel-plugin-import -D
OR 
yarn add babel-plugin-import -D


2. 修改babel.config.js
module.exports = {
  plugins: [
    [
      "import",
      {
        libraryName: 'element-plus',
        customStyleName: (name) => {
          name = name.slice(3)
          return `element-plus/packages/theme-chalk/src/${name}.scss`;
        },
      },
    ],
  ],
};
```

4. 基于vite的按需引入
```
1. 安装
npm install vite-plugin-style-import -D
OR
yarn add vite-plugin-style-import -D

2. 修改vite.config.js
import { defineConfig } from 'vite'
import vue from '@vitejs/plugin-vue'
import styleImport from 'vite-plugin-style-import'

export default defineConfig({
  plugins: [
    vue(),
    styleImport({
      libs: [{
        libraryName: 'element-plus',
        esModule: true,
        ensureStyleFile: true,
        resolveStyle: (name) => {
          name = name.slice(3)
          return `element-plus/packages/theme-chalk/src/${name}.scss`;
        },
        resolveComponent: (name) => {
          return `element-plus/lib/${name}`;
        },
      }]
    })
  ]
})
3. 注册组件
import { createApp } from 'vue'
import { ElButton, ElSelect } from 'element-plus';
import App from './App.vue';
// 如果要使用.scss样式文件，则需要引入base.scss文件
// import 'element-plus/packages/theme-chalk/src/base.scss'

const app = createApp(App)
app.component(ElButton.name, ElButton);
app.component(ElSelect.name, ElSelect);

/* or
 * app.use(ElButton)
 * app.use(ElSelect)
 */

app.mount('#app')

...具体细节可以阅读element-plus官网

```

