---
title: 2006. 差的绝对值为 K 的数对数目
date: 2022-02-09 13:40:50
description: 2006. 差的绝对值为 K 的数对数目 简单模拟
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 2006. 差的绝对值为 K 的数对数目 简单模拟

## [查看原题](https://leetcode-cn.com/problems/count-number-of-pairs-with-absolute-difference-k/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/3a762b63923d46da812e8e00fbbc18e8.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

双重循环遍历，模拟所有的可能结果。

## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var countKDifference = function(nums, k) {
	let count = 0;
	const length = nums.length;
	for(let i = 0; i < length; i++) {
		for(let j = i+1; j < length; j++){
			if(Math.abs(nums[i] - nums[j]) === k){
				count++;
			}
		}
	}
	return count;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/a2343cc7ebbe4fc2812e092bedb0134c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
