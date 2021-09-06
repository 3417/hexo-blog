---
title: Input预览图片美化上传框
date: 2020-08-10 23:35:21
tag: JavaScript
categories: [JavaScript]
---


## 美化上传input type="file"
```
html:
    <div class="logo">
        <input type="file" accept="image/*" capture="camera" @change="handleChange"/>
    </div>
    
css:
    .logo {
      position: relative;
      width: 46px;
      height: 46px;
      display: inline-block;
      overflow: hidden;
      background-color: #ffc8c8;
  //input样式
  input {
    position: absolute;
    font-size: 100px;
    right: 0;
    top: 0;
    opacity: 0;
    filter: alpha(opacity=0);  //兼容IE
    cursor: pointer; 
  }
  //图片预览样式
  #avator {
    display: inline-block;
    width: 100%;
    height: 100%;
  }
}  

```

<!-- more -->

## new FileReader() 实现base64预览
```
handleChange(event) {
      let file = event.target.files[0];
      // 新建文件读取器
      let reader = new FileReader();
      reader.readAsDataURL(file);
      reader.onload = function(e) {
        //  e.target.result = data:image/jpeg;base64,/9j/4AAQSk
        document.getElementById("avator").src = e.target.result;
      };
      console.log(file);
    }
```