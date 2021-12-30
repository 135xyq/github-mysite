---
title: 1995. 统计特殊四元组
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 1995. 统计特殊四元组
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 1995. 统计特殊四元组

## [查看原题](https://leetcode-cn.com/problems/count-special-quadruplets/)

## 解题思路

四层循环直接判断

## 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var countQuadruplets = function(nums) {
	let count = 0;

	for(let i = 0;i<nums.length-3;i++){
		for(let j = i+1;j<nums.length-2;j++){
			for(let t = j+1;t<nums.length-1;t++){
				for(let l = t+1;l<nums.length;l++){
					if(nums[i] + nums[j] + nums[t] === nums[l]){
						count++;
					}
				}
			}
		}
	}
	return count;
};

```