---
title: 748. 最短补全词 
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 748. 最短补全词 循环遍历每一个单词，比较是否符合
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 748. 最短补全词 循环遍历每一个单词，比较是否符合

## [查看原题](https://leetcode-cn.com/problems/shortest-completing-word/)

## 解题思路

使用了map集合来判断

1. 先将licensePlate的大写字母转为小写字母，再统计里面每一个小写单词的个数
2. 遍历words分别对每一个元素做出判断，该元素是否是补全词，该元素是补全词的话是否比前面的补全词更短

## 代码

```javascript
/**
 * @param {string} licensePlate
 * @param {string[]} words
 * @return {string}
 */
var shortestCompletingWord = function(licensePlate, words) {
	// 将字符串全转为小写字母
	const temp = licensePlate.toLowerCase();
	let map = new Map();//统计各个单词的个数
	for (const item of temp){
		// 将小写字母过滤
		if(item>='a' && item<='z'){
			if(map.has(item)){
				map.set(item,map.get(item) + 1)
			}else{
				map.set(item,1);
			}
		}
	}

	let index = null;//最短词的下标
	for(let i =0 ;i<words.length;i++){
		const temp = new Map(map);
		for(const word of words[i]){
			if(temp.has(word)){
				temp.set(word,temp.get(word) - 1 );
			}
		}
		let flag = true;//为true说明该单词是补全词
		for (const [key,value] of temp){
			if(value > 0){
				flag = false;
			}
		}

		// 进入此if说明是补全词，接下来判断是否要更新最短的补全词
		if(flag){
			if(index===null || words[i].length < words[index].length){
				index = i;
			}
		}
	}
	return words[index];
};

```



