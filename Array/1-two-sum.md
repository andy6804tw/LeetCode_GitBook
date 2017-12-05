# 1-Two Sum

## 題目

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

**Example:**
```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```
## 翻譯

給定一個整數陣列，回傳任兩數相加等於 target 的索引值。

你可以假設每個數字(索引值)為一個解，所以同一個索引值位置不會重複計算相加。

**Example:**
```
輸入 nums = [2, 7, 11, 15], target = 9,

因為 nums[0] + nums[1] = 2 + 7 = 9,
回傳 [0, 1].
```

## 解法

### Java

##### Solution 1.

此方法最直覺用雙迴圈下去一序做比較。

- 暴力、窮舉
- Run Time:	41 ms
- 時間複雜度 O(n<sup>2</sup>)
- 空間複雜度 O(1)

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length;i++){
            for(int j=i+1;j<nums.length;j++){
                if(nums[i]+nums[j]==target){
                    int arr[]={i,j};
                    return arr; 
                }
            }
        }
		return nums;
    }
}
```

##### Solution 2.

此種方法是利用容器 HashMap 下去實作使用 Key、Value 下去做搜尋，Key 儲存 twoSum 裡的內容，Value 儲存 twoSum 裡的索引值。

- One-pass Hash Table
- Run Time:	8 ms
- 時間複雜度 O(n)
- 空間複雜度 O(n)

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> map=new HashMap<>();
		int arr[]=new int [2];
		for(int i=0;i<nums.length;i++) {
			if(map.containsKey(target-nums[i])) {
				arr[0]=map.get(target-nums[i]);
				arr[1]=i;
				return arr;
			}else {
				map.put(nums[i],i);
			}
		}
		return arr;
    }
}
```

### C

##### Solution 1.

此種方法是利用容器 HashMap 下去實作使用 Key、Value 下去做搜尋，Key 儲存 twoSum 裡的內容，Value 儲存 twoSum 裡的索引值。

- 暴力、窮舉
- Run Time:	102 ms
- 時間複雜度 O(n<sup>2</sup>)
- 空間複雜度 O(1)

```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
int *twoSum(int *nums, int numsSize, int target){
  int i=0,j=0;
  int *arr=(int *)malloc(2*sizeof(int));
  for (i=0; i < numsSize;i++){
    for (j=1+i; j < numsSize;j++){
      if(nums[i]+nums[j]==target){
        arr[0]=i;
        arr[1]=j;
        return arr;
      }
    }
  }
  return arr;
}
```
