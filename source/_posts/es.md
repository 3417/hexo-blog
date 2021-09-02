---
title: ES新特性
date: 2020-02-24 14:34:13
tags: JavaScript
categories: [JavaScript]
---

## ES新特性
{% blockquote %}
ES是国际标准化组织发布的浏览器脚本语言的标准，全名：ECMAScript。
ES是JS语言的国际标准，JS是ES的实现。在日常场合，两个词可以互换。
ES是JS的子集，它是JS的内容的一部分，一个完整的JS实现是由以下三部分组成：
核心（ESMAScript）：规定了JS的语法、类型、语句、关键字、保留字、操作符、对象
{% endblockquote %}

<!-- more -->

### ES6(ES2015)
1.类
{% codeblock %}
class Animal{
     constructor(name,run) {
      this.name = name;
      this.run = run;
    }
    Run() {
      console.log('name:' + this.name + ',run:' + this.run);

    }
}

let animals = new Animal('Cat','Running')
animals.Run(); //name:Cat,run:Running
{% endcodeblock %}
2.模块化
{% codeblock %}
export const name ='Yellow'

//test.js
let name = 'Test',age='25';
export{name,age}


//导出函数
export function test(msg){
    return msg
}

//导入
import {modulesName} from 'xxxxx'
import {moduleA,moduleB} from 'xxxx'
{% endcodeblock %}
3.箭头函数
{% codeblock %}
()=>1
v=>v+1
(a,b)=>a+b
()=>{
    xxxx
}
{% endcodeblock %}
4.函数参数默认值(有局限性)
{% codeblock %}

function (name="张三",color="yellow"){
    //.....
}

{% endcodeblock %}
5.模板字符串
{% codeblock %}
`${name}在干嘛？`
{% endcodeblock %}
6.解构赋值
{% codeblock %}
let foo =['one','two','three','four']
let [one,two,three] = foo

//如果需要湖绿某些值
let [frist,,,last] = foo

let a,b;
[a,b] =[1,2]
console.log(a) //1
console.log(b) //2
//改变默认值
let c,d;
[c=1,d=6] =[1]
console.log(c) //1
console.log(d) //6

//交换两个变量的值
let e =1,f=2;
[e,f] = [f,e]

console.log(e) //2
console.log(f) //1

//获取对象中的值
const stu = {
    name:"张三",
    age:25,
    city:"成都"
}

const {name,age,city} = stu;

console.log(name) //张三
console.log(age) //25
console.log(city) //成都
{% endcodeblock %}
7.延展操作符
{% codeblock %}
//姑且自己叫做展开运算符吧
1、在函数调用/数组构造时, 将数组表达式或者string在语法层面展开；还可以在构造对象时, 将对象表达式按key-value的方式展开
function sum(x, y, z) {
  return x + y + z;
}
const numbers = [1, 2, 3];

//不使用延展操作符
console.log(sum.apply(null, numbers));

//使用延展操作符
console.log(sum(...numbers));// 6

//构造数组
const stuendts = ['Jine','Tom']; 
const persons = ['Tony',... stuendts,'Aaron','Anna'];
conslog.log(persions)// ["Tony", "Jine", "Tom", "Aaron", "Anna"]

//数组拷贝
var arr = [1, 2, 3];
var arr2 = [...arr]; // 等同于 arr.slice()
arr2.push(4); 
console.log(arr2)//[1, 2, 3, 4]

//链接多个数组
var arr1 = [0, 1, 2];
var arr2 = [3, 4, 5];
var arr3 = [...arr1, ...arr2];// 将 arr2 中所有元素附加到 arr1 后面并返回
//等同于
var arr4 = arr1.concat(arr2);

//合并对象
var obj1 = { foo: 'bar', x: 42 };
var obj2 = { foo: 'baz', y: 13 };

var clonedObj = { ...obj1 };
// 克隆后的对象: { foo: "bar", x: 42 }

var mergedObj = { ...obj1, ...obj2 };
// 合并后的对象: { foo: "baz", x: 42, y: 13 }


{% endcodeblock %}
8.对象属性简写
{% codeblock %}
const name='Ming',age='18',city='Shanghai';
   
const student = {
    name:name,
    age:age,
    city:city
};
console.log(student);//{name: "Ming", age: "18", city: "Shanghai"}

const name='Ming',age='18',city='Shanghai';
  
const student = {
    name,
    age,
    city
};
console.log(student);//{name: "Ming", age: "18", city: "Shanghai"}


{% endcodeblock %}
9.Promise
{% codeblock %}
var waitSecond = new Promise(function(resolve, reject)
{
    setTimeout(resolve, 1000);
});

waitSecond
    .then(function()
    {
      console.log("Hello"); // 1秒后输出"Hello"
      return waitSecond;
    })
    .then(function()
    {
        console.log("Hi"); // 2秒后输出"Hi"
    });


{% endcodeblock %}
10.Let与Const
{% codeblock %}
在之前JS是没有块级作用域的，const与let填补了这方便的空白，const与let都是块级作用域。
{
  var a = 10;
}

console.log(a); // 输出10

{
    let a =10
}
console.log(a) //ReferenceError: a is not defined"
{% endcodeblock %}


### ES7(ES2016)
1.数组includes()方法，用来判断一个数组是否包含一个指定的值，根据情况，如果包含则返回true，否则返回false
{% codeblock %}
let arr = ['react', 'angular', 'vue'];

if (arr.includes('react'))
{
    console.log('react存在');
}

{% endcodeblock %}
2.a ** b指数运算符，它与 Math.pow(a, b)相同。
{% codeblock %}
    console.log(2**10);// 输出1024
{% endcodeblock %}
### ES8(ES2017)
1.async/await
{% codeblock %}
    async function process(array){
        for await (let i of array){
            //.....
        }
    }
{% endcodeblock %}
2.Object.values()[Object.values()是一个与Object.keys()类似的新函数，但返回的是Object自身属性的所有值，不包括继承的值]
{% codeblock %}
const vals=Object.keys(obj).map(key=>obj[key]);
console.log(vals);//[1, 2, 3]

{% endcodeblock %}
3.Object.entries()[Object.entries()函数返回一个给定对象自身可枚举属性的键值对的数组]
{% codeblock %}
for(let [key,value] of Object.entries(obj1)){
	console.log(`key: ${key} value:${value}`)
}
//key:a value:1
//key:b value:2
//key:c value:3


{% endcodeblock %}
4.String padding
{% codeblock %}
String.padStart(targetLength,[padString])
targetLength:当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。
padString:(可选)填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断，此参数的缺省值为 " "
console.log('0.0'.padStart(4,'10')) //10.0
console.log('0.0'.padStart(20))// 0.00    
{% endcodeblock %}

{% blockquote %}
以上信息都来自于掘金网站，地址为:(https://juejin.im/post/5ca2e1935188254416288eb2)
{% endblockquote %}