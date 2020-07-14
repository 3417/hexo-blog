---
title:  一些CSS的用法
date: 2020-07-14 22:12:33
tags: [css]
categories: [css]
---


### flex 文字换行

```
包裹文字的div
overflow-wrap: break-word;
word-break: break-word;  //兼容IE

顶层父级加上hidden
overflow:hidden
```

### css实现渐变的dashed

```
width: 100%;
height: 1px;
background-image: linear-gradient(to right, #ccc 0%, #ccc 50%, transparent 50%);
background-size: 8px 1px;
background-repeat: repeat-x;
```

### 解决img src为空出现的边框

```
img[src=""],
img:not([src]){
          opacity:0;
     }

```
<!-- more -->

### 变量

```
:root{
    --some-thing:#ececec;
    --some-size--px:40px;
}


.class-variables{
    --some-color:#da7800;
    --some-keword:italic;
    --some-size:1.25em;
    color:var(--some-color);
    font-size:var(--some-size);
    font-size:var(--some-size--px);
}

text-transform：实现英文首字母大写，全部文字大写，小写

CSS实现input框的光标变色
 caret-color:red; 

```

### 文本省略

```
1、单行
text-overflow: ellipsis;
white-space: nowrap;
overflow: hidden;

2、多行(存在兼容性)
display: -webkit-box;
-webkit-box-orient: vertical;
-webkit-line-clamp: 3;  //可以自主选择
overflow: hidden;
```

### 快速重置表单元素
```
(存在兼容性)
button,input...{
    all:unset;
}
```

### 让 HTML 识别 string 里的 '\n' 并换行

```
让 HTML 识别 string 里的 '\n' 并换行
body {
  	white-space: pre-line;
}
```

### 图像灰度

```

img{
    filter:gray;
    -webkit-filter:grayscale(1);
}
```