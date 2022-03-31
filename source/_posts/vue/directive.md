---
title: Vue常用的一些指令
date: 2021-09-07 14:15:02
index_img: /img/vue/directive.jpg
banner_img: /img/vue/directive.jpg
tags: [Vue]
categories: [Vue]
---

{% note success %}
来源于掘金、思否等...相关网站
{% endnote %}

# 以下指令都是基于Vue2.xx
<!-- more -->

## v-permission(按钮级的权限控制)

```
//请求后台获取到的权限数据
function checkArray(key) {
  let arr = ['1', '2', '3', '4']
  let index = arr.indexOf(key)
  if (index > -1) {
    return true // 有权限
  } else {
    return false // 无权限
  }

  //简化版
  //return permissionList.includes(key)
}

const permission = {
  inserted: function (el, binding) {
    let permission = binding.value // 获取到 v-permission的值
    if (permission) {
      let hasPermission = checkArray(permission)
      if (!hasPermission) {
        // 没有权限 移除Dom元素
        el.parentNode && el.parentNode.removeChild(el)
      }
    }
  },
}

export default permission
```


## v-waterMarker(水印)

```
function addWaterMarker(str, parentNode, font, textColor) {
  // 水印文字，父元素，字体，文字颜色
  var can = document.createElement('canvas')
  parentNode.appendChild(can)
  can.width = 200
  can.height = 150
  can.style.display = 'none'
  var cans = can.getContext('2d')
  cans.rotate((-20 * Math.PI) / 180)
  cans.font = font || '16px Microsoft JhengHei'
  cans.fillStyle = textColor || 'rgba(180, 180, 180, 0.3)'
  cans.textAlign = 'left'
  cans.textBaseline = 'Middle'
  cans.fillText(str, can.width / 10, can.height / 2)
  parentNode.style.backgroundImage = 'url(' + can.toDataURL('image/png') + ')'
}

const waterMarker = {
  bind: function (el, binding) {
    addWaterMarker(binding.value.text, el, binding.value.font, binding.value.textColor)
  },
}

export default waterMarker
<!-- --------------------------------------------分割线---------------------------------------------- -->
<!-- 另一个版本 -->
const watermark =(props)=> {
  const {
    width='300px',
    height='300px',
    textAlign='center',
    verticalAlign='center',
    font='18px Microsoft Yahei',
    fillStyle='rgba(100,100,100,.2)',
    contnet='机密内容',
    rotate=-20
  }= props

  const canvas = document.createElement('canvas');
  const ctx = canvas.getContext('2d');
  canvas.setAttribute('width',width);
  canvas.setAttribute('height',height);
  ctx.textAlign = textAlign;
  ctx.verticalAlign = verticalAlign;
  ctx.font = font;
  ctx.fillStyle = fillStyle;
  ctx.rotate(Math.PI / 100 * rotate);
  ctx.fillText(content,parseFloat(width) / 2,parseFloat(height) / 2)
  const base64Url =canvas.toDataURL('image/png',.92);
  const _wm = document.querySelector('._wm');
  const watermarkDiv = _wm || document.createElement('div');
  const styleStr = `
    width:100%;
    height:100%;
    position:absolute;
    top:0;
    left:0;
    background:url(${base64Url});
    pointer-events:none;
  `
  watermarkDiv.setAttribute('style',styleStr);
  watermarkDiv.classList.add('_wm');
  if(!_wm){
    container.style.position = 'relative';
    container.insertBefore(watermarkDiv,container.firstChild);
  }
  const MutationObserver = window.MutationObserver || window.WebKitMutationObserver;
  if(MutationObserver){
    let observer = new MutationObserver(()=>{
      const _wm = document.querySelector('._wm');
      if((_wm && _wm.getAttribute('style')!== styleStr) || !_wm){
        observer.disconnect();
        observer = null;
        watermark(props);
      }
    })
    observer.observer(container,{
      attributes:true,
      childList:true,
      characterData:true,
      subtree:true
    })
  }
}

export {watermark};


```

## v-conversion(KB-MB-GB转换)

```
const filterData = (size)=>{
    const KB = 1024 // kb
    const MB = 1024 * 1024 // mb
    const GB = 1024 * 1024 * 1024 // gb
    if(size < KB)return size +'B'
    else if(size < MB)return (size / KB).toFixed(2) +'KB'
    else if(size < GB)return (size / MB).toFixed(2) +'MB'
    else return (size / GB).toFixed(2) + 'GB';
}

directives:{
    conversion:{
        inserted(el,binding,vnode){
            filterData(binding.value)
        }
    }
}
```

## v-debounce(防抖)

```
const debounce = {
  inserted: function (el, binding) {
    let timer
    el.addEventListener('click', () => {
      if (timer) {
        clearTimeout(timer)
      }
      timer = setTimeout(() => {
        binding.value()
      }, 1000)
    })
  },
}

export default debounce
```

## v-throttle(节流)

```
const throttle = {
  inserted: function (el, binding) {
    function throttleIn(fun, delay) {
        let last, deferTimer;
        return function () {
            let that = this;
            let _args = arguments;
            let now = +new Date();
            if (last && now < last + delay) {
                clearTimeout(deferTimer);
                deferTimer = setTimeout(function () {
                    last = now;
                    fun.apply(that, _args)
                }, delay)
            } else {
                last = now;
                fun.apply(that, _args);
            }
        }
    }
    const throttleFn = throttleIn(binding.value,1000);
    el.addEventListener('mousemove', () => {
        throttleFn('move一次')
    })
  },
}

<!-- 简化版本 -->
function throttleIn (fun:any, delay:number){
    let previous:number = 0;
    return function () {
        let that = this;
        let _args = arguments;
        let now = +new Date();
        if (now - previous > delay) {
            fun.apply(that, _args)
            previous = now;
        }
    }
}

export default throttle
```

## v-fixed(全局指令注册)
```
  Vue.directives:{
    fixed:{
      inserted(){
        let scrollTop = document.body.scrollTop || document.documentElement.scrollTop
        document.body.style.cssText +='position:fixed;overflow:hidden;width:100%;top:-'+scrollTop+'px;'
      },
      unbind(){
        let body = document.body,top = body.style.top;
        document.body.scrollTop = document.documentElement.scrollTop = -parseInt(top);
        body.style.position = '';
        body.style.top = '';
        body.style.overlfow = 'initial';
      }
    }
  }
```

## 批量注册自定义指令
```
const directives = {
    xxx,
    debounce:{
        inserted:funciton(el,binding){}
        ....
    },
    ....
}

export default {
    install(Vue){
        Object.keys(directives).forEach(key=>{
            Vue.directive(key,directives[key])
        })
    }
}
```