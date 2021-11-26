---
title: 'Validate Binary Search Tree'
description:
date: 2021-11-26T21:31:33+08:00
image:
math: true
license:
categories:
  - leetcode
tags:
  - depth-first-search
  - tree
hidden: false
comments: false
draft: false
---

## 验证二叉搜索树

| Category   | Difficulty      | Likes | Dislikes |
| ---------- | --------------- | ----- | -------- |
| algorithms | Medium (35.09%) | 1316  | -        |

给你一个二叉树的根节点 root ，判断其是否是一个有效的二叉搜索树。

有效 二叉搜索树定义如下：

节点的左子树只包含 小于 当前节点的数。节点的右子树只包含 大于 当前节点的数。所有左子树和右子树自身必
须也是二叉搜索树。

```
示例 1：

输入：root = [2,1,3] 输出：true
```

```
示例 2：

输入：root = [5,1,4,null,null,3,6] 输出：false 解释：根节点的值是 5 ，但是右子节点的值是 4 。

```

> 提示：树中节点数目范围在[1, 104] 内 -231 <= Node.val <= 231 - 1

```java
    //二叉搜索树 左节点小于右节点
    public boolean isValidBST(TreeNode root) {
        //add 添加到队尾 push 添加的队头
        Deque<TreeNode> stack = new LinkedList<>();
        Integer pre = -Integer.MAX_VALUE;
        while (!stack.isEmpty() || root != null) {
            while (root != null) {
                stack.push(root);
                root = root.left;
            }
            root = stack.pop();
            // 如果中序遍历得到的节点的值小于等于前一个 pre，说明不是二叉搜索树
            if (root.val <= pre) {
                return false;
            }
            pre = root.val;
            root = root.right;
        }
        return true;
    }
```
