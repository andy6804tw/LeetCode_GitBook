# 28. Implement strStr()

## 題目

Implement strStr().

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.

**Example 1:**

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

## 翻譯

實作 strStr()。

找出子字串 needle 是否出現在字串 haystack 裡，若有解回傳字首索引值，反之回傳 -1

這裡要注意的是當子字串大於主字串時要回傳 -1 ，子字串等於 0 時回傳 0。  

**範例 1:**

```
輸入: haystack = "hello", needle = "ll"
輸出: 2
```

**範例 2:**

```
輸入: haystack = "aaaaa", needle = "bba"
輸出: -1
```

## 解法

### Java

##### Solution 1.

Java的優點大量函式庫可以套用，使用 String 類別裡的 indexOf() 方法即可得出答案 。

- String 函式
- Run Time: 6 ms
- 時間複雜度: O(1)
- 空間複雜度: O(1)

```java
class Solution {
    public int strStr(String haystack, String needle) {
        return haystack.indexOf(needle);
    }
}
```

##### Solution 2.

這個方法是用子字串切割逐一比對字串，使用 String 類別裡的 substring() 方法。

- String 函式
- Run Time: 8 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
   public int strStr(String haystack, String needle) {
		int haystackLength=haystack.length(),needleLength=needle.length(),i=0;
		if(haystackLength<needleLength)
    			return -1;
		else if(needleLength==0) {
			return 0;
		}
        while(i<=haystackLength-needleLength) {
        		if(haystack.substring(i, i+needleLength).equals(needle))
        			return i;
        		i++;
        }
        	return -1;
    }
}
```

### C

##### Solution 1.

此方法跟 Java 解法2ㄧ樣，若要使用真正演算法解請參考 KMP。

- 陣列走訪、字元比對
- Run Time: 553 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
int strStr(char *haystack, char *needle){
   int haystackLength = strlen(haystack), needleLength = strlen(needle), i = 0, j = 0;
   if (haystackLength < needleLength)
     return -1;
   else if (needleLength == 0)
     return 0;
   char arr[needleLength], origin[haystackLength];
   for (; i < haystackLength;i++){
     for (j=0; j < needleLength;j++){
       if (haystack[i + j] != needle[j]){
          break;
       }
      }
      if (j == needleLength)
      return i;
    }
    return -1;
}
```