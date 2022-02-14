---
title: 前端当前主流的包管理工具(npm yarn pnpm)
date: 2019-12-26 14:06:19
categories: ['project']
---


## 当前主流的包管理工具

### 安装
```
1.node集成了npm 包，安装node后使用npm -v查看npm版本

2、安装淘宝镜像(cnpm)：npm install -g cnpm --registry=https://registry.npm.taobao.org

3、安装Yarn：npm install yarn -g

3、安装pnpm：npm i pnpm OR (升级：pnpm i pnpm)
```

### 小提示

a.使用相应的help命令可以查看包管理工具的命令属性
b.yarn 需要配置淘宝镜像(因为GFW)
```
yarn config set registry https://registry.npm.taobao.org -g （配置淘宝源）
yarn config set sass_binary_site http://cdn.npm.taobao.org/dist/node-sass -g（配置node-sass源）
yarn global dir -->查看yarn全局安装的位置
```