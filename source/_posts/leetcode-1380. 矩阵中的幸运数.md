---
title: 1380. 矩阵中的幸运数
date: 2022-02-15 10:28:47
description: 1380. 矩阵中的幸运数 模拟
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---


# 1380. 矩阵中的幸运数 模拟

## [查看原题](https://leetcode-cn.com/problems/lucky-numbers-in-a-matrix/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/19daf0e7d41949d0837321b86828bfa7.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

- 先求出每一行的最小值存到数组min，再求出每一列的最大值存到数组max;
- 双重循环遍历每一个元素，判断是否同时在min和max中，如果同时在则是幸运数

## 代码

```javascript
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var luckyNumbers  = function(matrix) {
	const m = matrix.length;
	const n = matrix[0].length;
	let result = [];
	let min = [];
	let max = [];
	for(let i = 0; i < m;i++) {
		min.push(Math.min(...matrix[i])); //一行的最小值	
	}
	
	for(let j = 0; j < n; j++) {
		let temp  = 0;
		for(let i = 0; i < m; i++) {
			if(matrix[i][j] > temp){
				temp = matrix[i][j];
			}
		}
		max.push(temp);
	}
	for(let i = 0; i < m; i++) {
		for(let j =0; j < n; j++){
			if(min.indexOf(matrix[i][j]) !== -1 && max.indexOf(matrix[i][j]) !==-1) {
				result.push(matrix[i][j]);
			}
		}
	}
	return result;
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/116366291d494d0f8951e4eb07bbd382.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
