#  125. Valid Palindrome (Java)

## 題目


Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

For example,
"A man, a plan, a canal: Panama" is a palindrome.
"race a car" is not a palindrome.

Note:
Have you consider that the string might be empty? This is a good question to ask during an interview.

For the purpose of this problem, we define empty string as valid palindrome.

## 翻譯
給予一個字串判斷是否為回文，只判斷字母和數字(標點符號略過)，無大小寫區分。

舉例,
"A man, a plan, a canal: Panama" 是回文.
"race a car" 不是回文.

注意：
你是否有想過字串可能為空？當你在面試時，這是個好問題。

為了題目方便，這題定義空字串為一個合法的回文。

## 解法

### Java

##### Solution 1.

這題先把所有字母轉為小寫再很直覺的走訪每個字元把英文字母和數字存入 `StringBuffer` 中最後做字串翻轉 `reverse()` 與未翻轉做比對，記得字串比對要轉為一般 `String` 型態。

- 字串處理
- Run Time: 11 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
class Solution {
    public boolean isPalindrome(String s) {
       char arr[]=s.toLowerCase().toCharArray();
        StringBuffer str=new StringBuffer();
        for(int i=0;i<arr.length;i++) {
        	if(arr[i]>='a'&&arr[i]<='z'||arr[i]>='0'&&arr[i]<='9')
        		str.append(arr[i]);
        }
        	return str.toString().equals(str.reverse().toString());
    }
}
```

##### Solution 2.

此方法使用 `replaceAll` 搭配正規表示法將英文字母和數字以外字元取代為空字串，最後再使用 `StringBuffer` 字串翻轉 `reverse()` 與未翻轉做比對，記得字串比對要轉為一般 `String` 型態。

- 字串處理
- Run Time: 33 ms
- 時間複雜度: O(n)
- 空間複雜度: O(1)

```java
public boolean isPalindrome(String s) {
    		String str=new StringBuffer(s.toLowerCase().replaceAll("[^a-z0-9]", "")).toString();
    		String reverseString=new StringBuffer(str).reverse().toString();
        return str.equals(reverseString);
    }
```

## C

##### Solution 1.

C語言什麼都必須自己來所以要手動把字串中的字母與數字抽離出來，遇到大寫字母轉成小寫 `(+ 'a' - 'A')` ，最後再同時頭尾比對每個字元是否相同，這邊要注意的是用字元陣列走訪似乎會超時(最後一筆過不了)，使用指標就會過了。

- 字串處理
- Run Time: 6 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```c
bool isPalindrome(char *s)
{
  char *arr=(char *)calloc(strlen(s)+1,sizeof(char));
  int i = 0, index = 0, j = 0, len = strlen(s);
  while (*s!='\0')
  {
    if ((*s >= 'a' && *s <= 'z') || (*s >= 'A' && *s <= 'Z') || (*s >= '0' && *s <= '9'))
    {
      if (*s >= 'A' && *s <= 'Z')
        arr[index++] = *s + 'a' - 'A';
      else
        arr[index++] = *s;
    }
    s++;
  }
  arr[index]='\0';
  for(i=0,j=index-1;i<j;i++,j--){
    if(arr[i]!=arr[j])
      return 0;
  }
  return 1;
}
```
