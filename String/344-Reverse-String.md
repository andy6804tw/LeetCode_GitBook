# 344-Reverse String
## 題目

Write a function that takes a string as input and returns the string reversed.

**Example:**

Given s = "hello", return "olleh".

## 翻譯

將一個字串反轉後回傳

**範例:**

Given s = "hello", return "olleh".

## 解法

### Java

##### Solution 1.

將String 字串轉為 StringBuffer 類別型態，並使用裡面的 reverse() 方法。

- StringBuffer 類別型態
- Run Time: 4 ms
- 時間複雜度 O(1)
- 空間複雜度 O(1)

```java
class Solution {
    public String reverseString(String s) {
        return new StringBuffer(s).reverse().toString();
    }
}
```


### C
##### Solution 1.

使用指標方式並配置記憶體位置使用陣列索引方式從陣列 s 尾逐一回頭塞入 str指標陣列，記得加入 \0 表示字串結尾。

- 陣列走訪
- Run Time:	3 ms
- 時間複雜度 O(n)
- 空間複雜度 O(n)

```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
char *reverseString(char *s){
  int i = strlen(s) - 1, j = 0;
  char *str = (char *)malloc(strlen(s) + 1);
  for (; i >= 0; i--)
    str[j++] = s[i];
  str[i] = '\0';
  return str;
}
```

##### Solution 2.

使用指標方式一開始配置記憶體從尾逐一塞入，此方法利用指標位移方式，記得加入 \0 表示字串結尾，最後再將記憶體位置返回前頭。

- 指標陣列走訪
- Run Time:	3 ms
- 時間複雜度 O(n)
- 空間複雜度 O(n)

```c
/**
 * Note: The returned array must be malloced, assume caller calls free().
 */
char *reverseString(char *s){
  int i = strlen(s) - 1;
  char *str = (char *)malloc(strlen(s) + 1);
  while (i >= 0)
  {
    *str = s[i--];
    str++;
  }
  *str = '\0';
  str -= strlen(s);
  return str;
}
```

