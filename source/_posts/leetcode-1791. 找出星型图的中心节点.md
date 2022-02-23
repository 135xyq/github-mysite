---
title: 1791. 找出星型图的中心节点
date: 2022-02-18 10:24:47
description: 1791. 找出星型图的中心节点 哈希&找规律
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---

# 1791. 找出星型图的中心节点 哈希&找规律

## [查看原题](https://leetcode-cn.com/problems/find-center-of-star-graph/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/fbfc1a5c51484bfdb4856717251a486a.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(哈希)

将二维数组转变为一维数组，求出每个数字出现的个数，出现个数为n-1的那个就是中心节点。


## 代码
```javascript
/**
 * @param {number[][]} edges
 * @return {number}
 */
var findCenter = function(edges) {
	const array = edges.toString().split(',');
	const n = edges.length;
	let map = new Map();
	for (const item of array) {
		if(map.has(item)) {
			if(map.get(item) === n - 1 && item !== ','){
				return item;
			}else{
				map.set(item,map.get(item) + 1);
			}
			
		}else {
			map.set(item,1);
		}
	}
};

```
![在这里插入图片描述](https://img-blog.csdnimg.cn/b72fe02b0b71420dbd6d06b3890bc715.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(找规律)

因为中心点有n-1条边与之相连，说明每一个点都要与中心点相连；因此只要判断前数组的两个数组中哪个数是重复出现的，那个数即为中心点。

## 代码

```javascript
/**
 * @param {number[][]} edges
 * @return {number}
 */
var findCenter = function(edges) {
	if(edges[0][0] === edges[1][0] || edges[0][0] === edges[1][1]) {
		return edges[0][0];
	}else {
		return edges[0][1]
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/04911f1daa7f4447bedd94d751350fed.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
