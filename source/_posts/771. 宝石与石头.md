---
title: 771. 宝石与石头
date: 2022-01-17 22:49:59
description: 771. 宝石与石头 遍历求解
toc: true
comments: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---



# 771. 宝石与石头 遍历一遍求解


## [查看原题](https://leetcode-cn.com/problems/jewels-and-stones/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/f0906751799f498dad87fac7c75dbc33.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路
遍历一遍stones，判断是否是宝石。

## 代码

```javascript
/**
 * @param {string} jewels
 * @param {string} stones
 * @return {number}
 */
var numJewelsInStones = function(jewels, stones) {
	let sum =0;
	for(let i =0 ;i<stones.length;i++){
		if(jewels.indexOf(stones[i]) != -1){
			sum++;
		}
	}
	return sum;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/74bfbe4173244470b151a8e069e4c930.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
