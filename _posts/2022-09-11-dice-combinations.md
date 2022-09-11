---
title: CSES Dice Combinations
date: 2022-09-11 12:07:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1633 "CSES-Dice Combinations")

**作法**
===

DP

<br>

**Code**
===

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;
const ll M = 1e9+7;
vector<ll> dp(1000005);
int main(){
    int n; cin >> n;
    dp[0] = 1;
    for(int i=0; i<=n; i++){
        for(int j=1; j <= 6; j++){
            if(i-j >= 0)
                dp[i] = (dp[i] + dp[i-j]) % M;
        }
    }
    cout << dp[n];
    return 0;
}
```