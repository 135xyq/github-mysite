---
title: 717. 1比特与2比特字符
date: 2022-02-20 19:52:47
description: 717. 1比特与2比特字符 简单模拟
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 717. 1比特与2比特字符 简单模拟

## [查看原题](https://leetcode-cn.com/problems/1-bit-and-2-bit-characters/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/6c0819f5ae6b4798b646a2e35a3865cf.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

因为2比特的是10和11,则1和其后面的元素是一个整体;遍历数组，当当前元素为1时则循环递增2,如果为0则递增1,如果当前元素为数组的最后一项，说明最后一项一定是一个字符。

## 代码

```javascript
/**
 * @param {number[]} bits
 * @return {boolean}
 */
var isOneBitCharacter = function(bits) {
	const length = bits.length;
	for(let i = 0; i < length; ) {
		if(i === length -1) {
			return true;
		}
		if(bits[i] === 1) {
			i += 2;
		}else{
			i++;
		}
	}
	return false;
};
```
![在这里插入图片描述](https://img-blog.csdnimg.cn/e04a40d19ccb4de8ac0d4eeee819fee3.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
