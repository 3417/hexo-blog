---
title: Map-Set
date: 2020-02-25 15:21:47
tags: 
categories: [map-set区别]
---

## Map和Set的区别
区别：
1.set所得元素只有key没有value，value就是key
2.不允许出现键值重复
3.所有元素都会被自动排序
4.不能通过迭代器来改变set的值，因为setZ的值就是键
---分界点----
1.map所有元素都是键+值存在
2.不允许键重复
3.所有的元素是通过键进行自动排序的

<!-- more -->

### Map

```
1、map转换为数组（使用扩展运算符）
const arr =[ [{a:1},111],[b:222]]
[...new Map(arr)]
2、Map与对象的互换
const obj ={}
const map = new Map([a,111],[b,222])
for(let [key,value] of map){
    obj[key] =value
}
console.log(obj) //{a:111,b:222}
```
### Set

```
1、数组去重
[...new Set([1,1,2,3,4,4,5])]
2、合并两个set对象
let a = new Set([1,2,3])
let b = new Set([4,5,6])
new Set([...a,...b])
3、交集
let a = new Set([1,2,3])
let b = new Set([2,3,4])
new Set([...a].filter(x=>b.has(x)))
4、差集
let a = new Set([1,2,3])
let b = new Set([4,3,2])
new Set([...a].filter(x=>!b.has(x)))
```

### 闲谈一句v-model实现子组件像父组件传值
```
//父
<increase v-model="rangeValue"></increase>

export default{
    data(){
        return{
            rangeValue:0
        }
    }
}
//子
<template>
     <button @click="increase">increase</button>
</template>
props: {
    value: {
      type: Number,
      default: 0
    }
  },
methods:{
    increase(){
        this.$emit('input', xxxx) 
    }
}  
```
