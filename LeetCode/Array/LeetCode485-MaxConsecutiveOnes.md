# 一、MaxConsecutiveOnes

## 1、问题

Given a binary array, find the maximum number of consecutive 1s in this array.

```
Example 1:
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.
```
**Note:**

The input array will only contain 0 and 1.
The length of input array is a positive integer and will not exceed 10,000


## 2、分析

- "0"为分隔符
- 使用临时sum和max_sum比较需要考虑全“1”情况


## 3、代码

```
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int sum = 0;
        int max_sum = 0;
        
        for (auto iter = nums.begin(); iter != nums.end(); iter++)
        {
            if (0 == *iter)
            {
                if (max_sum < sum) max_sum = sum;
                sum = 0;
            }
            if (1 == *iter) sum++;
        }
        
        return max(sum, max_sum);
    }
};
```

---
