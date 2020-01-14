---
title: Vue3.x创建项目
date: 2019-12-29 14:05:28
tags: [Vue,VueCli]
---

### 全局安装Cli

```
npm install -g @vue/cli
npm uninstall -g @vue/cli
# OR
yarn global add @vue/cli
yarn global remove @vue/cli

```
<!-- more -->

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

附上完整的vue.config.js配置
```
    后续添加
```

