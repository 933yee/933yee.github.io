---
title: CSES Coin Combinations I
date: 2022-09-11 12:37:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1635/ "CSES-Coin Combinations I")

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
    for(int i=1; i<=x; i++){
        for(int j=0; j<n; j++){
            if(i - coins[j] >= 0)
                dp[i] = (dp[i] + dp[i - coins[j]]) % M;
        }
    }
    cout << dp[x];
    return 0;
}
```