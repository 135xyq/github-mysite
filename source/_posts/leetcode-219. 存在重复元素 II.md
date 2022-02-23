---
title: 219. 存在重复元素 II
date: 2022-01-19 09:32:20
description: 219. 存在重复元素 II 双重循环 & 滑动窗口
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js

---


# 219. 存在重复元素 II 双重循环 & 滑动窗口

## [查看原题](https://leetcode-cn.com/problems/contains-duplicate-ii/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d32370c0981b440a8ab0119e9a21defb.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(双重循环)

外层数组遍历数组，内层循环判断从当前位置开始的后面k个元素是否有和当前元素相同的，如果有直接返回true，找不到则返回false。

## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
	for(let i = 0;i<nums.length;i++){
		for(let j = i+1;j<=i+k;j++){
			if(nums[i] === nums[j]){
				return true;
			}
		}
	}
	return false;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/cdbee3bf9dd94638aa8f77327e4ea876.png)


## 解题思路(滑动窗口)

新建一个set集合，不断向set集合中添加和删除数据，注意判断条件
1. 当i>k时，说明窗口长度到达了可以删除元素的长度，每次删除set集合中的第一个存进去元素(nums[i-k-1])
2. 如果集合set中有当前元素，直接返回true


## 代码

```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function(nums, k) {
	const set = new Set();
	const length = nums.length;
	for(let i = 0;i<length;i++){
		if(i > k){
			set.delete(nums[i-k-1])
		}
		if(set.has(nums[i])){
			return true;
		}
		set.add(nums[i])
	}
	return false;
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/2de8502431b143b198e592d56d54829e.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
