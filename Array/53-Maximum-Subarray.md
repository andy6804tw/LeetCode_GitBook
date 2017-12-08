# 53. Maximum Subarray

## 題目

Find the contiguous subarray within an array (containing at least one number) which has the largest sum.

For example, given the array [-2,1,-3,4,-1,2,1,-5,4],
the contiguous subarray [4,-1,2,1] has the largest sum = 6.


More practice:
If you have figured out the O(n) solution, try coding another solution using the divide and conquer approach, which is more subtle.

## 翻譯

找出陣列中連續的最大子字串數列總和(連續至少一個數字)。

例子，給予一個陣列
[-2,1,-3,4,-1,2,1,-5,4]
連續的子數列為 [4,-1,2,1] 有最大總和 6。

進階練習：
假如你有找出時間複雜度 O(n) 解法，試著用分而治之法讓時間複雜度為 O(n log n)。

## 解法

### Java

##### Solution 1.

Kadane's演算法能夠使用一個迴圈得出答案，若要更快速就要使用分而治之來實作了，間單蘭說Kadane's演算法就是當遇到負數就歸零，每次相加結果取最大數。
如果整個陣列都是負數也要輸出最小值，所以一開始 max 要設定最小值 Integer.MIN_VALUE = -2147483648。

- 陣列走訪
- Run Time: 14 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public int maxSubArray(int[] nums) {
		int tot = 0, max = Integer.MIN_VALUE;
		for (int i = 0; i < nums.length; i++) {
			tot += nums[i];
			if (max < tot) {
				max = tot;
			}
			if (tot <= 0) {
				tot = 0;
			}
		}
		return max;
    }
}
```

### C

##### Solution 1.

Kadane's演算法能夠使用一個迴圈得出答案，若要更快速就要使用分而治之來實作了，間單蘭說Kadane's演算法就是當遇到負數就歸零，每次相加結果取最大數。
INT_MIN = -2147483648，為 limits.h 函式庫得值。

- 陣列走訪
- Run Time: 6 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
int maxSubArray(int * nums, int numsSize) {
  int i = 0, tot = 0, max = INT_MIN;
  for (; i < numsSize; i++) {
    tot += nums[i];
    if (max < tot)
      max = tot;
    if (tot < 0)
      tot = 0;
  }
  return max;
}
```



