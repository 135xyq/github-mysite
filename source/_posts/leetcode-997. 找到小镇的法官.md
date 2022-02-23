---
title: 997. 找到小镇的法官
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 997. 找到小镇的法官 图的入度出度和普通方法运算
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 997. 找到小镇的法官 图的入度出度和普通方法运算

## [查看原题](https://leetcode-cn.com/problems/find-the-town-judge/)

## 解题思路

这种方法是先判断哪些可能是法官（不相信任何人），再判断这些可能法官中是否存在除自己外所有人都相信的真正法官。
1. 利用map集合筛选出可能是法官的那些人
2. 遍历这些可能是法官的的那批人，在判断他们是否有n-1个人相信，如果有说明他是真正的法官
3. 循环完毕返回-1，说明此时没有真正的法官

## 代码

```javascript
/**
 * @param {number} n
 * @param {number[][]} trust
 * @return {number}
 */
var findJudge = function(n, trust) {
	let map = new Map();
	for(let i = 1;i<=n;i++){
		map.set(i,0);
	}
	for(let i =0;i<trust.length;i++){
		if(map.has(trust[i][0])){
			map.delete(trust[i][0])
		}
	}
	if(map.size === 0){
		return -1;
	}else{
		for (const key of map.keys()){
			let count=0;
			trust.forEach(item=>{
				if(item[1] === key){
					count++;
				}
			})
			console.log(count)
			if(count === n-1){
				return key;
			}
		}
		return -1;
	}
};

```

## 解题思路

利用图论里面的出度和入度

1. 循环trust 将每个人相信的个人的入度加一，自己的出度加一
2. 循环判断一个人的出度=0，且入度=n-1，则这个人就是法官
3. 返回-1，说明没有法官


## 代码

```js
/**
 * @param {number} n
 * @param {number[][]} trust
 * @return {number}
 */
var findJudge = function(n, trust) {
	let input = new Array(n+1).fill(0);
	let output= new Array(n+1).fill(0);

	for(let i=0;i<trust.length;i++){
		input[trust[i][1]]++;
		output[trust[i][0]]++;
	}
	for(let i =1;i<=n;i++){
		if(input[i] === n-1 && output[i] === 0){
			return i;
		}
	}
	return -1;
};
```