# 58. Length of Last Word 

## 題目

Given a string s consists of upper/lower-case alphabets and empty space characters ' ', return the length of last word in the string.

If the last word does not exist, return 0.

Note: A word is defined as a character sequence consists of non-space characters only.

```
Example:

Input: "Hello World"
Output: 5
```

## 翻譯

給予一個由大小寫字母和空白所組成的字串，回傳最後一個單字的長度。

假如最後一個字母不存在回傳 0。

注意：一個單字的定義是連續且無空白的字母所組成。

```
範例：

輸入: "Hello World"
輸出: 5
```

## 解法

### Java

##### Solution 1.

這題我是使用 Java 的字串切割 split 並取出最後一筆字串回傳長度。

- 字串處理
- Run Time: 7 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
	public int lengthOfLastWord(String s) {
		String arr[] = s.split(" ");
		if (arr.length == 0)
			return 0;
		else
			return arr[arr.length - 1].length();
	}
}
```

### C

##### Solution 1.

這題使用 C語言的字串切割，並走訪每個切割並記錄字母數，回傳最後的數目。

- 字串處理
- Run Time: 0 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```c
int lengthOfLastWord(char * s) {
  char * arr = strtok(s, " ");
  int count = 0;
  while (arr != NULL) {
    count = (int) strlen(arr);
    arr = strtok(NULL, " ");
  }
  return count;
}
```


