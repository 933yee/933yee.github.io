---
title: CSES Coin Combinations II
date: 2022-09-11 12:42:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1636/ "CSES-Coin Combinations II")

**作法**
===

DP


**Code**
===

```cpp
#include <bits/stdc++.h>
const int M = 1e9+7;
using namespace std;
vector<int> dp(1000005), coins(105);
int main(){
    int n, x;
    cin >> n >> x;
    for(int i=0; i<n; i++){
        cin >> coins[i];
    }
    dp[0] = 1;
    for(int i=0; i<n; i++){
        for(int j=1; j<=x; j++){
            if(j - coins[i] >= 0)
                dp[j] = (dp[j] + dp[j - coins[i]]) % M;
        }
    }
    cout << dp[x];
    return 0;
}
```