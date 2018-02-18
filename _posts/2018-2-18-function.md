---
layout: post
title: 函数拓展
tags: Front-end es6
---
# 函数的拓展

## es5回顾

``` js
// 函数声明
function fn() {
	// some code
}

// 函数定义
var fn = function() {
	// some code
}
```
{: .box-note}
## es6拓展
### 函数设置默认值

``` js
// 以前做法一般是这样赋值
function fn(x) {
	x = x || 0;
}
// 现在可以这样做
function fn(x = 0) {
	// some code
}
```
{: .box-note}
### 箭头函数
要说es6最有趣的变化我认为是箭头函数了，优点就是简洁，缺点么就是我认为就是可读性了<br />

``` js
// 用法
let fn = a => a ** 2;
fn(2) // 4

// 相当于es5
var fn = function(a) {
	return Math.pow(a, 2);
}

// 如果没有参数，没有返回值
let fn = () => {
	let a = 5;
	console.log(a);
};
```
{: .box-note}
### rest参数

``` js
var fn = (...values) => {
	let sum = 0;
	for(var num of values) {
		sum += num;
	}
	return sum;
}
fn(1, 2, 3, 5); // 11
```
{: .box-note}
## 参考教程
<a href="http://es6.ruanyifeng.com/#docs/function" target="_blank">阮一峰es6</a>
