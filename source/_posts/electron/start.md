---
title: Electron
date: 2021-12-03 15:36:02
tags: [electron]
categories: [electron]
---


## 序言
Electron是一个使用 JavaScript、HTML 和 CSS 构建桌面应用程序的框架。 嵌入 Chromium 和 Node.js 到 二进制的 Electron 允许您保持一个 JavaScript 代码代码库并创建 在Windows上运行的跨平台应用 macOS和Linux——不需要本地开发经验

<!-- more -->

## 安装
1. 基于官网提供的安装方式
```
//初始化(文件夹已经创建好)
# npm init
# npm install --save-dev electron
// 添加启动命令行
{
    "script":{
        "start":"electron ."
    }
}

//执行启动
# npm start
```
2. [vue版本的electron安装](https://nklayman.github.io/vue-cli-plugin-electron-builder/guide/)
```
# VueCli版本为3.x以上
1、安装：vue add electron-builder
2、启动：npm/yarn electron:serve[可自配]
3、打包：npm/yarn electron:build[可自配]
```

## 设置electron淘宝镜像

```
npm config set ELECTRON_MIRROR https://npm.taobao.org/mirrors/electron/ 
```
## 文件初始化事例

```
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <!-- https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP -->
    <meta http-equiv="Content-Security-Policy" content="default-src 'self'; script-src 'self'">
    <meta http-equiv="X-Content-Security-Policy" content="default-src 'self'; script-src 'self'">
    <title>Hello World!</title>
  </head>
  <body>
    <h1>Hello World!</h1>
    We are using Node.js <span id="node-version"></span>,
    Chromium <span id="chrome-version"></span>,
    and Electron <span id="electron-version"></span>.
  </body>
</html>

-------------------------

//index.js
const { app, BrowserWindow } = require('electron')
function createWindow () {
  const win = new BrowserWindow({
    width: 800,
    height: 600
  })

  win.loadFile('index.html')
}
app.whenReady().then(() => {
  createWindow()
})

```


## 打包electron会出现下载包非常慢的情况(cmd翻墙可忽视)
1. 在C:\Users\xxxx\AppData\Local\electron-builder\Cache里面新建nsis和winCodeSign文件夹存放从github下载后解压的文件
2. 链接路径为执行electron打包时给的路径

#### [electron相关配置](https://blog.yasking.org/a/zh-install-electron-development.html)