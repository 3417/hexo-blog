---
title: 前端面试2025
date: 2025-08-19 19:36
tag: 前端面试2025
categories: [前端面试]
description: 2025年 失业潮下 寻找前端职位的相关面试心得
---


> 前言：2025年注定是一个不平凡的一年
很多人把面试看作一次单纯的考核，但对我来说，它更像是一场自我检验。每一次面试，都是一次与自己对话的机会。这篇文章，就记录了我在前端面试中的收获和反思。



### 天府市民云的外包面试


JS基础相关知识的考核：
1. for 循环的 break;  containue;  会跳出循环并且会打印 相关的值 注意是打印判断条件前的值
```
for(let i =0;i<100;i++){
    if(i<=50){
        break;
        containue;        
    }    
    console.log(i) // 0-50
}

```

2. Promise 打印console.log的问题

```
new Promise((resolve, reject) {
    console.log(1);
    resolve();
    console.log(2);
}).then(() {
    console.log(3);
});

console.log(4);
// 执行结果： 1 2 4 3
```

3. Vue基础问题
Vue如何实现类型v-model这样的双向绑定事件
```
基于Vue2的版本实现是 .async
基于Vue3的版本实现是 v-model:default


Vue2的实现方式：；
<comp :foo.sync="bar"></comp>  等同于 <comp :foo="bar" @update:foo="val => bar = val"></comp>

child:
$emit('update:foo', val)；



Vue3的实现方式：
<comp v-model="value" /> 等价于 <comp :modelValue="value" @update:modelValue="val=> value = val"/>  默认是modelValue 但是也可以扩展
v-model:data="value"  AND  emit('update:data',value);

```


4. CDN为什么访问快？
- 地理位置靠近，缓存机智，负载均衡，多协议支持 

5. 浏览器的相关策略

- 资源加载优化，
- 渲染优化，
- 缓存策略，
- 安全策略-内容安全策略，通过HTTP响应头限制资源加载源，防止XSS等攻击
- 同源策略，限制不同源的DOM操作和资源访问，防止跨域攻击
- Https加密  强制使用SSL/TLS加密传输，保障数据安全并提升SEO排名

6. TypeScript相关问题 （主要问了些辅助函数的使用  并没有更加深入的问题）


## 薪玺熠科技

1. forEach如何中断循环

```
const arr = [1, 2, 3];
arr.forEach((item, index, array) => {
  if (item === 2) array.length = 0; // 清空数组终止循环
  else console.log(item); // 输出 1
});

```
2. 闭包用在那些地方

- 封装私有变量
- 创建函数工厂
- 回调函数和事件处理
- 函数柯里化
- 模块化开发
- 解决循环中的变量共享问题
- 记忆化
- 防抖和节流

3. 防抖和节流的区别和应用场景

- 防抖：在事件被触发n秒后再执行回调，如果在这n秒内事件又被触发，则重新计时。
- 节流：在事件被触发n秒后再执行回调，如果在这n秒内事件被触发，则不会执行。

```
防抖场景:输入搜索、resize窗口、表单验证
节流场景:鼠标移动、拖拽、滚动


事例代码：
function debounce(fn, delay) { 
    let timer;
    return function(...args) { 
        clearTimeout(timer);
        timer = setTimeout(() => {
            fn.apply(this, args);
        },delay)
    }
}

function throttle(fn, delay) { 
    let timer;
    return function(...args) {
        if(!timer){
            fn.apply(this, args);
            timer = setTimeout(()=>{
                timer = null;
            },delay)
        }
    }
}
```

4. new WeakMap 和 new Map的区别
- WeakMap 的键必须是对象 数组  函数等等 不能使用原始的值 如字符串 数字 布尔值
- Map 的键可以是任意类型包括对象、原始值、符号等。



## 滴滴外包面试

1. （微任务和宏任务相关）

```
console.log(1);
setTimeout(()=>{
    console.log(2)
    Promise.resolve().then(()=>{
        console.log(3);
    })
    console.log(4);
},0)
new Promise((resolve)=>{
    console.log(5);
    resolve();
}).then(()=>{
    console.log(6);
}).then(()=>{
    console.log(7);
})
console.log(8);
//  执行结果：1,5,8,6,7 2,4,3

let obj = {
    name :'test',
    sayName:function(){
        let self = this;
        console.log(this.name);
        console.log(self.name);
        (function(){
            console.log(this.name); // undefined
            console.log(self.name); // test
        })()
    }
}
obj.sayName(); // test test undefined test
const func = obj.sayName;
func(); // undefined undefined undefined undefined
```
2. Vue相关面试题
Vue中父子组件 里面执行的顺序是什么？
+ 父组件先执行，子组件后执行
+ 父组件先走到 beforeMount，开始渲染子组件 → 子组件完整挂载 → 再回到父组件 mounted。（更新和销毁就同理）

```
父：beforeCreate-created-beforeMount
  子：beforeCreate-created-beforeMount-mounted
父：mounted
```

3. MVC和MVVM的区别?
+ MVC-Model View  Controller
+ MVVM-Model View  ViewModel
- MVC 核心是控制器 View和Model之间的联系通过Controller来管理
- MVVM 核心是数据绑定- 数据驱动视图发生变化

总结来说：
+ MVC 是传统架构，核心是 Controller，用户操作需要通过 Controller 去更新 Model，再由 Controller 渲染 View。
+ MVVM 是改进后的模式，引入了 ViewModel，利用数据双向绑定，使 View 和 Model 自动保持同步。	
+ MVC 适合服务端渲染和传统框架，而 MVVM 更适合现代前端框架（Vue、Angular），开发效率更高。

延伸问题：那么Vue中 script这块功能属于MVVM中那一层模块？
1. script 模块是 MVVM 架构中的 ViewModel 模块，它负责处理数据逻辑，并把数据传递给 View 层。
2. script 模块中的 data 属性是 MVVM 架构中的 Model 模块，它负责存储数据，并把数据传递给 View 层。


4. JS相关问题
+ 原型和原型链？

在 JavaScript 中，每个对象都有一个内部属性 
[[Prototype]]，即 __proto__构造函数有一个 prototype 属性，实例对象的 __proto__ 会指向构造函数的 prototype。访问对象属性时，会先在对象本身查找，如果没有，就沿着 __proto__ 链向上查找，这条查找路径就是 原型链。原型链的尽头是 Object.prototype.__proto__ = null。


5. 浏览器缓存有哪些  cookie有哪些优缺点？？？
+ 首先浏览器缓存：
- 强缓存（本地缓存 不会发送到服务端，直接用本地文件）   
- 协商缓存 (强缓存通过 Expires 或 Cache-Control 控制，直接用本地缓存；协商缓存通过 ETag 或 Last-Modified 与服务器比对，未更新则返回 304)
+ cookie的优缺点：
- 优点：兼容性强，自动携带 持久存储 可设置作用域
- 缺点：存储容量小，性能问题，安全隐患，操作复杂

## 壹立科技面试

1. Vue中nextTick是什么任务？
微任务，兼容IE的情况下就是宏任务

2. React中 React.memo  和 useMemo的问题和区别？
* React.memo 是一个高阶组件，用于缓存组件的渲染结果，从而避免不必要的重新渲染，适用于优化纯组件。会对props进行一个比较 来判断是否渲染
* useMemo 是一个 Hook，用于缓存计算结果，它帮助避免昂贵的计算在每次渲染时重新执行，适用于性能优化，尤其是对于计算密集型的操作。
* ajax 是宏任务 浏览器中得IO流都是宏任务。



面试总结：
1. 其中滴滴的外包面试给我的收获挺大的，也了解到自身的一些不足 以及对面试的准备不充分的问题。
2. 每次的面试让我清楚地看到自己的短板：不仅仅是技术上的深度，还包括面试表达和现场 coding 的稳定性。虽然没能完全发挥理想状态，但每一次都是很好的自我检验。