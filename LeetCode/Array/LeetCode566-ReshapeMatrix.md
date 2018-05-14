# 一、ReshapeTheMatrix

## 1、问题

In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.

You're given a matrix represented by a two-dimensional array, and two positive integers r and c representing the row number and column number of the wanted reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix in the same row-traversing order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.

**Example 1:**
```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 1, c = 4
Output: 
[[1,2,3,4]]

Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.
```
**Example 2:**
```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 2, c = 4
Output: 
[[1,2],
 [3,4]]
Explanation:
There is no way to reshape a 2 * 2 matrix to a 2 * 4 matrix. So output the original matrix.
```
**Note:**
- The height and width of the given matrix is in range [1, 100].
- The given r and c are all positive.

## 2、分析

- 如果输入是(r*c, 1)维度的矩阵则直接进行切片赋值即可
- 如何将输入(r_orig, c_orig)转化为(r*c, 1)的矩阵，有如何将(r*c, 1)的矩阵转化为(r, c)的矩阵
- 既然不同形状的矩阵都对应到同一形状矩阵，那么两者的直接对应关系是什么
- nums[r*c / c][rc % c] = reshaped[r*c / c_orig][r*c % c_orig]


## 3、代码

```
class Solution {
public:
    vector<vector<int>> matrixReshape(vector<vector<int>>& nums, int r, int c) {
        int r_orig = nums.size();
        int c_orig = nums[0].size();

        if (((1 == r_orig) && (1 == c_orig)) || (r_orig*c_orig != r*c)) return nums;

        vector<vector<int>> reshaped(r, vector<int>(c, 0));
        for (int i = 0; i < r*c; i++)
            reshaped[i / c][i % c] = nums[i / c_orig][i % c_orig];
        
        return reshaped;
    }
};
```

## 4、语言相关

1、
```
vector<vector<int>> reshaped(r, vector<int>(c, 0));
```

--- 
