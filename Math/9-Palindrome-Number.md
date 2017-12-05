# 9. Palindrome Number 

## 題目

Determine whether an integer is a palindrome. Do this without extra space.

**Some hints:**
```
Could negative integers be palindromes? (ie, -1)

If you are thinking of converting the integer to string, note the restriction of using extra space.

You could also try reversing an integer. However, if you have solved the problem "Reverse Integer", you know that the reversed integer might overflow. How would you handle such case?

There is a more generic way of solving this problem.
```
# 翻譯

判斷輸入的數字是否為迴文，使用無新增任何外部空間方法實作。

**小提示:**
```
1. 負整數是否為迴文？(ie, -1)
2. 假如你想將整數轉為字串，注意額外空間的限制。
3. 你可以試試整數反轉，假如你解過 "7.Reverse Integer" ，你會知道反轉整數可能會溢位。你會如何去處理這個問題？
4. 有很多方法可以解這道題目。
```

## 解法

### Java

##### Solution 1.

這題是考迴文，所以我就很簡單的把數字轉成字元陣列依序同時重頭及尾部一一比對是否相同。

- 陣列走訪、暴力
- Run Time: 254 ms
- 時間複雜度 O(n/2)
- 空間複雜度 O(n)

```java
class Solution {
    public boolean isPalindrome(int x) {
	        char str[]=Integer.toString(x).toCharArray();
	        for(int i=0,j=str.length-1;i<j;i++,j--) {
	        		if(str[i]!=str[j])
	        			return false;
	        }
	        return true;
	}
}
```

### C

##### Solution 1.

題目小提示提到可以利用數字反轉方法來檢查是否為迴文，另外負數不為迴文數字，此外題目很像沒給反轉後會溢位的數所以不用另外判斷是否超出範圍。

- 數學解法
- Run Time: 142 ms
- 時間複雜度: O(log<sup>10</sup>n)
- 空間複雜度: O(1)

```c
bool isPalindrome(int x){
  long tot=0,y=x;
  if(x<0)
    return false;
  while(x!=0){
    tot=tot*10+x%10;
    x/=10;
  }
  if(tot==y)
    return true;
  else
    return false;
}
```
