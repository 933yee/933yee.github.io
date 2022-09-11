---
title: CSES Minimizing Coins
date: 2022-09-11 12:25:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1634/ "CSES-Minimizing Coins")

**作法**
===

DP


**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
vector<int> dp(1000005, INT_MAX), coins(105);

int main(){
    int n, x;
    cin >> n >> x;
    for(int i=0; i<n; i++){
        cin >> coins[i];
    }
    dp[0] = 0;
    for(int i=1; i<=x; i++){
        for(int j=0; j<n; j++){
            if(i - coins[j] >= 0 && dp[i-coins[j]] != INT_MAX)
                dp[i] = min(dp[i], dp[i-coins[j]]+1);
        }
    }
    if(dp[x] == INT_MAX) 
        cout << -1;
    else 
        cout << dp[x];
    return 0;
}
```