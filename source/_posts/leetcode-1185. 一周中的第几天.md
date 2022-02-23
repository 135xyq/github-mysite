---
title: 1185. 一周中的第几天 
date: 2022-01-03 14:15:00
description: 1185. 一周中的第几天 Date函数和模拟天数求解
toc: true
comments: true
categories: leetcode题解
tags:
	- js 
	- leetcode
	- 算法
---

# 1185. 一周中的第几天 Date函数和模拟天数求解

## [查看原题](https://leetcode-cn.com/problems/day-of-the-week/)

## 解题思路(使用js日期函数Date)

1. 通过传入的年月日来创建一个日期对象，注意：month要减一
2. 再用getDay()方法获取一个星期的第几天（0-6）


## 代码

```javascript
/**
 * @param {number} day
 * @param {number} month
 * @param {number} year
 * @return {string}
 */
var dayOfTheWeek = function(day, month, year) {
	const week = ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
	return week[new Date(year,month-1,day).getDay()]
};
```


## 解题思路（模拟天数求解）

1. 找出第一天的星期数，即1971.01.01是星期五，这是最重要的
2. 找出当前的日期距离1971.01.01的天数
	- 整年的天数 (year - 1971)* 365 注意加上其中闰年的个数（闰年366天）
	- 整月的天数 (month  - 1) * 每个月的天数
	- 剩下的天数 day
3. 求出总天数加上3再模上7得出星期的下标，加4是因为第一天在星期数组的下标为3
4. 星期数组为：[ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday","Sunday"];

## 代码

```javascript
/**
 * @param {number} day
 * @param {number} month
 * @param {number} year
 * @return {string}
 */
var dayOfTheWeek = function(day, month, year) {
	// 1970 年 12 月 31 日是星期四，
	const monthDays = [31,28,31,30,31,30,31,31,30,31,30,31];
	const week = [ "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday","Sunday"];
	const yearNum = year - 1971;
	const monthNum = month  - 1;
	const dayNum = day;
	let daySum = yearNum * 365;
	for(let i = 1971;i<=year;i++){
		if((i % 4 === 0 && i % 100 !== 0)||(i % 400 ===0) ){
			if(i === year && month < 3){
				continue;
			}else{
				daySum++;
			}
		}
	}
	for(let i =0 ;i<monthNum;i++){
		daySum+= monthDays[i]
	}
	daySum += dayNum;
	console.log((daySum+3)%7)
	return week[(daySum+3)%7]
};
```
