---
title: 1078. Bigram 分词
date: 2021-12-30 18:24:47
description: 1078. Bigram 分词
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 1078. Bigram 分词

## [查看原题](https://leetcode-cn.com/problems/occurrences-after-bigram/)

## 解题思路

1. 将句子按空格分隔开
2. 遍历寻找符合条件的就行

## 代码

```javascript
/**
 * @param {string} text
 * @param {string} first
 * @param {string} second
 * @return {string[]}
 */
var findOcurrences = function(text, first, second) {
	let thirdWord = [];//结果
	// 将字符串转为数组
	const textArr = text.split(' ');
	for(let i = 0 ;i<textArr.length-2;i++){
		if(textArr[i]===first &&textArr[i+1] === second){
			thirdWord.push(textArr[i+2])
		}
	}
	return thirdWord;
};
```