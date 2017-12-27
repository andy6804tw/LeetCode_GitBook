#  67. Add Binary (Java)

## 題目

Given two binary strings, return their sum (also a binary string).

For example,
a = "11"
b = "1"
Return "100".

## 翻譯

給予兩個二進位字串，回傳總和(僅有二進位字串)。

舉例,
a = "11"
b = "1"
回傳 "100"。

## 解法

### Java

##### Solution 1.

土法煉鋼法走訪每位數相加，最後還要判斷是否有進位。

- 二元搜尋
- Run Time: 7 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
class Solution {
    public String addBinary(String a, String b) {
        int i=a.length()-1,j=b.length()-1,carry=0;
        StringBuffer str=new StringBuffer();
        while(i>=0||j>=0) {
        		if(i>=0) {
        			if(j<0) {
        				str.append((a.charAt(i)-'0'+carry)%2+"");
        				carry=(a.charAt(i)-'0'+carry)/2;
        			}
        			else {
        				str.append((a.charAt(i)-'0'+b.charAt(j)-'0'+carry)%2+"");
        				carry=(a.charAt(i)-'0'+b.charAt(j)-'0'+carry)/2;
        			}
        		}else {
    				str.append((b.charAt(j)-'0'+carry)%2+"");
    				carry=(b.charAt(j)-'0'+carry)/2;
    			}
        		i--;j--;
        }	
        if(carry>0)
        		str.append(carry+"");
        return str.reverse().toString();
    }
}
```

##### Solution 2.

方法二使用 Java 內建 BigInteger 大數下去做運算。

- 二元搜尋
- Run Time: 13 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
import java.math.BigInteger;
class Solution {
    public String addBinary(String a, String b) {
        BigInteger x=new BigInteger(a,2);
        BigInteger y=new BigInteger(b,2);
        return x.add(y).toString(2);
    }
}
```

## C

##### Solution 1.

由於 c語言沒有字串翻轉函式所以，最後使用 in-place algorithm 反轉字串。

- 二元搜尋
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```c
#define max(num1, num2) num1 > num2 ? num1 : num2;
char * addBinary(char * a, char * b) {
  int maxLen = max(strlen(a), strlen(b));
  int i = strlen(a) - 1, j = strlen(b) - 1, carry = 0, index = 0;
  char * arr = (char * ) calloc(maxLen + 1, sizeof(char));
  while (i >= 0 || j >= -0) {
    int num = 0;
    if (i >= 0)
      num += a[i--] - '0';
    if (j >= 0)
      num += b[j--] - '0';
    arr[index++] = (num + carry) % 2 + '0';
    carry = (num + carry) / 2;
  }
  if (carry > 0) {
    arr = (char * ) realloc(arr, 2 + index * sizeof(char));
    arr[index++] = carry + '0';
  }
  for (int i = 0; i < index / 2; i++) {
    char temp;
    temp = arr[i];
    arr[i] = arr[index - i - 1];
    arr[index - i - 1] = temp;
  }
  arr[index] = '\0';
  return arr;
}
```