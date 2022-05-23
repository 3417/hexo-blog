---
title: JS的一些方法
date: 2020-07-14 22:29:00
tags: JavaScript
categories: [JavaScript]
---


### 根据数字生成数组

```
let arr = Array.from({length:30},(v,k)=>k+1)

let arr1 = Array.from(Array(30),(v,k)=>k+1)

```
<!-- more -->
### JS 生成UUID

```
eg:1
function uuid(){
    var s = [];
    var hexDigits = '0123456789abcdef';
    for(var i = 0;i<36;i++){
        s[i] = hexDigits.substr(Math.floor(Math.random()*0x10),1)
    }
    s[14] = '4';
    s[19] = hexDigits.substr((s[19] & 0x3) | 0x8, 1)
    s[8] = s[13] = s[18] = s[23] = "-";
    var uuid = s.join("");
    return uuid;
}


eg2:
function guid(){
    return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g,function(c){
        var r = Math.random()*16|0,v=c=='x'?r:(r&0x3|0x8)
        return v.toString(16)
    })
}

eg3:
function guid(){
    function S4(){
        return (((1+Math.random())*0x10000)|0).toString(16).substring(1);
    }
    return (S4()+S4()+"-"+S4()+"-"+S4()+"-"+S4()+"-"+S4()+S4()+S4());
}
eg4:
function getUuid(len = 32){
    const S4 = () => Math.random().toString(16).substring(2);
    let res = "";
    while(res.length < len){
        res += S4().substring(0,len-res.length);
    }
    return res;
}
```

### 二维数组

```
结构：[ [1,2,3,4],[5,6,7,8] ] ... [ [], [], [] ]

第一种方法：
let a =[1,2,3,4];

for(let i=0; a.length;i++){
    a[i] *= 5/num
}

第二种方法：
a.map(e=>e * 5)

第三种方法：
function scaleMultiply(arr,multiplier){
    for(let i = 0;i< arr.length;i++){
        arr[i] *= multiplier
    }
    return arr;
}
scaleMultiply([1,2,3,4],6); //用法

```

###  矩阵运算

```
function reverseMatrix(sourceArr) {
      let reversedArr = [];
      for (let n = 0; n < sourceArr[0].length; n++) {
        reversedArr[n] = [];
        for (let j = 0; j < sourceArr.length; j++) {
          reversedArr[n][j] = sourceArr[j][n];
        }
      }
      return reversedArr;
    },
    
输入：[[1,2,3],[2,3,4],[5,6,7]]
输出：[[1,2,4],[2,3,6],[3,4,7]] 

```

## 获取文本的确切宽度

```
function getActualWidthOfChars(text,options = {}){
    const {size = 14,family = 'Microsoft YaHei'} = options;
    const canvas = document.createElement('canvas');
    const ctx = canvas.getContext("2d");
    ctx.font = `${size}px ${family}`;
    const metrics = ctx.measureText(text);
    return Math.abs(metrics.actualBoundingBoxLeft) + Math.abs(metrics.actualBoundingBoxRight);
}
```