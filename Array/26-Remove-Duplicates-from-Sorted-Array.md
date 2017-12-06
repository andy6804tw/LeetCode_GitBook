#  26. Remove Duplicates from Sorted Array

## 題目

Given a sorted array, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

**Example:**

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.
It doesn't matter what you leave beyond the new length.
```

## 翻譯

給予一個排序過的陣列，原地移除重複的數值，並計算回傳不重複數值的陣列長度。

不要配置而外記憶體空間給其他陣列，你只能原地修改輸入的陣列，空間複雜度 O(1)。


## 解法

### Java

##### Solution 1.

由於題目要求要使用 `duplicates in-place` 不增加額外記憶體方式將原本資料複寫並計算，所以就使用陣列走訪方式一個個去跟上一個比對，並寫入 index 的位置中，index 總數表示陣列中不重複數的數量，如果提議沒規定不可使用外部空間的限制，其實最直覺方式可以利用 Java 的 Set 集合下去實作， Set 會自動把重複數值捨棄。

- 陣列走訪
- Run Time: 14 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int index=0;
		    for(int i=0;i<nums.length;i++) {
		    		if(i==0||nums[i]>nums[i-1]) {
		    			nums[index++]=nums[i];
		    		}
		    }
		    return index;
    }
}
```

### C

##### Solution 1.

由於題目要求要使用 `duplicates in-place` 不增加額外記憶體方式將原本資料複寫並計算，所以就使用陣列走訪方式一個個去跟上一個比對，並寫入 index 的位置中，index 總數表示陣列中不重複數的數量。

- 陣列走訪
- Run Time: 12 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```js
int removeDuplicates(int *nums, int numsSize){
  int index=0,i=0;
  for(;i<numsSize;i++){
    if(i==0||nums[i]>nums[i-1]){
      nums[index++]=nums[i];
    }
  }
  return index;
}
```

