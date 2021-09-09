---
title: 前端压缩图片
date: 2021-09-09 15:18:45
tags: JavaScript
categories: JavaScript
---


## 前端预览图片
```
if(window.createObjectURL != undefined){
    url = window.createObjectURL(file);
}else if(window.URl != undefined){
    url = window.URL.createObjectURL(file);
}else if(window.webkitURL != undefined){
    url = window.webkitURL.createObjectURL(file);
}
```

## 前端上传压缩

```
/*
        三个参数
        file：一个是文件(类型是图片格式)，
        opts：压缩参数{width: 图片宽度, height: 图片高度, quality: 缩放比例，默认0.9}
        callback：回调函数，文件blob
        photoCompress()
         */
export function photoCompress(file, opts, callback) {
    var ready = new FileReader();
    /*开始读取指定的Blob对象或File对象中的内容. 当读取操作完成时,readyState属性的值会成为DONE,如果设置了onloadend事件处理程序,则调用之.同时,result属性中将包含一个data: URL格式的字符串以表示所读取文件的内容.*/
    ready.readAsDataURL(file);
    ready.onload = function () {
        var re = this.result;
        canvasDataURL(re, opts, function (base64Codes) {
            if (opts.wantFile) {
                callback(convertBase64UrlToFile(base64Codes, file.name));
            } else {
                callback(convertBase64UrlToBlob(base64Codes));
            }
        });
    }
}

function canvasDataURL(path, obj, callback) {
    var img = new Image();
    img.src = path;
    img.onload = function () {
        var that = this;
        // 默认按比例压缩
        var w = that.width,
            h = that.height,
            scale = w / h;
        w = obj.width || w;
        h = obj.height || (w / scale);
        var quality = 0.7; // 默认图片质量为0.7
        //如果分辨率大于2000
        if (w > 2000) {
            w = 2000;
            h = (w / scale)
        }
        //生成canvas
        var canvas = document.createElement('canvas');
        var ctx = canvas.getContext('2d');
        // 创建属性节点
        var anw = document.createAttribute("width");
        anw.nodeValue = w;
        var anh = document.createAttribute("height");
        anh.nodeValue = h;
        canvas.setAttributeNode(anw);
        canvas.setAttributeNode(anh);
        ctx.drawImage(that, 0, 0, w, h);
        // 图像质量
        if (obj.quality && obj.quality <= 1 && obj.quality > 0) {
            quality = obj.quality;
        }
        // quality值越小，所绘制出的图像越模糊
        var base64 = canvas.toDataURL('image/jpeg', quality);
        // 回调函数返回base64的值
        callback(base64);
    }
}

/**
 * 将以base64的图片url数据转换为Blob
 * @param urlData
 *            用url方式表示的base64图片数据
 */
function convertBase64UrlToBlob(urlData) {
    var arr = urlData.split(','),
        mime = arr[0].match(/:(.*?);/)[1],
        bstr = atob(arr[1]),
        n = bstr.length,
        u8arr = new Uint8Array(n);
    while (n--) {
        u8arr[n] = bstr.charCodeAt(n);
    }
    return new Blob([u8arr], {
        type: mime
    });
}
```