---
title: 'Add Two Numbers'
description:
date: 2021-11-04T21:23:28+08:00
image:
math:
license:
categories:
  - linked-list
  - math
tags:
  - leetcode
hidden: false
comments: false
draft: false
---

## 两数相加
<!--more-->

Category	Difficulty	Likes	Dislikes
algorithms	Medium (40.97%)	7007	-

Tags
linked-list | math

Companies
adobe | airbnb | amazon | bloomberg | microsoft

algorithms Medium (40.97%) Likes: 6991 Dislikes: 0 Total Accepted: 1M Total Submissions: 2.6M
Testcase Example: '[2,4,3]\n[5,6,4]'

给你两个   非空 的链表，表示两个非负的整数。它们每位数字都是按照   逆序   的方式存储的，并且每个节点
只能存储   一位   数字。

请你将两个数相加，并以相同形式返回一个表示和的链表。

你可以假设除了数字 0 之外，这两个数都不会以 0  开头。

示例 1：

```java

 输入：l1 = [2,4,3], l2 = [5,6,4]
 输出：[7,0,8]
 解释：342 + 465 = 807.

```

示例 2：

```java
 输入：l1 = [0], l2 = [0]
 输出：[0]

```

示例 3：

```java

 输入：l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
 输出：[8,9,9,9,0,0,0,1]

```

提示：

每个链表中的节点数在范围 [1, 100] 内 0 题目数据保证列表表示的数字不含前导零

/

```java
// @lc code=start

//  Definition for singly-linked list.
 public class ListNode {
     int val;
     ListNode next;
     ListNode() {}
     ListNode(int val) { this.val = val; }
     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 }

class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode pre = new ListNode(0);
        ListNode curr = pre;
        int carry = 0;
        while (l1 != null || l2 != null) {
            int x = l1 != null ? l1.val : 0;
            int y = l2 != null ? l2.val : 0;
            int sum = x + y + carry;
            //进位数字
            carry = sum / 10;
            //本位数字
            sum = sum % 10;
            curr.next = new ListNode(sum);
            curr = curr.next;
            if (l1 != null) {
                l1 = l1.next;
            }
            if (l2 != null) {
                l2 = l2.next;
            }
        }
        //最后一位是否进位
        if (carry == 1) {
            curr.next = new ListNode(carry);
        }
        //去除第一个节点
        return pre.next;
    }
}
// @lc code=end

```
