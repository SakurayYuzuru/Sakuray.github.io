---
title: Sliding Window
date: 2025-09-24 17:25:49
tags: Algorithm
---

- 本篇分成三个部分，用于解释如何解决*滑动窗口*的问题
这是一种*双指针/区间维护*技巧，本质是:  
    1. 窗口区间$[l, r]$表示当前子区间  
    2. 根据题目要求不断扩展`r`，直到满足条件
    3. 当窗口不再满足条件时，收缩`l`，直到恢复条件
    4. 在这个过程中统计答案
- 时间复杂度通常为$O(n)$

## 定长滑动窗口
- 特点: 窗口长度固定为$k$
- 处理方式: 
    - 每次右移`r`，把元素加入窗口
    - 如果$r - l + 1 > k$，则移出`l`，再右移`r`
- 典型问题:
    - 求窗口内的最值
    - 求窗口内的和、平均值
    - 求窗口内的不同元素个数
- 代码示例
```cpp
int maxSumSubarray(const std::vector<int>& nums, int k){
    int n = nums.size();
    int left = 0, right = 0, sum = 0, ans = std::numeric_limits<int>::min();

    while(right < n){
        sum += nums[right ++];
        if(right - left == k){
            ans = std::max(ans, sum);
            sum -= nums[left --];
        }
    }

    return ans;
}
```
