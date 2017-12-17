# 292. Nim Game

## 題目

You are playing the following Nim Game with your friend: There is a heap of stones on the table, each time one of you take turns to remove 1 to 3 stones. The one who removes the last stone will be the winner. You will take the first turn to remove the stones.

Both of you are very clever and have optimal strategies for the game. Write a function to determine whether you can win the game given the number of stones in the heap.

For example, if there are 4 stones in the heap, then you will never win the game: no matter 1, 2, or 3 stones you remove, the last stone will always be removed by your friend.

Credits:
Special thanks to @jianchao.li.fighter for adding this problem and creating all test cases.

## 翻譯

你和你朋友兩人在玩一個組合遊戲，桌上有一堆石頭，每次一方只能拿走1~3顆石頭，拿走最後一顆的人極為獲勝，你將為比賽第一輪也就是第一個先拿走石頭的。

你要假設兩方都有深思熟慮的考慮才拿走石頭，寫一個函式給予 n 個石頭判斷你是否會贏得比賽。

舉例，假如桌上有 4 個石頭情況你必定會輸比賽;無論你拿走 1, 2, 3 顆石頭，最後一顆石頭必定是你朋友拿走。


## 解法

## Java

##### Solution 1.

這題是在兩個玩家情況下輪流拿石頭，拿到最後一個獲勝，題目有說到剩 4 顆石頭必輸，所以要盡可能想辦法讓對方拿到 4 顆(4的倍數)，以下舉幾個所有可能情況。
- 1~3顆全拿(獲勝)
- 4顆(輸)
  - 我方拿1、2、3顆對方都獲勝
- 5顆(獲勝)
  - 我方拿1顆對方剩4顆情況
- 6顆(獲勝)
  - 我方拿2顆對方剩4顆情況
- 7顆(獲勝)
  - 我方拿3顆對方剩4顆情況
- 8顆(輸)
  - 我方拿1、2、3顆對方都獲勝


- 數學解法
- Run Time: 0 ms
- 時間複雜度: O(1)
- 空間複雜度: O(1)

```java
class Solution {
    public boolean canWinNim(int n) {
        if(n<4)
        		return true;
        else
        		return (n%4)!=0;
    }
}
```
# C

##### Solution 1.

這題是在兩個玩家情況下輪流拿石頭，拿到最後一個獲勝，題目有說到剩 4 顆石頭必輸，所以要盡可能想辦法讓對方拿到 4 顆(4的倍數)，以下舉幾個所有可能情況。
- 1~3顆全拿(獲勝)
- 4顆(輸)
  - 我方拿1、2、3顆對方都獲勝
- 5顆(獲勝)
  - 我方拿1顆對方剩4顆情況
- 6顆(獲勝)
  - 我方拿2顆對方剩4顆情況
- 7顆(獲勝)
  - 我方拿3顆對方剩4顆情況
- 8顆(輸)
  - 我方拿1、2、3顆對方都獲勝


- 數學解法
- Run Time: 0 ms
- 時間複雜度: O(1)
- 空間複雜度: O(1)

```c
bool canWinNim(int n) {
    if(n<4)
        return 1;
    else
        return (n%4)!=0;
}
```
