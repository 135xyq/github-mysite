---
title: 1518. 换酒问题
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 1518. 换酒问题 不断更新当前瓶子的个数
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---
# 1518. 换酒问题 不断更新当前瓶子的个数

## [查看原题](https://leetcode-cn.com/problems/water-bottles/)

## 解题思路
1. 定义变量count表示可以喝的总瓶数，bottles表示当前有多少空瓶子
2. 循环，不断将瓶子换酒在换酒，结束条件为当前的瓶子数小于能兑换一瓶酒的最小瓶子数
3. 更新当前的瓶子数为换到的酒的数量加上不够一瓶酒的瓶子数
4. 更新count的值

## 代码

```javascript
/**
 * @param {number} numBottles
 * @param {number} numExchange
 * @return {number}
 */
var numWaterBottles = function(numBottles, numExchange) {
	let count = numBottles;//可以喝多少瓶酒
	let bottles = numBottles;//有多少瓶子
	while (bottles >= numExchange){
		let temp = Math.floor(bottles / numExchange);//当前的瓶子可以换多少瓶酒
		bottles = temp + (bottles - temp * numExchange);
		count += temp;
	}
	return count;
};
```