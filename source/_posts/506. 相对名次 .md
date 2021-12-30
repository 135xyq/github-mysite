---
title: 506. 相对名次
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description:  506. 相对名次 排序后switch
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 506. 相对名次 排序后switch

## [查看原题](https://leetcode-cn.com/problems/relative-ranks/)

## 解题思路

1. 深克隆一个数组temp，将temp降序排序；
2. 遍历原数组，判断每一项，前三名特殊处理；

## 代码

```javascript
/**
 * @param {number[]} score
 * @return {string[]}
 */
var findRelativeRanks = function(score) {
	const temp = [...score];//得到一个为新数组
	temp.sort((a,b)=>b-a);//将数组降序排列，得到正确的名次
	let result = [];
	score.forEach(item=>{
		const index = temp.indexOf(item);//得到当前元素的排名
		switch (index){
			case 0:
				result.push('Gold Medal');
				break;
			case 1:
				result.push('Silver Medal');
				break;
			case 2:
				result.push('Bronze Medal');
				break;
			default:
				result.push(`${index+1}`)
		}
		
	})
	return result;
	
};

console.log(findRelativeRanks(score = [5,4,3,2,1]));
```
