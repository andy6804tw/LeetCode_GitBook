# 7. Reverse Integer 

## 題目

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**
```
Input: 123
Output:  321
```
**Example 2:**
```
Input: -123
Output: -321
```
**Example 3:**
```
Input: 120
Output: 21
```

Note:
Assume we are dealing with an environment which could only hold integers within the 32-bit signed integer range. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

## 翻譯

給予一個 32-bit 整數(包含正負數)，並反轉他們的位數。

**範例 1:**
```
Input: 123
Output:  321
```
**範例 2:**
```
Input: -123
Output: -321
```
**範例 3:**
```
Input: 120
Output: 21
```

注意：
假使我們的執行環境只能處理 32-bit 有號整數範圍(2147483647~-2147483648)，為了符合題意假使整數溢位則函式回傳0。


## 解法

### Java 

##### Solution 1.

此方法比較暴力若超出 Integer 範圍就輸出 0，其餘利用 StringBuffer 做字串反轉。

- StringBuffer 類別型態
- Run Time: 54 ms
- 時間複雜度 O(1)
- 空間複雜度 O(1)

```java
class Solution {
    public  int reverse(int x) {
		long ans=0;
		if(x==-2147483648)
			return 0;
		if(x<0) {
			ans=Long.parseLong("-"+new StringBuffer(-x+"").reverse().toString());
			if(ans<-2147483648)
				ans=0;
		}else {
			ans=Long.parseLong(new StringBuffer(x+"").reverse().toString());
			if(ans>2147483647)
				ans=0;
		}
		return (int)ans;
    }
}
```



### C

##### Solution 1.

此方法是利用餘數求個位數，從尾部每次先 %10 再除以 10 直到 x等於 0 為止，跳出迴圈後第一個就是判斷該數是否超出 int 範圍(2147483647~-2147483648)，若超出範圍輸出 0 反之輸出答案，記住變數 tot 要設為長整數 long 不然步行判斷有無溢位(overflow)。

- 數學解法
- Run Time: 15 ms
- 時間複雜度 O($$log10$$n)
- 空間複雜度 O(1)

```c
int reverse(int x){
  long tot=0;
  while(x!=0){
    tot = (tot * 10) + (x % 10);
    x /= 10;
  }
  if (tot > INT_MAX || tot < INT_MIN)
    return 0;
  else
    return tot;
}
```

