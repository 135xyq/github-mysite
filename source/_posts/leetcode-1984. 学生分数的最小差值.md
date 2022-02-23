---
title: 1984. 学生分数的最小差值
date: 2022-02-11 11:10:12
description: 1984. 学生分数的最小差值 排序加滑动窗口
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法 
	- leetcode
	- js
---

# 1984. 学生分数的最小差值 排序加滑动窗口

## [查看原题](https://leetcode-cn.com/problems/minimum-difference-between-highest-and-lowest-of-k-scores/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/35dcd97d2b054162a22b9f9779af6efc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

求出一段区间中最大值和最小值的最小差值，答案就在选择顺序排列的区间内。

## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var minimumDifference = function(nums, k) {
	let length = nums.length;
	if(k === 1){
		return 0;
	}else{
		let min = 100000;
		nums.sort((a,b)=>a-b);
		for(let i = 0; i < length-k+1; i++){
			if(nums[i+k-1] - nums[i] < min){
				min = nums[i+k-1] - nums[i];
			}
		}
		return min;
	}
};

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/16ec10bc4d9846fe9f135ff90896e81a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

