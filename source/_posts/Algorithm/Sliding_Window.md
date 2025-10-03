---
title: Sliding Window
date: 2025-09-24 17:25:49
tags:
---

This section is divided into three parts, explaining how to solve "*sliding window*" problems.

## Fixed-length sliding window
These types of problems typically provide a fixed window size $k$ and a boundary condition; the goal is usually to find the largest possible range that satisfies the given condition.
So we could solve these like:
```textplain
int FixedLengthSlidingWindow(nums, k):
    n = length(nums);
    ans = 0, l = 0, r = 0;
    cnt = 0;

    while(r ++ < n):
        cnt += nums.at(r) - nums.at(l ++);
        ans = max(ans, cnt);

    return ans;
```
