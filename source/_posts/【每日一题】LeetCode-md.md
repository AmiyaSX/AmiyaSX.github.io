---
title: 【每日一题】LeetCode
date: 2022-09-21 10:38:54
tags: LeetCode
---
## 9 / 20  [最长公共前缀](https://leetcode.cn/problems/longest-common-prefix/)

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 `""`。

```c++
class Solution {

public:
/**  
 * 1.特判输入字符串为 "" 时  
 * */
 string longestCommonPrefix(vector<string>& strs) {  
    string prefix;  
    int index = 0;  
    for (string str = strs[0]; index < str.size(); index++) {  
        char c = str[index];  
        for (string str : strs) {  
            if (str == "") return "";  
            if (c != str[index] || index >= str.size()) {  
                return prefix;  
            }  
        }  
        prefix.push_back(c);  
    }  
    return prefix;  
}

};
```

## 9/21 [不同路径](https://leetcode.cn/problems/unique-paths/)
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为 “Start” ）
机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为 “Finish” ）
问总共有多少条不同的路径？
```C++
/**  
 * 不同路径  
 * （动态规划）
 * a[m][n] = a[m-1][n] + a[m][n-1] 
 **/
 int a[101][101];  
int uniquePaths(int m, int n) {  
    a[0][0] = a[1][1] = a[1][0] = a[0][1] = 0;  
    for (int i = 1; i <= m; ++i) {  
        a[i][1] = 1;  
    }  
    for (int i = 1; i <= n; ++i) {  
        a[1][i] = 1;  
    }  //两个特殊初始化很重要，因为后面计算会用到，不初始化会少算路径
    for (int i = 2; i <= m; ++i) {  
        for (int j = 2; j <= n; ++j) {  
            a[i][j] = a[i-1][j] + a[i][j-1];  
        }  
    }  
    return a[m][n];  
}
```
