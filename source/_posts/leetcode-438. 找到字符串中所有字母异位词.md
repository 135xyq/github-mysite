---
title: 438. 找到字符串中所有字母异位词
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 438. 找到字符串中所有字母异位词 滑动窗口
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 438. 找到字符串中所有字母异位词 滑动窗口

## [查看原题](https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/)

## 解题思路
这是最容易想到的，循环，无用功太多，结果自然是g了
**超出时间限制**
1. 先将p转为数组排序后再转为字符串
2. 循环s利用字符串方法slice截取和p等长的字符串，再进行排序最后比较是否相等
3. 如果相等就push到结果数组中

## 代码
```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
	let result = [];//结果
	const slength = s.length;
	const plength = p.length;
	const arr = s.split('');
	const p1 = p.split('').sort().join('');//将p转为数组排序后再转为字符串
	for(let i = 0;i<=slength - plength;i++){
		let temp = arr.slice(i,plength+i)
		if(temp.sort().join('') === p1)
		result.push(i)
	}

	return result;
};
```

## 解题思路
这种思路使用了滑动窗口，虽然能解决问题，能通过测试，但效率还是有点低。
1. 将字符串p中的字母和字母的个数映射到map集合中
2. 循环字符串s取出和p等长的一段，判断map集合中是否右当前元素，且元素的数量不是0
3. 每次符合条件都要更新temp里面的数据，注意这个temp每次都要新建,通过p映射的那个map集合创建
4. ```!temp.has(s.charAt(j))||temp.get(s.charAt(j))===0```这是判断条件，为true则直接break，为false则更新temp集合```temp.set(s.charAt(j),temp.get(s.charAt(j))-1)```
5. 判断```j===i+plength```，来说明循环是否正常走完，为false则不是正常走完，说明不符合条件；为true说明正常走完了循环，则将 i push到结果数组中。

## 代码

```javascript


/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
	let result = [];//结果
	const slength = s.length;
	const plength = p.length;
	const pmap = new Map();
	// 将字符串p的单词和个数映射到map对象中
	for(let i = 0;i<plength;i++){
		if(pmap.has(p.charAt(i))){
			pmap.set(p.charAt(i),pmap.get(p.charAt(i))+1)
		}else{
			pmap.set(p.charAt(i),1);
		}
	}
	for(let i = 0;i<=slength-plength;i++){
		const temp = new Map(pmap);
		let j;
		for( j = i;j<i+plength;j++){
		
			if(!temp.has(s.charAt(j))||temp.get(s.charAt(j))===0){
				break;
			}else{
				temp.set(s.charAt(j),temp.get(s.charAt(j))-1);
			}
		}
		if(j===i+plength){
			result.push(i)
		}
	}
	return result;
};
```

## 解题思路
这种思路效率就比较高了，当然是参考别人的了

## 代码

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
    if (!s || !p) return [];
    let need = {}, window = {}, ans = [];
    [...p].forEach(c => need[c] ? need[c]++ : need[c] = 1);
    let l = 0, r = 0, cnt = 0, nkLen = Object.keys(need).length;
    while (r < s.length) {
        let c1 = s[r];
        if (need[c1]) {
            window[c1] ? window[c1]++ : window[c1] = 1;
            if (window[c1] === need[c1]) cnt++;
        }
        r++;
        while (cnt === nkLen) {
            let c2 = s[l];
            if ((r - l) == p.length) ans.push(l);
            if (need[c2]) {
                window[c2]--;
                if (window[c2] < need[c2]) cnt--;
            }
            l++;
        }
    }
    return ans;
};
```