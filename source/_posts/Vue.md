---
title: Vue-Cli创建项目
date: 2019-12-29 14:05:28
tag: VueCli
categories: [Vue,VueCli]
---
## Vue2.xx创建项目

### 安装淘宝镜像

```
npm install -g cnpm --registry=https://registry.npm.taobao.org

Vue初始化安装

全局安装脚手架vue-cli-->npm  i vue-cli -g
利用webpack安装模板：vue init webpack 文件夹名称
```
<!-- more -->
### Vue启动打包项目
```
npm run dev-->启动

npm run build-->打包
```
### 在webpack.prod.conf.js文件里面的plugins 加上，打包过滤console.log()日志。
```
new webpack.optimize.UglifyJsPlugin({
      compress: {
        warnings: false,
        drop_debugger: true,
        drop_console: true
      },
      sourceMap: true
    })
```

### 全局安装Cli--Vue3.x

```
npm install -g @vue/cli
npm uninstall -g @vue/cli
# OR
yarn global add @vue/cli
yarn global remove @vue/cli

```


### 新建项目
```
1.使用图形化界面进行安装
vue ui(根据业务需求进行选择安装)


2.使用命令行进行安装
vue create 项目名称 / yarn create 项目名称 
```

### 启动项目
```
yarn serve OR npm run serve

yarn build OR npm run build
```

### 注意事项

如果要修改Vue默认的webpack配置，需要自己新建一个Vue.config.js文件进行覆盖配置


