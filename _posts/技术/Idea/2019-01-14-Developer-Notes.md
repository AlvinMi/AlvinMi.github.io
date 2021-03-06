---
layout: post
title: Developer-Notes
category: 资源
tags: "资源 前端 idea"
keywords: 资源,工具,积累
published: true
---

[个人开发笔记总结！](https://alvinmi.github.io/Developer-notes/)

# 前端

> 个人技术总结、答疑积累，同时可做面试参考！

## JavaScript

>闭包、IIFE、this、prototype 及一些底层知识(ES、VO、AO)， 新的 ES6 特性 class、module、arrow function

1.闭包？

1.1.闭包作用，缺点？

2.原型链？

3.继承？

4.自己平时在项目中如何封装()?

5.script 标签中 defer 和 async 的区别？

6.深浅拷贝的区别和用途？

7.ES 里的 Generator 是怎么运行的？ 和 async + await 有什么区别？

8.

## CSS

1.CSS 有哪些实现布局的方式？

2.CSS 命名冲突如何解决？

3.

## Vue

1.Vue 双向绑定原理？

2.Vue 生命周期？

```
即 Vue 的 8 个生命周期阶段： beforeCreate(创建前) → created(创建后) → beforeMount(载入前) → mounted(载入后) → beforeUpdate(更新前) → Updated(更新后) → beforeDestroy(销毁前) → destroyed(销毁后)
```

2.1.Vue 生命周期的作用？

```

```

2.2.第一次页面加载会触发哪几个钩子？

```
第一次页面加载会触发： beforeCreate、created、beforeMount、mounted 这几个钩子。
```

2.3.DOM 渲染在哪个生命周期就已经完成？

```
DOM 在 mounted 中就已经完成。
```

3.Vue Router 中 query 和 param 的区别？

4.Vue 的 data 为什么只能是函数，而不能是对象呢？

## React

1.React 里的 key 有什么用？

2.React 里什么时候用 Context？

3.reader props 是什么？ 什么时候用？

4.路由如何做权限校验？

## node.js

1.写一个小服务可以通过 URL 下载文件？ (大文件是否能下载) stream。

## 打包工具

1.webpack

## 浏览器

1.一般看是不是浏览器 bug，就看不同浏览器表现是否相同。

## 常用网络

1.什么是 Ajax ?
2.GET/POST 之间的差异?

## 移动端适配

>最近看了很多移动适配的文章，还没消化，先积累着。搞懂移动端适配问题，先明白像素和视口。

1.设备的像素？

设备像素 (device pixel, dp): 又称为物理像素。单位 pt。pt 在 css 单位中属于真正的绝对单位，1pt = 1/72 (inch), inch 及英寸，而 1 英寸等于 2.54 厘米。所以设备像素的特点就是大小固定，不可变。比如 iPhone 5 的分辨率为 640 x 1136px.

2.CSS 像素?

在 CSS、JS 中使用的一个抽象的概念，单位是 px。
>CSS 像素也可以称为设备独立像素 (device-independent pixels)，简称为 dips，单位是 dp。



[DPI 计算/PPI 计算参考网站](https://www.sven.de/dpi/)

## 前端安全防范知识

1.XSS？

2.CSP？

3.CSRF？

4.rAF 

等...
