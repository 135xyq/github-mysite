---
title: 1748. 唯一元素的和
date: 2022-02-07 14:22:12
description: 1748. 唯一元素的和 排序 & 哈希表
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 1748. 唯一元素的和 排序 & 哈希表

## [查看原题](https://leetcode-cn.com/problems/sum-of-unique-elements/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/8804e6db1d3c40fb9578ce4a4ac974a3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(排序)

将数组排序，将数组不和前一项和后一项相等的元素就是唯一元素。

## 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var sumOfUnique = function(nums) {
	nums.sort((a,b)=>a-b);
	let sum = 0;
	let i = 0;
	const length = nums.length;

	for(i = 0; i < length; i++) {
		if(nums[i] !== nums[i+1] && nums[i] !== nums[i-1]){
			sum += nums[i];
		}
	}

	return sum;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/d9c6aff34e764334ad94c530ee1152a7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(哈希表)

统计每一个数字出现的次数，找出出现次数为一的元素求和。


## 代码

```javascript

/**
 * @param {number[]} nums
 * @return {number}
 */
var sumOfUnique = function(nums) {
	const map = new Map();
	let sum = 0;
	nums.forEach(num=>{
		if(map.has(num)) {
			map.set(num, map.get(num) + 1)
		}
		else {
			map.set(num,1);
		}
	})

	for (const [key,value] of map) {
		if(value == 1) {
			sum += Number(key);
		}
	}

	return sum;
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/b55b0a3d73154910b60c75f3fd9bc186.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
