---
title: 794. 有效的井字游戏
date: 2021-12-30 18:24:47
comments: true #是否可评论
toc: true #是否显示文章目录
description: 794. 有效的井字游戏  找出判断条件
categories: "leetcode题解" #分类
tags:   #标签
    - js
    - leetcode
    - 算法
---


# 794. 有效的井字游戏  找出判断条件

## [查看原题](https://leetcode-cn.com/problems/valid-tic-tac-toe-state/)

## 解题思路

### 棋盘可能达到的状态是：
1. 玩家一下的 'X'个数 等于玩家二下的 ''O' 的个数或 'O'的个数加一
2. 只能有一个玩家赢
3. 当玩家一赢的时候，棋局上 'X'的个数等于'O'的个数加一
4. 当玩家二赢的时候，棋局上'O'的个数等于'X'的个数

### 关键步骤：
1. 求出棋盘上'X'和'O'的个数
2. 判断是否符合条件一
3. 若符合条件一继续执行，不符合则直接```return false```
4. 接下来判断是否有玩家获胜
5. 当两个玩家都获胜则不符合条件
6. 当只有玩家一获胜，判断棋局上 'X'的个数是否等于'O'的个数加一
7. 当只有玩家二获胜，判断棋局上'O'的个数是否等于'X'的个数


### 玩家获胜的情况

1. 水平的三个字符都一样： ```board[i][0] === board[i][1] && board[i][1] === board[i][2]```
2. 垂直的三个字符都一样：```board[0][i] === board[1][i] && board[1][i] === board[2][i]```
3. 正对角线的三个字符一样：```board[0][0] === board[1][1] && board[1][1]=== board[2][2]```
4. 反对角线的三个字符都一样:```board[0][2] === board[1][1] && board[1][1]=== board[2][0] ```



## 代码

```javascript
/**
 * @param {string[]} board
 * @return {boolean}
 */
var validTicTacToe = function(board) {
	let XNumber = 0;//X的个数
	let ONumber = 0;//O的个数
	let player1Win = false;
	let player2Win = false;

	// 统计X和O的个数
	for(let i = 0;i<board.length;i++){
		for(let j = 0;j<board[i].length;j++){
			if(board[i].charAt(j) === 'X'){
				XNumber++;
			}else if(board[i].charAt(j) === 'O'){
				ONumber++;
			}
		}
	}
	if(XNumber === ONumber+1 || XNumber === ONumber){
		// 判读是否有玩家获胜
		//判断一行
		for(let i = 0;i<board.length;i++){
			if(board[i][0] === board[i][1] && board[i][1] === board[i][2]){
				if(board[i][0] === 'X'){
					player1Win = true;
				}else if(board[i][0] === 'O'){
					player2Win = true;
				}
			}
		}
		// 判断一列
		for(let i = 0;i<board.length;i++){
			if(board[0][i] === board[1][i] && board[1][i] === board[2][i]){
				if(board[0][i] === 'X'){
					player1Win = true;
				}else if(board[0][i] === 'O'){
					player2Win = true;
				}
			}
		}

		// 判断对角线
		if(board[0][0] === board[1][1] && board[1][1]=== board[2][2]){
			if(board[0][0] === 'X'){
				player1Win = true;
			}else if(board[0][0] === 'O'){
				player2Win = true;
			}
		}

		if(board[0][2] === board[1][1] && board[1][1]=== board[2][0]){
			if(board[0][2] === 'X'){
				player1Win = true;
			}else if(board[0][2] === 'O'){
				player2Win = true;
			}
		}

		// 玩家一玩家二都赢
		if(player1Win && player2Win){
			return false;
		}


		// 玩家一赢，玩家二不赢
		if(player1Win && !player2Win){
			if(XNumber === ONumber + 1){
				return true;
			}else{
				return false;
			}
		}

		// 玩家二赢，玩家一不赢
		if(!player1Win && player2Win){
			if(XNumber === ONumber){
				return true;
			}else{
				return false;
			}
		}

		// 都不赢
		if(!player1Win && !player2Win){
			return true;
		}
	}

	return false;
};

```