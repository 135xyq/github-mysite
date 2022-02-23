---
title: 540. 有序数组中的单一元素
date: 2022-02-14 11:57:20
description: 540. 有序数组中的单一元素 二分查找&模拟
comments: true #是否可评论
toc: true #是否显示文章目录
categories: "leetcode题解" #分类
tags:   #标签
	- js
	- leetcode
	- 算法
---



# 540. 有序数组中的单一元素 二分查找&模拟

## [查看原题](https://leetcode-cn.com/problems/single-element-in-a-sorted-array/)
![在这里插入图片描述](https://img-blog.csdnimg.cn/d76905ac16ab41a79c582ad6e5e92a1b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)

## 解题思路(二分)

假设只出现一次的元素位于下标 x，由于其余每个元素都出现两次，因此下标 xx 的左边和右边都有偶数个元素，数组的长度是奇数。

由于数组是有序的，因此数组中相同的元素一定相邻。对于下标 x左边的下标 y，如果 nums[y] = nums[y + 1]nums[y]=nums[y+1]，则 y一定是偶数；对于下标 x 右边的下标 z，如果 nums[z] = nums[z + 1]nums[z]=nums[z+1]，则 zz 一定是奇数。由于下标 xx 是相同元素的开始下标的奇偶性的分界，因此可以使用二分查找的方法寻找下标 x。

初始时，二分查找的左边界是 0，右边界是数组的最大下标。每次取左右边界的平均值mid 作为待判断的下标，根据 mid 的奇偶性决定和左边或右边的相邻元素比较：

如果 mid 是偶数，则比较 nums[mid] 和 nums[mid + 1]是否相等；

如果 mid 是奇数，则比较 nums[mid- 1] 和 nums[mid]是否相等。

如果上述比较相邻元素的结果是相等，则 mid < x，调整左边界，否则 mid ≥x，调整右边界。调整边界之后继续二分查找，直到确定下标 x 的值。

得到下标 xx 的值之后，nums[x] 即为只出现一次的元素。

细节

利用按位异或的性质，可以得到 mid 和相邻的数之间的如下关系，其中 ⊕ 是按位异或运算符：

当 mid 是偶数时，mid + 1 = mid⊕1；

当 mid 是奇数时，mid−1=mid⊕1。

因此在二分查找的过程中，不需要判断 mid 的奇偶性，mid 和 mid⊕1 即为每次需要比较元素的两个下标。


```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNonDuplicate = function(nums) {
	let left = 0;
	let right = nums.length - 1;
	let mid;
	while(left < right){
		mid = Math.floor((right - left) / 2) + left;
		if(nums[mid] === nums[mid^1]) {
			left = mid +1;
		}else{
			right = mid;
		}
	}
	return nums[left]
};

```

![在这里插入图片描述](https://img-blog.csdnimg.cn/ff2893876acc4587ae84997f71dc3c49.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)


## 解题思路(模拟)

因为数组是有序的，只要判断相邻两个元素是否相等，如果不相等，则说明这个元素是单一的。

## 代码

```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNonDuplicate = function(nums) {
	const length = nums.length;
	for(let i =0;i<length;i+=2){
		if(nums[i] !== nums[i+1]){
			return nums[i]
		}
	}
};
```

![在这里插入图片描述](https://img-blog.csdnimg.cn/05fe5da61c63420584e3d254548a012b.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBA562xLi4=,size_20,color_FFFFFF,t_70,g_se,x_16)
