---
title: 747. 至少是其他数字两倍的最大数
date: 2022-01-13 09:50:12
toc: true
comments: true
description: 747. 至少是其他数字两倍的最大数 遍历求最大值和次大值
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 747. 至少是其他数字两倍的最大数 遍历求最大值和次大值

## [查看原题](https://leetcode-cn.com/problems/largest-number-at-least-twice-of-others/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/e3aa50f29f5a42f69b2657111f38612e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

先求出最大值，在求出次大值两者进行比较看是否满足大于等于2倍的关系。
1. 先使用Math.max方法求出最大值，用indexOf()求出下标
2. 将数组中的最大值删除
3. 再次使用Math.max()求出最大值，此时是原数组的次大值
4. 再比较两次求出的最大值，判断返回内容

## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var dominantIndex = function(nums) {
	const max = Math.max(...nums);
	const index = nums.indexOf(max);
	nums.splice(index,1);
	const secondMax = Math.max(...nums);
	if(max >= 2 * secondMax){
		return index;
	}
	return -1;
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/f3ac8efa77ec4077962c20bdb4e0d8e2.png)
