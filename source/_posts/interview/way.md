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


# 2024年06月


## 防抖节流函数(高频事件)

```
    防抖：  触发高频事件后n秒后执行一次，如果n秒内再次触发，则重新计时
    function debounce(fn, delay) {
        let timer = null;
        return function () {
            if (timer) clearTimeout(timer);
            timer = setTimeout(() => {
                fn.apply(this, arguments);
            }, delay);
        };
    }

    节流：  触发高频事件后n秒内函数只能执行一次，如果n秒内连续触发，只有一次生效
    function throttle(fn, delay) {
        let isThre = false;
        return function () {
            if(!isThre){
                fn.apply(this, arguments);
                isThre = true;
                setTimeout(function() {  
                   return isThre = false;  
                 }, delay);
            } 
        };
    }



```


## 为什么vue/react项目中要使用key，有什么作用？

key是给每一个vnode的唯一id  可以更依赖key更准确更快的拿到oldVnode中对应的vnode节点

## ['1','2','3'].map(praseInt)

结果：log: [1,NaN,NaN]

## bind call apply区别

1. 三者都可以改变函数的this对象指向
2. 三者第一个参数都是this的指向对象，如果没有这个参数或参数为undefined/null，则默认指向全局window
3. 三者都可以传参数，但是apply是数组或类数组，而call是参数列表，且apply和call是一次性传入参数，而bind可以分为多次传入
4. bind是返回绑定this之后的函数，apply、call则是立即执行

## es5和es6区别

1. 变量声明方式不同
2. 块级作用域
3. 箭头函数
4. 字符串模板
5. 类和继承
6. 模块化
7. 解构赋值
9. Promise
10. 新增Set/Map/Symbol方法等


## 详解作用域链、原型链、闭包

1. JavaScript的作用域我们可以有效访问变量或函数的区域，JS具有三种类型的作用域：全局作用域、函数作用域和块级作用域
2. 原型链：JavaScript中每个函数都有一个prototype属性，这个属性指向函数的原型对象，原型对象也是个对象，原型对象有一个constructor属性，指向构造函数，原型对象可以添加共有属性和方法，实例对象可以访问原型对象上的属性和方法
3. 闭包：闭包是函数和函数外部变量的引用，闭包可以访问函数外部变量，函数外部变量可以访问闭包变量
4. 作用域链：内部函数访问外部函数的变量，采取的是链式查找的方法来决定那个结构，这种结构称之为作用域链

## 关于this

注：this是执行上下文中的一个属性，他指向最后一次调用这个方法的对象，在实际开发中 this的指向可以通过四种调用模式来判断
1. 函数调用模式：this指向全局对象
2. 方法调用模式：this指向调用方法的对象
3. 构造函数调用模式：this指向构造函数的实例对象
4. apply/call/bind调用模式：this指向第一个参数

## 异步编程的实现方式

1. 回调函数
2. Promise
3. Generator
4. async/await  是Generator和promise实现的一种自动执行的语法糖


## 相关算法

```
    回文字符含义：指的是正着读和倒着读都一样的字符串
    function isPalindrome(str){
    return str === str.split('').reverse().join('');
    }
    console.log(isPalindrome('madam'));

      1. 实现字符串得排列组合
      function permute(str,prefix=''){
        if(!str) return '';
        for(let i=0;i<str.length;i++){
          permute(str.slice(0,i)+str.slice(i+1),prefix+str[i]);
        }
      }
      2.找出数组中最大的值、最小值、地k大/小的元素等

      // 最大值
      const max = Math.max(...arr);
      // 最小值
      const min = Math.min(...arr);
      //第k大的元素
      function findRandMax(arr,k){
        const sortList = arr.sort((a, b) => a - b);
        return sortList[k-1];
      }

      3.数组排序算法，如快速排序、归并排序
      
      //快速排序算法（是一种高效的排序算法，采用分治策略来把一个序列分为较小和较大的两个子排序，然后在递归地对子序列进行排序）
      function quickSort(arr){
        if(arr.length <= 1) return arr;

        const pivot =arr[0];
        const left = [];
        const right = [];
        for(let i=1;i<arr.length;i++){
          if(arr[i] < pivot){
            left.push(arr[i]);
          }else{
            right.push(arr[i])
          }
        }
        return quickSort(left).concat(pivot,quickSort(right));
      }

      //归并排序算法(归并算法也是基于一种分治法的排序算法，他将数组分成两半，递归地排序每一半，然后将结果合并成一个有序的数组)
      const merge = (left,right)=>{
        let result = [],i=0,j=0;
        while(i<left.length && j<right.length){
            if(left[i] < right[j]){
              result.push(left[i]);
              i++;
            }else{
              result.push(right[j]);
              j++;
            }
        }
        return result.concat(left.slice(i)).concat(right.slice(j));

      }
      function mergeSort(arr){
        if(arr.length <= 1) return arr;
        const mid = Math.floor(arr.length / 2);
        const left = arr.slice(0,mid);
        const right =arr.slice(mid);

        return merge(mergeSort(left),mergeSort(right));
      }  

    // 封装一个类实现自增

    class addCount {
        constructor(count=0){
            this.count = count;
        }
        getCount(){
            return this.count;
        }
        addCount(){
            this.count++;
        }
    }
    let result = new addCount();   
    console.log(result.addCount())
    console.log(result.getCount()) 

```

