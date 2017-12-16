# 242. Valid Anagram

## 題目

Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

Note:
You may assume the string contains only lowercase alphabets.

Follow up:
What if the inputs contain unicode characters? How would you adapt your solution to such case?

## 翻譯

給予兩個字串 s 和 t，寫一個函式判斷 t 是否為 s 的重組字。

舉個例子：
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

注意：
你可以假設所有字串僅只包含小寫字母。


## 解法

### Java

##### Solution 1.

分別將兩字串切成字串陣列再由內建 Arrays 做字元排序，最後依序做比對，一開始兩字串長度不同即可立即回傳 false

- 字串處理
- Run Time: 146 ms
- 時間複雜度: O(n log n)
- 空間複雜度: O(n)

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())return false;
    		String arrS[]=s.split(""),arrT[]=t.split("");
    		Arrays.sort(arrS);
    		Arrays.sort(arrT);
    		for(int i=0;i<arrS.length;i++) {
    			if(!arrS[i].equals(arrT[i]))
    				return false;
    		}
    		return true;
    }
}
```

##### Solution 2.

方法二跟一雷同，差別在於最後判斷兩字串方法，直接使用 Arrays.equals() 方法來比對兩字串陣列。

- 字串處理
- Run Time: 122 ms
- 時間複雜度: O(n log n)
- 空間複雜度: O(n)

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length()!=t.length())return false;
    		String arrS[]=s.split(""),arrT[]=t.split("");
    		Arrays.sort(arrS);
    		Arrays.sort(arrT);
    		return Arrays.equals(arrS, arrT);
    }
}
```

## C

##### Solution 1.

分別將兩字串切成字串陣列再由內建 Arrays 做字元排序，最後依序做比對，一開始兩字串長度不同即可立即回傳 false

- 字串處理
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
bool isAnagram(char * s, char * t) {
  if (strlen(s) != strlen(t))
    return 0;
  int arr[26] = {
    0
  }, i = 0;
  while ( * s) {
    arr[ * s - 'a']++;
    arr[ * t - 'a']--;
    s++;
    t++;
  }
  for (i = 0; i < 26; i++) {
    if (arr[i] != 0)
      return 0;
  }
  return 1;
}
```

