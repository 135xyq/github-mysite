---
title: 1122. 数组的相对排序 利用Map集合和数组排序
date: 2021-12-30 18:24:47
description: 1122. 数组的相对排序 利用Map集合和数组排序
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 1122. 数组的相对排序 利用Map集合和数组排序

## [查看原题](https://leetcode-cn.com/problems/relative-sort-array/)

## 解题思路
1. 先将数组arr1映射到map对象中，用数组的值为键，数组每个值得个数为值
2. 遍历arr2将map中的元素全部取出，顺序排列，注意要
```	js
	for(let i = 0;i<map.get(item);i++){
			result.push(item);
	}
```
将每一项都取出，防止遗漏重复项，取出一项后记得删除
3. 再次遍历map取出arr1特有的元素，进行排序再push到大数组中返回

## 代码

```javascript
/**
 * @param {number[]} arr1
 * @param {number[]} arr2
 * @return {number[]}
 */
var relativeSortArray = function(arr1, arr2) {
	// 将arr1映射到Map集合中值为元素的个数
	const map = new Map();
	arr1.forEach(item=>{
		if(map.has(item)){
			map.set(item,map.get(item)+1);
		}else{
			map.set(item,1);
		}
	});
	let result  =[];
	//遍历数组arr2按顺序将map中的值push到result中
	arr2.forEach(item=>{
		for(let i = 0;i<map.get(item);i++){
			result.push(item);
		}
		map.delete(item);
	});
	let other = [];
	for (const [key,value] of map){
		for(let i = 0;i<value;i++){
			other.push(key);
		}
	}
	result.push(...other.sort((a,b)=>a-b)) ;
	return result;
};

```