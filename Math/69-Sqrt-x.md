#  69. Sqrt(x)

## 題目

Implement int sqrt(int x).

Compute and return the square root of x.

x is guaranteed to be a non-negative integer.


**Example 1:**
```
Input: 4
Output: 2
```
**Example 2:**
```
Input: 8
Output: 2
```
Explanation: The square root of 8 is 2.82842..., and since we want to return an integer, the decimal part will be truncated.

## 翻譯

實作 int sqrt(int x)。

計算和回傳 x 的平方根。

x 是由正整數所組成。

**範例 1:**
```
輸入: 4
輸出: 2
```
**範例 2:**
```
輸入: 8
輸出: 2
```

說明：8 的平方根為 2.82842... 因此只要回傳整數部分 2 小數點後捨棄。

## 解法

### Java

##### Solution 1.

Java 寫法利用內建的 Math.sqrt() 來計算平方根。

- 二元搜尋
- Run Time: 37 ms
- 時間複雜度: O(log n)
- 空間複雜度: O(1)

```java
class Solution {
    public int mySqrt(int x) {
        return (int)Math.sqrt(x);
    }
}
```

### C

##### Solution 1.

此方法為二元逼近法，這題會超過 int 大小所以變數記得要宣告 long 最後回傳時再強制轉型。

- 二元搜尋
- Run Time: 12 ms
- 時間複雜度: O(log n)
- 空間複雜度: O(1)

```c
int mySqrt(int x) {
    long r=x;
    while(r*r>x){
      r = (r + x / r) / 2;
    }
    return (int)r;
}
```
