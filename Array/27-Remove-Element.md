# 27. Remove Element

## 題目

Given an array and a value, remove all instances of that value in-place and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example:**

```
Given nums = [3,2,2,3], val = 3,

Your function should return length = 2, with the first two elements of nums being 2.
```
## 翻譯

給予一個陣列和一個數值，移除陣列中所有符合該數值的數，並只能在原陣列中操作，並回傳新的長度。

不要配置新的記憶體空間給於其他陣列，你必須只能在原陣列中操作，空間複雜度 O(1)。

陣列中的元素可以隨意排序，且新的長度對原本的陣列不會有所影響。

**範例:**

```
輸入 nums = [3,2,2,3], val = 3

你的函式必須回傳長度等於2，代表前兩個數字[3,3]
```



## 解法

### Java

##### Solution 1.

這題類似 `26. Remove Duplicates from Sorted Array`，一樣在不配置任何記憶體空間狀態下將指定數字 `val` 從原本陣列中移除。

- 陣列走訪
- Run Time: 9 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int index=0;
		    for(int i=0;i<nums.length;i++) {
		    		if(nums[i]!=val) {
		    			nums[index++]=nums[i];
		    		}
		    }
		    return index;
    }
}
```

### C

##### Solution 1.

這題類似 `26. Remove Duplicates from Sorted Array`，一樣在不配置任何記憶體空間狀態下將指定數字 `val` 從原本陣列中移除。

- 陣列走訪
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
int removeElement(int *nums, int numsSize, int val){
  int index=0,i=0;
  for(;i<numsSize;i++){
    if(nums[i]!=val){
      nums[index++]=nums[i];
    }
  }
  return index;
}
```

