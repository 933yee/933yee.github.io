---
title: CSES Counting Towers
date: 2022-09-11 18:44:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/2413/ "CSES-Counting Towers")

**作法**
===

DP
![algorithm](/assets/images/algorithm.png)

**Code**
===

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;
const ll M = 1e9+7;
vector<vector<ll>> dp(1000005, vector<ll>(2));

int main(){
    dp[1][0] = dp[1][1] = 1;
    for(int i=2; i<=1000000; i++){
        dp[i][0] = (dp[i-1][0]*2 + dp[i-1][1]) % M; 
        dp[i][1] = (dp[i-1][0] + dp[i-1][1]*4) % M; 
    }
    int t; cin >> t;
    while(t--){
        int n; cin >> n;
        cout << (dp[n][0] + dp[n][1]) % M << '\n';
    }
    return 0;
}
```