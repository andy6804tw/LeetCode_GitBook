# 205. Isomorphic Strings

## 題目

Given two strings s and t, determine if they are isomorphic.

Two strings are isomorphic if the characters in s can be replaced to get t.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

For example,
Given "egg", "add", return true.

Given "foo", "bar", return false.

Given "paper", "title", return true.

Note:
You may assume both s and t have the same length.

## 翻譯

給予兩個字串 s 和 t 判定兩字串是否同構字。

假如字串 s 的每個字元可以取代 t 則兩字串為同構字。


所有出現的字母必須用另一個字母替換，同時保留字母的順序。沒有兩個字符可以映射到同一個字母，但是一個字符可以映射到它自己。

舉例,
Given "egg", "add", return true.

Given "foo", "bar", return false.

Given "paper", "title", return true.

注意：
你必須假設兩字串長度為相同。


## 解法

### Java

##### Solution 1.

這題建立兩個 255 長度的陣列，儲存每個字母每一次出現的索引值，若索引值不同即可回傳 false。

- 字串處理
- Run Time: 8 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
class Solution {
    public boolean isIsomorphic(String s, String t) {
         int arr1[]=new int [255],arr2[]=new int [255];
        for(int i=0;i<s.length();i++) {
        		
        		if(arr1[s.charAt(i)]!=arr2[t.charAt(i)]) {
        			return false;
        		}
        		
        		arr1[s.charAt(i)]=i;
        		arr2[t.charAt(i)]=i;
        }
        return true;
    }
}
```

### C

##### Solution 1.

這題，很特別寫很多方式都會超時，最後發現把 for 迴圈改成 while 就過了，此寫法建立兩個 255 長度的陣列，儲存每個字母每一次出現的索引值，若索引值不同即可回傳 false。

- 字串處理
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```c
bool isIsomorphic(char *s, char *t){
  int arr1[255]={0}, arr2[255]={0}, i = 0;
  while(s[i]!='\0')
  {
    if (arr1[s[i]] != arr2[t[i]])
      return 0;
    arr1[s[i]] = i + 1;
    arr2[t[i]] = i + 1;
     i++;
  }
  return 1;
}

```