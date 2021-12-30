---
title: 1154. 一年中的第几天 打表求解
date: 2021-12-30 18:24:47
description: 1154. 一年中的第几天 打表求解
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 1154. 一年中的第几天 打表求解

## [查看原题](https://leetcode-cn.com/problems/day-of-the-year/)

## 解题思路

先将每个月份的天数存到数组中，再判断该年是不是闰年，闰年的2月份是29天。

## 代码

```javascript

/**
 * @param {string} date
 * @return {number}
 */
var dayOfYear = function(date) {
	let count = 0;
	let months = [31,28,31,30,31,30,31,31,30,31,30,31];
	// 年月日拆开
	const nums = date.split('-');

	const year = parseInt(nums[0]);
	const month = parseInt(nums[1]);
	const day = parseInt(nums[2])
	// 判断是不是闰年
	if((year % 4 === 0 && year % 100 !== 0)||year % 400 === 0){
		if(month > 2){
			count++;
		}
	}
	for(let i = 1;i<month;i++){
		count += months[i-1];
	}
	count += day;
	return count;
```