---
title: JS加减乘除精度丢失问题
date: 2022-05-25 14:02:30
tags: JavaScript
categories: JavaScript
---


## JS 加减乘除精度丢失处理（来源：博客园大佬）

```
export const calc = {
    <!-- 加法函数(d:保留小数的位数) -->
    Add(arg1,arg2){
        arg1 = arg1.toString(),arg2 = arg2.toString();
        let arg1Arr = arg1.split(".),arg2Arr = arg2.split("."),d1 = arg1Arr.length == 2 ? argArr[1] : "",d2 = arg2Arr.length == 2? arg2Arr[1] : '';
        let maxlen = Math.max(d1.length,d2.length);
        let m = Math.pow(10,maxLen);
        let result = Number(((arg1 *m+arg2*m)/m).toFixed(maxLen));
        let d = arguments[2];
        return typeof d === "number" ? Number((result).toFixed(d)) : result;
    }
    <!-- 减法函数 -->
    Sub(arg1,arg2){
        return this.Add(arg1,-Number(arg2),arguments[2])
    }
    <!-- 乘法函数 -->
    Mul(arg1,arg2){
      let r1 = arg1.toString(), r2 = arg2.toString(), m, resultVal, d = arguments[2];
      m = (r1.split(".")[1] ? r1.split(".")[1].length : 0) + (r2.split(".")[1] ? r2.split(".")[1].length : 0);
      resultVal = Number(r1.replace(".", "")) * Number(r2.replace(".", "")) / Math.pow(10, m);
      return typeof d !== "number" ? Number(resultVal) : Number(resultVal.toFixed(parseInt(d)));
    }
    <!-- 除法函数 -->
    Div(arg1,arg2){
      let r1 = arg1.toString(), r2 = arg2.toString(), m, resultVal, d = arguments[2];
      m = (r2.split(".")[1] ? r2.split(".")[1].length : 0) - (r1.split(".")[1] ? r1.split(".")[1].length : 0);
      resultVal = Number(r1.replace(".", "")) / Number(r2.replace(".", "")) * Math.pow(10, m);
      return typeof d !== "number" ? Number(resultVal) : Number(resultVal.toFixed(parseInt(d)));
    }
}

//使用
calc.add(arg1,arg2,d)
OR
calc.add(arg1,arg2)
```