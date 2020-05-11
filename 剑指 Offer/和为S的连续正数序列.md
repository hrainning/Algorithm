## 题目描述

一个整型数组里除了两个数字之外，其他的数字都出现了两次。请写程序找出这两个只出现一次的数字。

## 解题思路

出发点：假设有一有序数组，找到两个数和为k。可以设置两个指针，一个指向第一个，一个指向最后一个，若和大了则后指针前挪，若小了前指针后挪，直到找到或者终结。

拓展本题：设置一个双指针，分别指向开头和末尾，小了末尾后挪，大了开头后挪，直至开头越过中值结束。

**code 1 **

```c++
class Solution {
public:
     vector<vector<int> > FindContinuousSequence(int sum) {
          int s = 1, e = 2;
          int total = 3;
          vector<vector<int> > result;
          if (sum < 3) {
               return result;
          }
          while (s <= sum / 2 + 1&& e<sum) {

               if (total < sum) {
                    e++;
                    total += e;

               }
               else
               {
                    if (total == sum) {
                         vector<int> temp;
                         for (int i = s; i <= e; i++) {
                              temp.push_back(i);
                         }
                         result.push_back(temp);
                    }
                    total -= s;
                    s++;
              
               }
          }
          return result;
     }
};

```



