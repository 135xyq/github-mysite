---
title: 1688. 比赛中的配对次数
date: 2022-01-25 15:19:20
description: 1688. 比赛中的配对次数 模拟&直接观察规律
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js

---


# 1688. 比赛中的配对次数 模拟&直接观察规律

## [查看原题](https://leetcode-cn.com/problems/count-of-matches-in-tournament/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/b81b650b52404ca59426123c2ed6648b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(模拟)

一步步模拟出比赛的步骤，直到剩下一名选手。

## 代码

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var numberOfMatches = function(n) {
	let count = 0;
	while(n > 1){
		let temp = Math.floor(n / 2);
		count += temp;
		n = Math.ceil(n / 2);
	}
	return count ;
};
```

![](https://img-blog.csdnimg.cn/05b1556140674d6fada991be1b1a903b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)







## 解题思路(找规律)

因为要淘汰n-1名选手，所以要比赛n-1次


## 代码

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var numberOfMatches = function(n) {
	return n - 1;
};
````
![在这里插入图片描述](https://img-blog.csdnimg.cn/ce8467c2816f46c68af5c63255a4f2a3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)