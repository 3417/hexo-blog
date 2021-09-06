---
title: 前端面试
date: 2020-11-17 17:04:33
tag: 前端面试
categories: [前端面试]
---


## i++和 ++i
```
    i++ 是先赋值在自增 
    ++i是先自增在赋值
```
## 算数运算符
```
+   -    *    /    %[取模求余数]   ++自身加1   --自身减1 
```
<!-- more -->

## HTML5 和 CSS3的新特性
```
HTML5:
1、用于绘画的canvas元素
2、用于媒体回放的video和audio元素
3、对于本地离线存储的更好的支持
4、新的特殊内容元素，比如artice、footer、header、nav、section
5、新的表单控件，比如calender、date、time、email、url、search
CSS3:
1、css3实现圆角border-radius阴影box-shadow
2、对文字加特效text-shadow 线性渐变gradient 旋转 transform
3、transform：
    a.scale -->缩放
    b.translate-->移动
    c.skew-->扭曲
    d.rotate-->旋转
    e.matrix-->矩阵
    f,改变元素基点transform-origin
4、增加了更多的CSS选择器多背景的rgba
5、在css3中唯一引入的伪类元素是::selection
6、媒体查询，多栏布局
7、border-image

4、行内元素
a span img input select....

5、块级元素
div p ul h1 h2...ol dl dt...

区别：
1、块级元素会独占一行，默认占满父级元素
2、行内元素width、height无效
3、块级元素可以设置margin和padding属性
line-height只影响行内元素，并不能直接应用于块级元素。
line-height具有可继承性，块级元素的子元素会继承该特性，并且在行内元素生效。
lin-height 设置为你需要的box的大小可以实现单行文字居中。
只要浮动就脱离了文档流，因此父容器的背景，边框，margin值都不能正常显示，因此需要清除浮动，父容器这些属性显示正常。
常用的清除方式：clear:both; overflow:auto;

display:inline-block什么时候会显示间隙？
1、有空格的时候会有间隙，解决：移除空格
2、margin正值的时候 解决：margin使用负值
3、使用font-size时候 解决：font-szie :0、letter-spacing、 word-spacing

6、空元素
br hr img input meta
```

## 怪异盒模型&&标准盒模型
```
怪异盒子模型：
盒子总的宽度/高度 = width/height + margin，也就是说width = 内容宽度+padding+border;
标准盒子模型：
盒子总的宽度/高度 = width/height+padding+border + margin
box-sizing:border-box/content-box[怪异盒子模型/标准盒子模型]
```

## jquery的事件委托on、delegate、live之间有什么区别？
    1.ive将事件委托给document。
    2.delegate可指定事件委托的对象。
    3.on可以指定事件委托的对象，填了跟delegate作用一致，不填写对自身注册事件。

## 页面导入样式时，link和@import有什么区别?
 1. link属于XHTML标签，而@import完全是css提供的一种方式
 2. @import只能加载CSS
 3. 加载顺序的差别还有兼容性的差别
 4. @import不能用DOM控制
 5. @import可以在css中再次引入其他的样式表

## JS去重
```
    ES6:
        let arr = [1,1,12,3,4,5]
        Array.from(new Set(arr)) OR [...new Set(arr)]
        
    es5:
        let arr = [1,1,2,3,3,4,5,6]
        let arr2 =[];
        for(let i = 0;i <arr.length;i++){
            if(arr2.indexOf(arr[i]) < 0){
                arr2.push(arr[i])
            }
        } 
```

## 函数声明在调用，给数字的原型上扩展一个方法
``` 

    Number.prototype.add = function(data){
        return this + data
    }
    let a = 20;
    let c = a.add(30) // 50
```


## 闭包理解(简单理解)
```
### 不使用let 版本
for(var i = 0;i<10;i++){
    (function(i){
        setTimeout(function(){
            console.log(i)
        },1000*i)
    })(i)
}
### 使用let 版本
for(let i = 0;i<10;i++){
    setTimeout(function(){
        console.log(i)
    },1000*i)
}
```



## 伪类(:) /  伪元素(::)
```
伪类
:visited
:hover
:active
:focus
:not
:nth-child-xxx
...

伪元素
::before
::after
::selection
::placeholder
::first-letter
::first-line
```

## JS的基本数据类型
```
Boolean 布尔类型
String 字符串类型
Null 
undefined
Symbol ES6新增
Number 数字类型
BigInt ES6新增
 null表示一个对象被定义了，但存放了空指针。undefined表示这个值不存在。
复杂类型(引用类型)
Object OR Object/Function //对象-函数
```

## IIFE表达式解决闭包引起的内存泄漏
```
(function(){})() OR (function(){}())
```
## this指向
```
this指的是调用函数的那个对象
this 在没有运行之前不能知道代表谁;js的this 指向是不确定的；和定义没有关系，和执行有关
执行的时候，点前面是谁，this 就是谁；自执行函数里面的this 代表的是 window
定时器书写的时候，window可以省略掉；定时器执行的时候，里面的this 代表的也是 window 
this 是js的一个关键字，随着函数使用场合不同，this 的值会发生变化。
总结：
this 指的是调用函数的那个对象,如果没有被调用，则未知。
this 一般情况下：是全局对象Global。 作为方法调用，那么this 就是指这个对象
```

## node.js使用mongoose中间键来连接MongoDB数据库的

## 箭头函数：(重点！！！)
1. 箭头函数本身是没有this和arguments的，
2. 在箭头函数中引用this实际上是调用的是定义时的上一层作用域的this。
3. 这里强调的是上一层作用域，是因为对象是不能形成独立的作用域的。



## 原生AJAX的写法
```
ajax实现跨域请求基于同源策略
var xhr = new XMLHttpRequest();
xhr.open('方式','URL')
xhr.onreadystatechange = function(){}
xhr.send() //发送数据
xhr.readyState //获取当前的AJAX引擎状态
xhr.status //获取Http状态码
xhr.responseText //获取响应的数据，字符串，需要parse一下
```