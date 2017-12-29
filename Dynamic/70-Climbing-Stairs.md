#  70. Climbing Stairs (Java)

## 題目

You are climbing a stair case. It takes n steps to reach to the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

Note: Given n will be a positive integer.


**Example 1:**
```
Input: 2
Output:  2
Explanation:  There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```
**Example 2:**
```
Input: 3
Output:  3
Explanation:  There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

## 翻譯

你有一個爬樓梯問題，需要幾步才能爬到頂端。

你每次只能往上一步或二步。計算有幾種方式可到達頂端？

注意：n 為正整數

**範例 1:**
```
Input: 2
Output:  2
驗證:  有兩種方式可到達頂端。
1. 1 步 + 1 步
2. 2 步
```
**範例 2:**
```
Input: 3
Output:  3
驗證:  有三種方式可到達頂端。
1. 1 步 + 1 步 + 1 步
2. 1 步 + 2 步
3. 2 步 + 1 步
```

## 解法

### Java

##### Solution 1.

這題仔細看可以發現是費氏數列，使用這列方式記錄每筆數值。

- 動態規劃
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
class Solution {
    public int climbStairs(int n) {
        int arr[]=new int [n+1];
        arr[0]=1;
        arr[1]=1;
        for(int i=2;i<=n;i++)
        		arr[i]=arr[i-1]+arr[i-2];
        return arr[n];
    }
}
```

### C

##### Solution 1.

這題仔細看可以發現是費氏數列。

- 動態規劃
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```C
int climbStairs(int n) {
  int arr[n + 1], i = 2;
  arr[0] = 1;
  arr[1] = 1;
  for (; i <= n; i++)
    arr[i] = arr[i - 1] + arr[i - 2];
  return arr[n];
}
```