# 35. Search Insert Position 

## 題目

Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.

You may assume no duplicates in the array.

**Example 1:**
```
Input: [1,3,5,6], 5
Output: 2
```
**Example 2:**
```
Input: [1,3,5,6], 2
Output: 1
```
**Example 3:**
```
Input: [1,3,5,6], 7
Output: 4
```
**Example 4:**
```
Input: [1,3,5,6], 0
Output: 0
```

## 翻譯

給予一個已排序的陣列和一個 target 值，尋找 target 是出現在陣列中，若有回傳該數的索引值，若找不到則回傳第一個大於 target 的索引值。

你可以假設陣列中沒有重複的值。

**範例 1:**
```
Input: [1,3,5,6], 5
Output: 2
```
**範例 2:**
```
Input: [1,3,5,6], 2
Output: 1
```
**範例 3:**
```
Input: [1,3,5,6], 7
Output: 4
```
**範例 4:**
```
Input: [1,3,5,6], 0
Output: 0
```

## 解法

### Java

##### Solution 1.

這題使用陣列走訪一去檢查當該數大於等於 target 就輸出答案，index 初始化維陣列總長。

- 陣列走訪
- Run Time: 5 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
		int index=nums.length;
		for (int i = 0; i < nums.length; i++) {
			if (nums[i] >= target) {
				index = i;
				break;
			}
		}
		return index;
	}
}
```

### C

##### Solution 1.

這題使用陣列走訪一去檢查當該數大於等於 target 就輸出答案，index 初始化維陣列總長。

- 陣列走訪
- Run Time: 5 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
int searchInsert(int * nums, int numsSize, int target) {
  int index = numsSize, i = 0;
  for (; i < numsSize; i++) {
    if (nums[i] >= target) {
      index = i;
      break;
    }
  }
  return i;
}
```