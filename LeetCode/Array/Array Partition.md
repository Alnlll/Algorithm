# 一、Array Partition 1

## 1、问题

Given an array of 2n integers, your task is to group these integers into n pairs of integer, say (a1, b1), (a2, b2), ..., (an, bn) which makes sum of min(ai, bi) for all i from 1 to n as large as possible.

Example 1:

```
Input: [1,4,3,2]

Output: 4
```
**Explanation**: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).

**Note**:
n is a positive integer, which is in the range of [1, 10000].
All the integers in the array will be in the range of [-10000, 10000].

## 2、分析

- 按题意是求取数字大小相关问题，对数组排序是重要手段
- 如果数组有序，那么题目的最优解为按顺序2数字一组

## 3、代码

```
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        int sum = 0;
        sort(nums.begin(), nums.end());
        for (int i = 0; i < nums.size() / 2; i++)
            sum += nums[2*i];
        
        return sum;
    }
};
```

## 4、语言相关

- vector : size()、capacity()、begin()、end()

---
