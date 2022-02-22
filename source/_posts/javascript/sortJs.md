---
title: 前端排序
date: 2022-02-22 14:21:32
tags:
categories: JavaScript
---

## 冒泡排序
依次比较相邻的两个元素，如果后一个小于前一个，则交换，这样从头到尾一次，就将最大的放到了末尾
<!-- more -->
```
function bubbleSort(arr){
    for(let i=0;i<arr.length-1;i++){
        for(let j=0;j<arr.length;j++){
            if(arr[j] < arr[j+1]){ //此处控制是否升序和降序
                let temp = arr[j+1];
                arr[j+1] = arr[j];
                arr[j] = templ;
            }
        }
    }
    return arr;
}
```
## 选择排序
```
function selectSort(arr){
    let len = arr.length;
    let minIndex,templ;
    for(let i=0;i<len-1;i++){
        minIndex = i;
        for(let j=i+1;j<len;j++){
            if(arr[j] < arr[minIndex]){ //控制升序和降序
                minIndex = j;
            }
        }
        templ = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = templ;
    }
    return arr;
}
```

## 快速排序
```
function insertSort(arr){
    let len = arr.length;
    let preIndex,current;
    for(let i=1;i<len;i++){
        preIndex = i -1;
        current = arr[i];
        while(preIndex >= 0 && arr[preIndex] > current){  //大于current为升序 小于current为降序
            arr[preIndex+1] = arr[preIndex];
            preIndex--;
        }
        arr[preIndex+1] = current;
    }
    return arr;
}
```
