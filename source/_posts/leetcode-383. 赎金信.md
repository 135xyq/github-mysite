---
title: 383. 赎金信
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 383. 赎金信 哈希表
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 383. 赎金信 哈希表

## [查看原题](https://leetcode-cn.com/problems/ransom-note/)

## 解题思路

1. 将 magazine字符串映射到map集合中，键为字符的种类，值为字符的个数；
2. 将 ransomNote字符串映射到map1集合中，键为字符的种类，值为字符的个数；
3. 遍历map1，查找map中是否存在对应的键，且值大于等于map1中对应的值。

## 代码

```javascript
/**
 * @param {string} ransomNote
 * @param {string} magazine
 * @return {boolean}
 */
var canConstruct = function(ransomNote, magazine) {
	// 将杂志字符串映射到map集合
	const map = new Map();
	for(let i = 0;i<magazine.length;i++){
		if(map.has(magazine.charAt(i))){
			map.set(magazine.charAt(i),map.get(magazine[i])+1);
		}else{
			map.set(magazine[i],1);
		}
	}
	// 将赎金信映射到map1中
	const map1 = new Map();
	for(let i = 0;i<ransomNote.length;i++){
		if(map1.has(ransomNote.charAt(i))){
			map1.set(ransomNote.charAt(i),map1.get(ransomNote[i])+1);
		}else{
			map1.set(ransomNote[i],1);
		}
	}
	for (const [key,value] of map1){
		if(map.has(key) && map.get(key)>=value){
			continue;
		}else{
			return false;
		}
	}
	return true;
	
};

```