# 20. Valid Parentheses

## 題目

Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

## 翻譯
給予一個字串僅有'('、 ')'、 '{'、 '}'、 '[' 和 ']'，判斷該字串是否合法。
括號必須符合左右順序開合，"()" 和 "()[]{}" 皆為合法的，而 "(]" 和 "([)]" 皆為不合法。

## 解法

### Java

##### Solution 1.

這題使用堆疊依序把對應的括號放入容器中，當遇到空堆疊或是該符號不相同時即可回傳 false，注意該字串只有括號而已沒其他字元。

- 堆疊 stack
- Run Time: 11 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```js
class Solution {
    public boolean isValid(String s) {
		Stack<Character> stack = new Stack<Character>();
		for (char c : s.toCharArray()) {
			if (c == '(')
				stack.push(')');
			else if (c == '{')
				stack.push('}');
			else if (c == '[')
				stack.push(']');
			else if (stack.isEmpty() || stack.pop() != c)
				return false;
		}
		return stack.isEmpty();
	}
}
```

### C

##### Solution 1.

由於 C 沒有 stack 所以就自己模擬把 index++ 當作 push、--index 當作 pop，依序把對應的括號放入容器中，當遇到空堆疊或是該符號不相同時即可回傳 false。

- 字元陣列實作 堆疊 stack
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
bool isValid(char *s){
  char stack[1000000];
  int i = 0, index = 0;
  while (*s)
  {
    if (*s == '(')
      stack[index++] = ')';
    else if (*s == '{')
      stack[index++] = '}';
    else if (*s == '[')
      stack[index++] = ']';
    else if (index == 0 || stack[--index] != *s)
      return 0;
    s++;
  }
  return index == 0;
}
```
