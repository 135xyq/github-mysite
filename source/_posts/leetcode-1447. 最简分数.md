---
title: 1447. 最简分数
date: 2022-02-10 09:47:12
description: 1447. 最简分数 暴力枚举
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法 
	- leetcode
	- js
---

# 1447. 最简分数 暴力枚举

## [查看原题](https://leetcode-cn.com/problems/simplified-fractions/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/757bf27f581945eeb0663b661ae92401.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

双重遍历分子分母，求出他们的最大公约数，如果公约数不为一，则说明不是最简分数，直接跳过(因为前面已经计入)。

## 代码

```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var simplifiedFractions = function(n) {
	let arr = [];

	for(let i = 1; i <= n; i++) {
		for(let j = 1; j < i; j++) {
			let temp = null; 
			let m = i;
			let n = j;
			while(temp = m % n){
				m = n;
				n = temp;
			}
			if(n === 1){
				arr.push(`${j}/${i}`)
			}
		}
	}
	return arr;
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/c58ce540c9ec438e9fc872480f2c9c6c.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
