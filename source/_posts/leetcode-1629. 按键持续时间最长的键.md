---
title: 1629. 按键持续时间最长的键
date: 2022-01-10 20:07:20
description: 1629. 按键持续时间最长的键  遍历两个数组
toc: true
comments: true
categories: leetcode题解
tags:
	- 算法
	- leetcode
	- js
---

# 1629. 按键持续时间最长的键  遍历两个数组

## [查看原题](https://leetcode-cn.com/problems/slowest-key/)

## 题解

1. 在数组的最前面加上一个0，为了更好求出每个按键的时间```releaseTimes[i+1] - releaseTimes[i]```
2. 用一个变量记录当前的最大持续时间，一个变量记录对应的按键
3. 循环不断判断是否有比当前持续时间长的按键，如果有，则更新最长持续时间和对应的按键
4. 如果和最大持续时间相等，则继续比较按键的大小，如果最新的较大，则更新为对应的按键
5. 循环结束返回存储的按键

## 代码

```javascript
/**
 * @param {number[]} releaseTimes
 * @param {string} keysPressed
 * @return {character}
 */
var slowestKey = function(releaseTimes, keysPressed) {
	releaseTimes.unshift(0)
	maxNum = 0;
	maxKey = null;
	for(let i = 0;i<keysPressed.length;i++){
		if(releaseTimes[i+1] - releaseTimes[i] > maxNum){
			maxNum = releaseTimes[i+1] - releaseTimes[i];
			maxKey = keysPressed.charAt(i);
		}else if(releaseTimes[i+1] - releaseTimes[i] === maxNum){
			if(maxKey.charCodeAt() < keysPressed.charCodeAt(i)){
				maxKey = keysPressed.charAt(i)
			}
		}
	}
	return maxKey;
};
```