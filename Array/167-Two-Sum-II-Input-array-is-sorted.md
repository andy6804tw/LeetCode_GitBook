#  167. Two Sum II - Input array is sorted 

## 題目

Given an array of integers that is already sorted in ascending order, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2. Please note that your returned answers (both index1 and index2) are not zero-based.

You may assume that each input would have exactly one solution and you may not use the same element twice.

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2


## 翻譯

給予一個已排序過的整數陣列，找出兩個相加會等於 target 的元素。

函式 twoSum 必須回傳兩元素的索引值，且相加總和等於 target，此外索引值1小於索引值2。

你可以假設兩元素不會重複且一定有解。

輸入: numbers={2, 7, 11, 15}, target=9
輸出: index1=1, index2=2



## 解法

### Java

##### Solution 1.

第一種方法是使用 Map 方式 key 儲存數字 value 索引值，每次去搜target-該數的值的是否有在 map 中。

- 進位轉換
- Run Time: 6 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
		int arr[] = new int[2];
		for (int i = 0; i < nums.length; i++) {
			if (map.containsKey(target - nums[i])) {
				arr[0] = Math.min(i + 1, map.get(target - nums[i]) + 1);
				arr[1] = Math.max(i + 1, map.get(target - nums[i]) + 1);
				break;
			} else {
				map.put(nums[i], i);
			}
		}
		return arr;
    }
}
```

### C

##### Solution 1.

由於C語言沒有內建 Map 所以就用陣列的方式模擬，配置一個100000大小的陣列，其中有一個小問題是陣列可能包含負數，所以將每一個數字加上1000就能避開測資的負數了(偷吃步方法)。

- 進位轉換
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```c
int *twoSum(int *numbers, int numbersSize, int target, int *returnSize){
  int arr[100000] = {0}, i = 0, *ans=(int*)calloc(2,sizeof(int));
  for(i=0;i<numbersSize;i++)
  {
    if (arr[target - numbers[i]+1000] > 0)
    {
      ans[0] = i + 1 > arr[target - numbers[i] + 1000] ? arr[target - numbers[i] + 1000] : i + 1;
      ans[1] = i + 1 < arr[target - numbers[i] + 1000] ? arr[target - numbers[i] + 1000] : i + 1;
      break;
    }else{
      arr[numbers[i] + 1000] = i + 1;
    }
  }
  *returnSize=2;
  return ans;
}
```
