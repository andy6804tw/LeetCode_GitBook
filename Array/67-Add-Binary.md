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

這題用內建的二進位計算會爆，所以只好土法煉鋼的走訪每位數相加，最後還要判斷是否有進位。

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
