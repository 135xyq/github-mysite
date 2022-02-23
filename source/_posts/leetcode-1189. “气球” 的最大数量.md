---
title: 1189. “气球” 的最大数量
date: 2022-02-13 11:07:20
description: 1189. “气球” 的最大数量 简单模拟求出各个字母的个数
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 1189. “气球” 的最大数量 简单模拟求出各个字母的个数

## [查看原题]()
![在这里插入图片描述](https://img-blog.csdnimg.cn/bbe8e460ccf448a3adce73e00f5717d9.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路

遍历字符串求出'balloon'单词所有需要的字母的个数，其中'l'和'o'要除以二并向下取整；再求出他们的最小值即可。

## 代码

```javascript

/**
 * @param {string} text
 * @return {number}
 */
var maxNumberOfBalloons = function(text) {
	// 字符串中各个单词的数量
	let count_a = 0;
	let count_b = 0;
	let count_o = 0;
	let count_n = 0;
	let count_l = 0;
	let length = text.length;
	for(let i = 0; i <length; i++){
		switch (text[i]) {
			case 'a':
				count_a++;
				break;
			case 'b':
				count_b++;
				break;			
			case 'o':
				count_o++;
				break;			
			case 'n':
				count_n++;
				break;			
			case 'l':
				count_l++;
				break;
		}
	}
	const maxCount = Math.min(count_a,count_b,Math.floor(count_o / 2),Math.floor(count_l / 2),count_n);
	return maxCount;
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/55cf8360e5884efdb52e99d7eeac1984.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
