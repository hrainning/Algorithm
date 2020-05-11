## 题目描述

输入一个递增排序的数组和一个数字S，在数组中查找两个数，使得他们的和正好是S，如果有多对数字的和等于S，输出两个数的乘积最小的。

## 解题思路

可以设置两个指针，一个指向第一个，一个指向最后一个，若和大了则后指针前挪，若小了前指针后挪。本质上是选择所有的两个数的组合进行判别是否等于S，但是删除掉了一些可以直接跳过的要素，如：第一个与最后一个相加要小，则1与最大值前方任意一个相加都必不可能得到相等。

为了得到乘法最小，既可知，其为最先找到的一对。

**code 1 **

```c++
class Solution {
public:
     vector<int> FindNumbersWithSum(vector<int> array, int sum) {
		int s=0, e=array.size()-1;
		vector<int> res;
		while (s < e) {
			if (array[s] + array[e] == sum) {
				res.push_back(array[s]);
				res.push_back(array[e]);
				return res;
			}
			else if (array[s] + array[e] <sum)
			{
				s++;
			}
			else
			{
				e--;
			}
		}
		return res;
     }
};
```



