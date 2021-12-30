---
title: 1446. 连续字符
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 1446. 连续字符 滑动窗口
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---

# 1446. 连续字符 滑动窗口

## [查看原题](https://leetcode-cn.com/problems/consecutive-characters/)

## 解题思路
1. 定义一个总的最大值max = 1，一个局部最大值temp = 1；
2. 循环字符串的每一项，判断当前项与前一项是否相等
	- 相等，则局部最大值temp++
	- 不相等，则说明要重新开始寻找相同的字符串了，将temp=1;
3. 注意循环要从 1 开始
4. 要不断判断temp 与max的大小，更新max

## 代码

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var maxPower = function(s) {
	let max = 1;
	let temp = 1;
	let i ;
	// 遍历字符串，遇到不是一样的字符据重新计算
	for(i= 1;i<s.length;i++){
		if(s.charAt(i)===s.charAt(i-1)){
			temp++;
		}else{
			temp = 1;
		}
		if(temp > max){
			max =  temp;
		}

	}
	return max;
};
```