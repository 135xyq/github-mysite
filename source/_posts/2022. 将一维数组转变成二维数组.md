---
title: 2022. 将一维数组转变成二维数组
date: 2022-01-01 13:59:47
description: 先判断能否转变，再循环一维数组数组转变成二维数组数组。
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 2022. 将一维数组转变成二维数组

## [查看原题](https://leetcode-cn.com/problems/convert-1d-array-into-2d-array/)

## 解题思路

先判断能否转变，再循环一维数组数组转变成二维数组数组。

1. 若 original.length !== m * n 说明一位数组的长度过长或过短，直接返回 空数组[] ；
2. 截取数组的n个长度添加到二维数组中。

## 代码

```javascript

/**
 * @param {number[]} original
 * @param {number} m
 * @param {number} n
 * @return {number[][]}
 */
var construct2DArray = function(original, m, n) {
	// 元素个数不够或多余不能转为
	if(original.length !== m * n){
		return [];
	}


	let result= [];
	for(let i =0 ;i < m ;i++){
		result.push(original.splice(0,n))
	}

	return result;
};

```