---
title: 507. 完美数
date: 2021-12-31 16:21:22
description: 507. 完美数 直接求解&数学理论
categories: "leetcode题解"
tags: 
	- js
	- leetcode
	- 算法
---

# 507. 完美数 直接求解&数学理论

## [查看原题](https://leetcode-cn.com/problems/perfect-number/)

## 解题思路（直接求因子）

直接循环找出每一个正因子相加判断

## 代码

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var checkPerfectNumber = function(num) {
	if(num ===1 ){
		return false;
	}
	let sum  = 1;
	for(let i = 2;i <= Math.floor(Math.sqrt(num));i++){
		if(num % i === 0){
			sum += num/i + i;
		}
	}
	if(sum === num){
		return true;
	}else{
		return false;
	}
};

```

## 解题思路（数学理论）

根据欧几里得-欧拉定理，每个偶完全数都可以写成

$$2^p-1(2^p -1)$$

的形式，其中 $p$ 为素数且 $2^p-1$也是素数

由于目前奇完全数还未被发现，因此题目范围 [1,10^8][1,10^8] 内的完全数都可以写成上述形式。
这一共有如下 5 个：
6, 28, 496, 8128, 33550336

## 代码

```javascript
var checkPerfectNumber = function(num) {
    return num === 6 || num === 28 || num === 496 || num === 8128 || num === 33550336;
};

```