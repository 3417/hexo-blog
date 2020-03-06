---
title: Vue项目使用SCSS使用全局变量
date: 2019-12-29 14:05:59
tags: [Vue,sass]
---


## Vue.config.js,使用全局的sass变量
```
css:{
    loaderOptions:{
        sass:{
            data: `@import "@/assets/styles/_variable.scss"`;
        }
    }
}
```
<!-- more -->
## Vue 中使用“scss”,"sass"

```
如何在vue中使用sass OR　scss
<style lang="sass">
如果出现错误提示：无效的css。因为sass语法不使用大括号和分号。
如果你喜欢使用不带大括号的语法，只要去掉css代码的大括号和分号，即使用缩进语法。
如果你希望使用带大括号的语法，即SCSS
那么，你只要把lang="sass"改成lang="scss"就行了。
```

