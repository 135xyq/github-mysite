---
title: 884. 两句话中的不常见单词
date: 2022-01-30 10:01:20
description: 884. 两句话中的不常见单词 Map统计]
toc: true
comments: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---



# 884. 两句话中的不常见单词


## [查看原题](https://leetcode-cn.com/problems/uncommon-words-from-two-sentences/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/67c6c30dbdcd4913a4be52d15e2590af.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

1. 先将两个字符串的单词分割到数组中
2. 使用Map集合统计两个字符串中每个单词的数量
3. 遍历两个map集合，判断是否另个map集合没有这个单词，且当前字符串该单词出现的频率为1

## 代码

```javascript
/**
 * @param {string} s1
 * @param {string} s2
 * @return {string[]}
 */
var uncommonFromSentences = function(s1, s2) {
	const arr1 = s1.split(" ");
	const arr2 = s2.split(" ");
	const map1 = new Map();
	const map2 = new Map();
	const arr = [];
	arr1.forEach(item=>{
		if(map1.has(item)){
			map1.set(item,map1.get(item)+1)
		}else{
			map1.set(item,1);
		}
	})
	arr2.forEach(item=>{
		if(map2.has(item)){
			map2.set(item,map2.get(item)+1)
		}else{
			map2.set(item,1);
		}
	})
	for (const [key,value] of map1){
		if(!map2.has(key)&&value==1){
			arr.push(key);
		}
	}
	for (const [key,value] of map2){
		if(!map1.has(key)&&value==1){
			arr.push(key);
		}
	}
	return arr;
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/3b72cbb2c66547a0b7bd7f70e6984017.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
