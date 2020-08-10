---
title: console
date: 2020-08-10 23:40:03
tags: console
categories: [console]
---


## 基础
1. console.log()
2. console.info()
3. console.debug()
4. consle.warn()
5. console.error()
<!-- more -->

## 拓展

```
console.table()以表格的形式输出数据。这个方法最适用的场景我觉得是对象的数组
console.assert() 条件性输出,条件不满足时才会输出
console.group() 为输出内容添加一定的缩进来整理好内容
console.trace() 追踪函数的执行栈
console.count() 统计代码的执行次数
console.time() 记录代码执行的耗时，以毫秒（ms）为单位

替换字符串 - string substitution
console.log("%o is xxxxx %f xxx",{name:"Sean"},18,99.5)
console.log("%c superMan","color:red;xxxxx");
````