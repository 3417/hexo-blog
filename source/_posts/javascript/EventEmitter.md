---
title: 发布订阅
date: 2022-02-21 17:21:43
tags: eventEmitter
categories: JavaScript
---


## 发布订阅模式

通过 on 方法注册事件，trigger 方法触发事件，来达到事件之间的松散解耦，并且额外添加了 once 和 off 辅助函数用于注册只触发一次的事件以及注销事件.（相关知识网站总结）

<!-- more -->
```
//定义
class EventEmitter {
    constructor(){
        this.cache = {}
    }
    
    on(name,fn){
        if(this.cache[name]){
            this.cache[name].push(fn)
        }else{
            this.cache[name] = [fn]
        }
    }
    
    off(name,fn){
        const tasks = this.cache[name]
        if(tasks){
            const index = tasks.findIndex((f)=>f === fn || f.callback === fn);
            if(index >=0){
                tasks.splice(index,1)
            }
        }
    }
    emit(name,once = false){
        if(this.cache[name]){
            const tasks = this.cache[name].slice()
            for(let fn of tasks){
                fn()
            }
            if(once){
                delete this.cache[name]
            }
        }
    }
}

//使用
const eventBus = new EventEmitter();
const task1 = ()=>{console.log('task1')}
const task2 = ()=>{console.log('task2')}

eventBus.on('task',task1);
eventBus.on('task',task2);
eventBus.off('task',task1);
setTimeout(()=>{
    eventBus.emit('task');
},1000)
```
