---
title: CSES Array Description
date: 2022-09-11 18:16:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1746/ "CSES-Array Description")

**作法**
===

DP


**Code**
===

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;
const ll M = 1e9+7;
vector<vector<ll>> dp(100005, vector<ll>(105));
int main(){
    int n, m, x;
    cin >> n >> m >> x;
    if(x == 0){
        for(int i=1; i<=m; i++)
            dp[1][i]++;
    }else
        dp[1][x]++;

    for(int i=2; i<=n; i++){
        cin >> x;
        if(x == 0){
            for(int j=1; j<=m; j++)
                dp[i][j] = (dp[i-1][j] + dp[i-1][j-1] + dp[i-1][j+1]) % M;
        }else
            dp[i][x] = (dp[i-1][x] + dp[i-1][x-1] + dp[i-1][x+1]) % M;
    }
    ll res = 0;
    for(int i=1; i<=m; i++)
        res += dp[n][i];
    cout << res % M;
    return 0;
}
```