
2026-01-02

Tags: [[Programming]] [[Algorithms]]
# Dynamic Programming Design Patterns
## Fibonacci  -  Climbing Stairs (70)
You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?
``` C
int climbStairs(int n) {
	int* array = (int*)malloc(sizeof(int)*n);
	if(n <= 2){
		return n;
	}
	array[0] = 1;
	array[1] = 2;
	for(int x = 2; x < n; x++){
		array[x] = array[x-1] + array[x-2];
	}
	return array[n-1];
}
```

## Fibonacci  -  House Robber (198)
You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return _the maximum amount of money you can rob tonight **without alerting the police**_.

``` C
int rob(int* nums, int numsSize) {
	if(numsSize == 1){
		return nums[0];
	} else if(numsSize == 2){
		// return the larger of the first two elements
		int larger = nums[0] > nums[1];
		return nums[0]*(larger)+nums[1]*(1-larger);
	}
	int* array = (int*)malloc(sizeof(int)*numsSize);
	array[0] = nums[0];
	array[1] = nums[1];
	array[2] = nums[2]+nums[0];
	for(int x = 3; x < numsSize; x++){
		if(array[x-3] > array[x-2]){
			array[x] = array[x-3]+nums[x];
		} else {
			array[x] = array[x-2]+nums[x];
		}
	}
	for(int x =0; x < numsSize; x++){
		printf("%d,", array[x]);
	}
	// return the larger of the last two elements
	int larger = array[numsSize-1] > array[numsSize-2];
	int val = array[numsSize-1]*(larger)+array[numsSize-2]*(1-larger);
	free(array);
	return val;
}
```

## Matrix         -  Unique Paths (62)
There is a robot on an m x n grid. The robot is initially located at the top-left corner (i.e., grid\[0\]\[0\]). The robot tries to move to the bottom-right corner (i.e., grid\[m - 1\]\[n - 1\]). The robot can only move either down or right at any point in time.

Given the two integers m and n, return the number of possible unique paths that the robot can take to reach the bottom-right corner.

The test cases are generated so that the answer will be less than or equal to 2 * 109.
``` C
int uniquePaths(int m, int n) {
	int srow, scol, out;
	// handle the base case of a corridor
	if(m == 1 || n == 1){
		return 1;
	}
	
	srow = m;
	scol = n;
	int** array = (int**)malloc(sizeof(int*)*srow);
	for(int x = 0; x < srow; x++){
		array[x] = (int*)malloc(sizeof(int)*scol);
	}
	
	for(int prow = 0; prow < srow; ++prow){
		for(int pcol = 0; pcol < scol; ++pcol){
			if(prow == 0 && pcol == 0){
				array[prow][pcol] = 1;
			} else if (prow == 0){
				array[prow][pcol] = array[prow][pcol-1];
			} else if (pcol == 0){
				array[prow][pcol] = array[prow-1][pcol];
			} else{
				array[prow][pcol] = array[prow][pcol-1] + array[prow-1][pcol];
			}
		}
	}
	out = array[srow-1][scol-1];
	for(int x = 0; x < srow; x++){
		free(array[x]);
	}
	free(array);
	return out;
}
```

## Matrix         -  Unique Paths 2 (63)
You are given an `m x n` integer array `grid`. There is a robot initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

An obstacle and space are marked as `1` or `0` respectively in `grid`. A path that the robot takes cannot include **any** square that is an obstacle.

Return _the number of possible unique paths that the robot can take to reach the bottom-right corner_.

The testcases are generated so that the answer will be less than or equal to `2 * 109`.
``` C
int uniquePathsWithObstacles(int** obstacleGrid, int obstacleGridSize, int* obstacleGridColSize) {

	long** array = (long**)malloc(sizeof(long*)*obstacleGridSize);
	int row, col, out;
	for(int x = 0; x < obstacleGridSize; x++){
		array[x] = (long*)malloc(sizeof(long)*obstacleGridColSize[x]);
	}
	for(row = obstacleGridSize-1; row >= 0; --row){
		for(col = obstacleGridColSize[row]-1; col >= 0; --col){
			if(obstacleGrid[row][col] == 1){
				array[row][col] = 0;
				continue;
			}
			if(row == obstacleGridSize-1 && col == obstacleGridColSize[row]-1){
				array[row][col] = 1;
				
			} else if(row == obstacleGridSize-1){
				array[row][col] = array[row][col+1];
				
			} else if(col == obstacleGridColSize[row]-1){
				array[row][col] = array[row+1][col];
			
			} else {
				array[row][col] = array[row][col+1] + array[row+1][col];
			}
		}
	}
	
	out = array[0][0];
	
	for(int x = 0; x < obstacleGridSize; x++){
		free(array[x]);
	}
	free(array);
	return out;
}
```
## Strings        -  Longest Palindromic Substring (5) 
Given a string `s`, return _the longest_ in `s`.

Solution below from leetcode
``` C
#include <stdbool.h>
#include <string.h>

char* longestPalindrome(char* s) {
    int n = strlen(s);
    bool dp[n][n];
    memset(dp, false, sizeof dp);
    int ans[2] = {0, 0};

    for (int i = 0; i < n; ++i) {
        dp[i][i] = true;
    }

    for (int i = 0; i < n - 1; ++i) {
        if (s[i] == s[i + 1]) {
            dp[i][i + 1] = true;
            ans[0] = i;
            ans[1] = i + 1;
        } else {
            dp[i][i + 1] = false;
        }
    }

    for (int diff = 2; diff < n; ++diff) {
        for (int i = 0; i < n - diff; ++i) {
            int j = i + diff;
            if (s[i] == s[j] && dp[i + 1][j - 1]) {
                dp[i][j] = true;
                ans[0] = i;
                ans[1] = j;
            } else {
                dp[i][j] = false;
            }
        }
    }

    s[ans[1] + 1] = '\0';
    return s + ans[0];
}
```

## LCS              -  Longest Common Subsequence (1143)
Given two strings `text1` and `text2`, return the length of their longest common subsequence. If there is no common subsequence, return 0.

A subsequence of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.
    For example, `"ace"` is a subsequence of `"abcde"`.
A common subsequence of two strings is a subsequence that is common to both strings.
``` Go
func longestCommonSubsequence(text1 string, text2 string) int {
	len1 := len(text1)
	len2 := len(text2)
	
	tabula := make([][]int, len1+2)
	for i := range tabula {
		tabula[i] = make([]int, len2+2)
	}
	
	for x := 1; x < len1+1; x++{
		for y := 1; y < len2+1; y++{
			if(text1[x-1] == text2[y-1]){
				tabula[x][y] = tabula[x-1][y-1] + 1
			} else {
				tabula[x][y] = max(tabula[x][y-1], tabula[x-1][y])
			}
		}
	}
	return tabula[len1][len2]
}
```
![[Pasted image 20260102182512.png]]
In this code moving diagonally downwards and adding one is when we take a letter, and moving either straight up or straight down doesn't "change" the subset at all. This way we can imagine the `a` from `ace` as next to any letter in `abcde` simply by moving through the space of the array.

## Knapsack  -  Perfect Squares (279)
Given an integer `n`, return _the least number of perfect square numbers that sum to_ `n`.

A **perfect square** is an integer that is the square of an integer; in other words, it is the product of some integer with itself. For example, `1`, `4`, `9`, and `16` are perfect squares while `3` and `11` are not.
``` python
class Solution(object):
	def numSquares(self, num):
		dp = [float('inf')] * (num + 1)
		dp[0] = 0 
		for position in range(1, num + 1):
			j = 1
			while j * j <= position:
				dp[position] = min(dp[position], dp[position - j * j] + 1)
				j += 1
				
		return dp[n]
```
1. Create a DP array of size n + 1, initialized with infinity. Set `dp[0] = 0`.
2. For each number i from 1 to n, try every square number `j*j <= i`. 
3. Update `dp[i] = min(dp[i], dp[i - j*j] + 1)`.
4. The answer is `dp[n]`

## 1D                 -  Coin Change (322)
You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return _the fewest number of coins that you need to make up that amount_. If that amount of money cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.

``` C
int coinChange(int* coins, int coinsSize, int amount) {
	int* arr = (int*)malloc(sizeof(int)*(amount+1));
	arr[0] = 0;
	int min, temp;
	
	//loop through each index < n
	for(int mainPos = 1; mainPos <= amount; mainPos++){
		min = -1;
		// find the smallest index less than mainPos
		// that is also a coin's value away
		for(int x = 0; x < coinsSize; x++){
			if(mainPos-coins[x] < 0){
				continue;
			}
			
			temp = arr[mainPos-coins[x]];
			// hits if the temp location is valid
			// and either it's lower than min
			// or if min isn't set yet then take anything valid
			if(temp != -1 && (temp + 1 < min || min == -1)){
				min = temp + 1;
			}
		
		}
		arr[mainPos] = min;
	}
	int out = arr[amount];
	free(arr);
	return out;
```
}


# References

