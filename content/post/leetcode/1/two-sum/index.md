---
title: 'Two Sum'
description: 'Two Sum'
date: 2021-11-04T14:34:38+08:00
image:
math:
license:
categories:
  - spring
tags:
  - leetcode
hidden: false
comments: false
draft: false
---

@lc app=leetcode.cn id=1 lang=java

[1] 两数之和

https://leetcode-cn.com/problems/two-sum/description/

algorithms Easy (52.14%) Likes: 12492 Dislikes: 0 Total Accepted: 2.6M Total Submissions: 5.1M
Testcase Example: '[2,7,11,15]\n9'

给定一个整数数组 nums  和一个整数目标值 target，请你在该数组中找出 和为目标值 target  的那   两个  
整数，并返回它们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素在答案里不能重复出现。

你可以按任意顺序返回答案。

示例 1：

输入：nums = [2,7,11,15], target = 9 输出：[0,1] 解释：因为 nums[0] + nums[1] == 9 ，返回 [0, 1] 。

示例 2：

输入：nums = [3,2,4], target = 6 输出：[1,2]

示例 3：

输入：nums = [3,3], target = 6 输出：[0,1]

提示：

2 -10^9 -10^9 只会存在一个有效答案

进阶：你可以想出一个时间复杂度小于 O(n^2) 的算法吗？

```
// @lc code=start
class Solution {
   public int[] twoSum(int[] nums, int target) {
       HashMap<Integer, Integer> numMap = new HashMap<>();
       for (int i = 0; i < nums.length; i++) {
           if (numMap.containsKey(nums[i])) {
               return new int[] { numMap.get(nums[i]), i };
           }
           numMap.put(target - nums[i], i);
       }
       return null;
   }
}
// @lc code=end
```
