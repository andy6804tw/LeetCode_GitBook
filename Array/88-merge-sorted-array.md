# 88. Merge Sorted Array (Java)

## 題目

Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

Note:
You may assume that nums1 has enough space (size that is greater or equal to m + n) to hold additional elements from nums2. The number of elements initialized in nums1 and nums2 are m and n respectively.

## 翻譯

給予兩個以排序的陣列 nums1 和 nums2 合併 nums2 到 nums1 中，形成一個以排序的陣列。

注意：
你要假設 nums1 有足夠的空間(大小大於等於m+n)去容納 nums2的所有元素。nums1 和 nums2 的原始數量分別為 m 和 n。

## 解法

### Java

##### Solution 1.

將nums2陣列內容與nums1合併，最後使用 Arrays 中的 sort() 內建陣列排序。

- 陣列走訪、排序
- Run Time: 1 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int index=0;
        for(int i=m;i<m+n;i++) {
        		nums1[i]=nums2[index++];
        }
        Arrays.sort(nums1);
    }
}
```

##### Solution .2

將nums2陣列內容與nums1合併，再來將nums1複製到暫存的temp陣列中，最後經由temp與nums2逐一走訪將小的一方依序塞入nums1中。

- 陣列走訪、排序
- Run Time: 1 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int temp[]=nums1.clone(),i=0,j=0,index=0;
        while(i<m||j<n) {
        		if(i<m&&j<n) {
        			if(temp[i]<nums2[j]) {
        				nums1[index++]=temp[i++];
        			}else {
        				nums1[index++]=nums2[j++];
        			}
        		}else if(i==m) {
        			nums1[index++]=nums2[j++];
        		}else {
        			nums1[index++]=temp[i++];
        		}	
        }
    }
}
```

### C

##### Solution 1.

將nums2陣列內容與nums1合併，最後再用氣泡排序法將nums1排序。

- 陣列走訪、排序
- Run Time: 3 ms
- 時間複雜度: O(n^2)
- 空間複雜度: O(n)

```c
void merge(int * nums1, int m, int * nums2, int n) {
  int i = m, p = n, j = 0;
  for (; i < m + n; i++)
    nums1[i] = nums2[--p];
  for (i = 0; i < m + n; i++) {
    for (j = i + 1; j < m + n; j++) {
      if (nums1[i] > nums1[j]) {
        int temp = nums1[i];
        nums1[i] = nums1[j];
        nums1[j] = temp;
      }
    }
  }
}
```

##### Solution .2

此寫法是從大到小逐一放入nums1陣列當中。

- 陣列走訪、排序
- Run Time: 3 ms
- 時間複雜度: O(n)
- 空間複雜度: O(n)

```c
void merge(int * nums1, int m, int * nums2, int n) {
  int index = m + n - 1;
  m--, n--;
  while (m >= 0 || n >= 0) {
    if (m >= 0 && n >= 0) {
      if (nums1[m] > nums2[n]) {
        nums1[index--] = nums1[m--];
      } else {
        nums1[index--] = nums2[n--];
      }
    } else if (n < 0) {
      nums1[index--] = nums1[m--];
    } else {
      nums1[index--] = nums2[n--];
    }
  }
}
```


