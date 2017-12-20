# 198. House Robber 

## 題目

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security system connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given a list of non-negative integers representing the amount of money of each house, determine the maximum amount of money you can rob tonight without alerting the police.

## 翻譯

你是一個專業的竊盜，計畫偷竊一條街道上的房子，每間房子藏有一些錢，有一個阻止你繼續偷竊的條件是當你同一晚連續偷竊兩間相鄰的房子系統保全會自動通知警方。

給予一個正整數數列代表每間房子藏有的金額，在無處發保全情況下計算出今晚你可以偷竊的最高金額。

## 解法

### Java

##### Solution 1.

這題運用一些小技巧使用迴圈走偶數，迴圈內索引值 i+1 就為奇數位置了，但每次要判斷奇數位置是否超出陣列大小，然而每次 tot1 和 tot2 都判斷兩者誰大然後覆寫，保持每次相加都是最大值，最後跳出迴圈依樣回傳兩者最大的一方。

要考慮這種情況 3 1 1 2＝>最大值為5

- 陣列走訪
- Run Time: 0 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public int rob(int[] nums) {
        int tot1=0,tot2=0;
        for(int i=0;i<nums.length;i+=2) {
        		tot1=Math.max(tot1+=nums[i], tot2);
        		if(i+1<nums.length)
        			tot2=Math.max(tot1, tot2+=nums[i+1]);
        }
        return Math.max(tot1, tot2);
    }
}
```

### C

##### Solution 1.

這題運用一些小技巧使用迴圈走偶數，迴圈內索引值 i+1 就為奇數位置了，但每次要判斷奇數位置是否超出陣列大小，然而每次 tot1 和 tot2 都判斷兩者誰大然後覆寫，保持每次相加都是最大值，最後跳出迴圈依樣回傳兩者最大的一方。

C 語言由於沒有直接判斷大小的函式所以就使用 `#define` 自己用問號表達式定義一個比大小方法。

要考慮這種情況 3 1 1 2＝>最大值為5

- 陣列走訪
- Run Time: 0 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
#define max(num1,num2) num1>num2?num1:num2; 
int rob(int * nums, int numsSize) {
  int num1 = 0, num2 = 0, i = 0;
  for (i = 0; i < numsSize; i += 2) {
    num1 = max(num1 + nums[i], num2);
    if (i + 1 < numsSize)
      num2 = max(num1, num2 + nums[i + 1]);
  }
  return max(num1, num2);
}
```
