---
title: 1725. 可以形成最大正方形的矩形数目
date: 2022-02-04 13:53:45
description: 1725. 可以形成最大正方形的矩形数目 一次遍历
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 1725. 可以形成最大正方形的矩形数目 一次遍历

## [查看原题](https://leetcode-cn.com/problems/number-of-rectangles-that-can-form-the-largest-square/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/ed8411fc2e414f1e989b03f360549561.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

一次遍历数组，求出每一个矩形所能分割出的最大正方形，再判断当前项是否是最大值，如果是最大值则将正方形的数量加一；如果比当前的最大值大则更新最大值，并且将最大值的个数从1开始重新计数。

## 代码

```javascript
/**
 * @param {number[][]} rectangles
 * @return {number}
 */
var countGoodRectangles = function(rectangles) {
	let count = 0;
	let maxLen = 0;
	let temp = null;
	rectangles.forEach(item=>{
		temp = Math.min(...item);
		if(temp > maxLen){
			maxLen = temp;
			count = 1;
		}else if(temp === maxLen){
			count++;
		}
	})
	return count;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/616d0e8d9c9046e0869589d807879634.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
