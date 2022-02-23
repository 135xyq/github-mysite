---
title: 1996. 游戏中弱角色的数量
date: 2022-01-28 10:58:10
description: 1996. 游戏中弱角色的数量 递增栈
comments: true
toc: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 1996. 游戏中弱角色的数量 递增栈

## [查看原题](https://leetcode-cn.com/problems/the-number-of-weak-characters-in-the-game/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/feb04e0219cf475897d26c86f15cb9ed.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

1. 将数组按照攻击力从低到高进行排序，其中攻击力相同的按照防御力从高到低排序；
2. 创建一个栈，遍历排序后的数组，将每一项与栈顶的元素进行比较，如果比栈顶的防御力大，则说明栈顶的元素是弱者，count++,并将其弹出栈，继续与下一项比较
3. 如果防御力小于栈顶元素，则将新的元素加入栈中

## 代码

```javascript
/**
 * @param {number[][]} properties
 * @return {number}
 */
var numberOfWeakCharacters = function(properties) {
	// 按照攻击力高低排序
	properties.sort((a,b)=>a[0]===b[0]?b[1] - a[1] : a[0] - b[0]);
	let count = 0;
	let arr = [];
	for (const propertie of properties){
		while (arr.length && arr[arr.length - 1] < propertie[1]){
			arr.pop();
			count++;
		}
		arr.push(propertie[1])
	}
	return count;
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/44922d09f1a540de90334104b5740280.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
