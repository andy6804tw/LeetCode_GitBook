#  125. Valid Palindrome (Java)

## 題目

Related to question `168. Excel Sheet Column Title`

Given a column title as appear in an Excel sheet, return its corresponding column number.

For example:
```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

## 翻譯
相關題目 `168. Excel Sheet Column Title`

給予一列 Excel所出現的標頭欄位，回傳相對應欄位的數字。

舉例：
```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

|...|第3位數|第2位數|第1位數|
|:|:|:|
|...|676(26^2)|26(26^1)|1(26^0)|


**ex:**
```
ABA => (26^2)*1 + (26^1)*2 + (26^0)*1 = 676 + 52 + 1 = 729
```




## 解法

### Java

##### Solution 1.

這題就把它當成是一個二十六進位轉十進位位的轉換。

- 進位轉換
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public int titleToNumber(String s) {
        int tot=0;
        for(int i=0;i<s.length();i++) {
        		tot+=(int)Math.pow(26,s.length()-1-i)*(s.charAt(i)-'A'+1);
        		
        }
        return tot;
    }
}
```

### C

##### Solution 1.

這題就把它當成是一個二十六進位轉十進位位的轉換，每個英文字母利用ASCii來轉換，例如'B' = 'B'-'A'+1 = 2。

- 進位轉換
- Run Time: 6 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
int titleToNumber(char * s) {
  int tot = 0, i = 0, len = strlen(s);
  for (i = 0; i < len; i++) {
    tot += (int) pow(26, len - 1 - i) * (s[i] - 'A' + 1);
  }
  return tot;
}
```
