---
title: 539. 最小时间差
date: 2022-01-18 11:44:52
description: 539. 最小时间差 将时间转为数字进行比较
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 539. 最小时间差 将时间转为数字进行比较

## [查看原题](https://leetcode-cn.com/problems/minimum-time-difference/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/4cf97b6a15c8428da07e5f09c298ec89.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)


## 解题思路

将时间转为一天中的多少分钟

1. 使用split将时间按照':'分为小时和分钟，再将小时转为分钟存到数组arr中
2. 将arr排序(升序),再遍历求出相邻元素的最小差值min
3. 注意要比较第一个和最后一个元素的差值，判断arr中最后一个元素的值距离00：00还需多少分钟，再加上arr中第一个元素的值，与当前最小的分钟数进行比较。


## 代码

```javascript
/**
 * @param {string[]} timePoints
 * @return {number}
 */
var findMinDifference = function(timePoints) {
	let arr = [];
	for(let i = 0;i<timePoints.length;i++){
		// 将时间拆开
		const temp = timePoints[i].split(':');
		arr.push(parseInt(temp[0]) * 60 + parseInt(temp[1]))
	}
	arr.sort((a,b)=>a-b);
	let min = 1440 ;
	for(let i = 1;i<arr.length;i++){
		if(min > arr[i] - arr[i-1]){
			min = arr[i] - arr[i-1];
		}
	}
	let maxNum = 24 * 60;
	if(maxNum - arr[arr.length - 1] + arr[0] < min){
		min = maxNum - arr[arr.length - 1] + arr[0]
	}
	console.log(arr)
	return min;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/10baaeb750b8414f8d2674bec97a584e.png)
