---
title: 48. 旋转图像
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 48. 旋转图像 另开空间和直接旋转
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 48. 旋转图像 另开空间和直接旋转
## [查看原题](https://leetcode-cn.com/problems/rotate-image/)

## 解题思路
1. 新开一个二维数组，存放交换后的数据
2. 遍历原数组，将交换后的值存放到相应位置 ```temp[j][length-i-1] = matrix[i][j];```
3. 将新数组的值再次赋给原数组
4. 这种思路，时间复杂度为 O(N^2),空间复杂度为 O(N^2)

## 代码
```javascript
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function(matrix) {
	// 矩阵的宽度
	const length =  matrix.length;
	const temp = (new Array(length).fill(0)).map(item=>new Array(length));
	for(let i = 0;i<length;i++){
		for(let j = 0;j<length;j++){
			temp[j][length-i-1] = matrix[i][j];
		}
	}
	for(let i = 0;i<length;i++){
		for(let j = 0;j<length;j++){
			matrix[i][j] = temp[i][j]
		}
	}
};

```

## 解题思路
1. 不开辟新数组，找出新矩阵的每一项的对应的原矩阵的位置为```matrix[j][length-i-1] = matrix[i][j];```
2. 但是这样会发现交换之后会把原有位置上的数据覆盖，所以应该先把原有位置上的数据移动到应该的位置。
```javascript
	let temp = matrix[i][j];
	matrix[i][j] = matrix[length-1-j][i];
	matrix[length-1-j][i] = matrix[length-1-i][length-1-j];
	matrix[length-1-i][length-1-j] = matrix[j][length-1-i];
	matrix[j][length-1-i] = temp;
```
3. 判断哪些应该交换，当数组的长度length为偶数时：需要交换n^2/4=(n/2)×(n/2) 个位置;当length 为奇数是：需要交换(n^2−1)/4=((n−1)/2)×((n+1)/2)

## 代码

```javascript
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function(matrix) {
	// 矩阵的宽度
	const length =  matrix.length;
	for(let i = 0;i<Math.floor(length/2);i++){
		for(let j = 0;j<Math.floor((length+1)/2);j++){
			let temp = matrix[i][j];
			matrix[i][j] = matrix[length-1-j][i];
			matrix[length-1-j][i] = matrix[length-1-i][length-1-j];
			matrix[length-1-i][length-1-j] = matrix[j][length-1-i];
			matrix[j][length-1-i] = temp;
		}
	}
};
```