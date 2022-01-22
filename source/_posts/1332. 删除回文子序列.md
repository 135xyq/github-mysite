---
title: 1332. 删除回文子序列
date: 2022-01-22 08:33:01
description: 1332. 删除回文子序列 判断原字符串是否是回文串
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 1332. 删除回文子序列 判断原字符串是否是回文串

## [查看原题](https://leetcode-cn.com/problems/remove-palindromic-subsequences/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/49440f208fed485b9de97693f95364f0.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)


## 解题思路

因为删除的是子回文串，所以最大删除次数为2。当字符串本身是一个回文串，则删除一次就行，如果不是则需要删除2次。

## 代码

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var removePalindromeSub = function(s) {
	const length = s.length;
	for(let i = 0 ;i<Math.floor(length /2);i++){
		if(s[i] !== s[length - i -1]){
			return 2;
		}
	}
	return 1
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/5236c8516ccd43d6999be986e952a7d1.png)
