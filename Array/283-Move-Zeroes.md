# 283. Move Zeroes

## 題目

Given an array nums, write a function to move all 0's to the end of it while maintaining the relative order of the non-zero elements.

For example, given nums = [0, 1, 0, 3, 12], after calling your function, nums should be [1, 3, 12, 0, 0].

Note:
You must do this in-place without making a copy of the array.
Minimize the total number of operations.

## 翻譯

給予一個陣列 nums，寫一個函式移動所有的 0 道陣列的尾端，非 0 元素同時保留原本順序。

舉例，給予 nums = [0, 1, 0, 3, 12]，呼叫函式後必須變成 [1, 3, 12, 0, 0]。

注意：
你必須使用原地演算法，不要額外配置陣列位置。最小化你的指令。

## 解法

### Java

##### Solution 1.

題目要求不能配置新的空間，必須在原本陣列做修改勢必複雜度不超過 O(n)。

- 字串處理
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int index=0;
        for(int i=0;i<nums.length;i++) {
        		if(nums[i]!=0) {
        			nums[index++]=nums[i];
        		}
        }
        for(int i=index;i<nums.length;i++)
        		nums[i]=0;
    }
}
```

### C

##### Solution 1.

題目要求不能配置新的空間，必須在原本陣列做修改勢必複雜度不超過 O(n)。

- 字串處理
- Run Time: 16 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
void moveZeroes(int * nums, int numsSize) {
  int index = 0, i = 0;
  for (i = 0; i < numsSize; i++) {
    if (nums[i] != 0) {
      nums[index++] = nums[i];
    }
  }
  for (int i = index; i < numsSize; i++)
    nums[i] = 0;
}
```

