---
title: TypeScript
date: 2020-01-17 16:20:10
tag: TypeScript
categories: [TypeScript]
---


## 初识TS
{% blockquote %}
TypeScript 是 JavaScript 的一个超集，支持 ECMAScript 6 标准。
TypeScript 由微软开发的自由和开源的编程语言。
TypeScript 设计目标是开发大型应用，它可以编译成纯 JavaScript，编译出来的 JavaScript 可以运行在任何浏览器上
{% endblockquote %}
<!-- more -->
## JavaScript 与 TypeScript 的区别
TypeScript 是 JavaScript 的超集，扩展了 JavaScript 的语法，因此现有的 JavaScript 代码可与 TypeScript 一起工作无需任何修改，TypeScript 通过类型注解提供编译时的静态类型检查。
TypeScript 可处理已有的 JavaScript 代码，并只对其中的 TypeScript 代码进行编译。


## 常见类型
 1、布尔类型(boolean)
 2、数字类型(number)
 3、字符串类型{string}
 4、数组类型(array)
 5、元祖类型(tuple)
 6、枚举类型(enum)
 7、任意类型(any)
 8、null和undefined
 9、void类型
 10、never类型


```
// string
let str: string = "hello typescript!!!"
console.log(str)
// boolean
let boo: boolean = true;
console.log(boo);
// number
let num: number = 234234;
console.log(num)

// 数组类型--定义数组类型
// 第一种写法！！！
let arr: number[] = [1, 2, 3, 4]
console.log(arr);
let arr1: any[] = [1, '2', 3, 4]
console.log(arr1);
// 第二种写法！！
let arrs: Array<number> = [2, 3, 4, 5, 6]
console.log(arrs)

// 元祖类型-->每一个位置指定类型利用数组定义类型
let rra: [string, number] = ['123', 234]
console.log(rra);
```

## 枚举类型

{% codeblock %}
enum 枚举名称{
     标识符[=整数常数]
 }
 * 一般用在标识状态码，表示什么类型的错误
 * 如果标识符没有赋值，他的值就是下标

 enum Flag { success = '成功', error = '失败', 'message' = 5 }
let s: Flag = Flag.success;
console.log(s);
{% endcodeblock %}

## 任意类型
```
let anyOne: any = 123123
anyOne = true
console.log(anyOne);

let ele: any = document.getElementsByClassName('box')[0]
ele.style.color = 'red';
```

## null 和undefined 其他(never类型) 数据类型的子类型

let nums: number | null | undefined
console.log(nums);

## void类型 typescript中void标识没有任何类型，一般用于定义方法的时候方法没有返回值

```
function run(): void {
    console.log('没有任何返回值的参数void!!!')
}
run();

//有返回值的情况
function add(a: number, b: number): number {
    return a + b;
}

console.log(add(3, 7))

```

## never类型，是其他类型，(包括null和undefined)的子类型，代表从不会出现的值，这意味着声明never的变量只能为never赋值

```
// let a: never;
// a = (() => {
//     throw new Error('错误')
// })()

// console.log(a);
```
