# 一、Toeplitz Matrix

## 1、问题

A matrix is Toeplitz if every diagonal from top-left to bottom-right has the same element.

Now given an M x N matrix, return True if and only if the matrix is Toeplitz.
 

**Example 1**:
```
Input: matrix = [[1,2,3,4],[5,1,2,3],[9,5,1,2]]
Output: True
Explanation:
1234
5123
9512

In the above grid, the diagonals are "[9]", "[5, 5]", "[1, 1, 1]", "[2, 2, 2]", "[3, 3]", "[4]", and in each diagonal all elements are the same, so the answer is True.
```
**Example 2**:
```
Input: matrix = [[1,2],[2,2]]
Output: False
Explanation:
The diagonal "[1, 2]" has different elements.
```
**Note**:

- matrix will be a 2D array of integers.
- matrix will have a number of rows and columns in range [1, 20].
- matrix[i][j] will be integers in range [0, 99].

## 2、分析

- 将问题分解到最小来看，实际比较的对象是$m_{i,j}$与$m_{i+1,j+1}$是否相等
- 那么遍历全部元素并按前述比较即可解决问题

## 3、代码

```
class Solution {
public:
    bool isToeplitzMatrix(vector<vector<int>>& matrix) {
        int prev_elem = matrix[0][0];
        
        if ((matrix.size() == 1) || (matrix[0].size() == 1))
            return true;
            
        for (int i = 1; i < min(matrix.size(), matrix[0].size()); i++)
        {
            if (prev_elem != matrix[i][i])
                return false;
            prev_elem = matrix[i][i];
        }
        
        return true;
    }
};
```

