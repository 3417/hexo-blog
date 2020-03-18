---
title: Lowdb(一个操作JSON的数据库)
date: 2019-10-02 14:05:28
tags: Lowdb
---

### 序言：
LowDB是基于node的纯JSON文件数据库
数据库被自动存往db.json
你能使用任何lodash方法来查询和操纵数据库

<!-- more -->
### 安装

```
yarn add lowdb OR npm install lowdb
```

### 使用

```
获取
db.get('xxx').find({xxx}).value()
设置
db.set({xxx}).write()
db.get(xxx).push({xxx}).write()
更新
db.get(xxx).find({xxx}).assign({xxxx}).write()
删除
db.get(xxx).remove({xxx}).write()

注意：
value()，write()涉及到数据的更新，添加，删除，获取，必须跟上
```

### [官网](https://github.com/typicode/lowdb) https://github.com/typicode/lowdb