---
title: 567. 字符串的排列
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 567. 字符串的排列
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 567. 字符串的排列

## [查看原题](https://leetcode-cn.com/problems/permutation-in-string/)

## 解题思路

1. 先求出s1里面各个字符的个数存储到数组arr1中
2. 再遍历数组s2注意结束条件是 ```let i = 0;i<=s2.length - s1.length;i++```,当个数少于```s2.length - s1.length```不会再有结果
3. 统计s2中每个s1.length长度区间的各个字符的个数，与s1中的比较，如果元素个数都一样则符合条件返回true
4. 直接返回false，说明前面没有符合条件的

## 代码

```javascript
/**
 * @param {string} s1
 * @param {string} s2
 * @return {boolean}
 */
var checkInclusion = function(s1, s2) {
	let arr1 = new Array(26).fill(0);

	for (const item of s1){
		arr1[item.charCodeAt() - 97]++;
	}
	
	for(let i = 0;i<=s2.length - s1.length;i++){
		let arr2 = new Array(26).fill(0);

		for(let j = 0;j<s1.length;j++){
			arr2[s2.charCodeAt(i+j) - 97]++;
		}

		let t = 0;
		for(t = 0;t<26;t++){
			if(arr2[t] !== arr1[t]){
				break;
			}
		}

		if(t===26){
			return true;
		}
	}
	return false;
};

```