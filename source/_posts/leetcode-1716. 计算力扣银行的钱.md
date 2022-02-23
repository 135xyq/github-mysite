---
title: 1716. 计算力扣银行的钱
date: 2022-01-16 14:49:50
description: 1716. 计算力扣银行的钱 分别求出整星期个不足星期的钱
comments: true
toc: true
categories: leetcode题解
tags: 
	- 算法
	- leetcode
	- js
---


# 1716. 计算力扣银行的钱 分别求出整星期个不足星期的钱

## [查看原题](https://leetcode-cn.com/problems/calculate-money-in-leetcode-bank/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/b07b9b31ab154b5b875684bd7e6e46bf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

先求出有多少个完整的星期和剩下的天数，分别求解。
每个星期不加钱的情况下存钱为28元，每个星期比上个星期多7元。
1. 求出星期数weeks和剩余天数days
2. 求出整的星期数包含的钱（基本的加上多存的）
3. 求出剩余天数存的钱(星期一的钱数为weeks)

## 代码

```javascript
/**
 * @param {number} n
 * @return {number}
 */
var totalMoney = function(n) {
	const weeks = Math.floor(n / 7);
	const days = n % 7;
	let result = 0;
	// 整数个星期的钱
	result += 28 * weeks;
	for(let i =1 ;i<weeks;i++){
		result += 7 * i;
	}
	// 不足一个星期的钱
	for(let i = 1 ;i<=days;i++){
		result += weeks + i;
	}
	return result
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/babecdc85099428da37a143892e591e3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
