---
title: CSES Grid Paths
date: 2022-09-11 13:06:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1638/ "CSES-Grid Paths")

**作法**
===

DP


**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
const int M = 1e9+7;
vector<vector<int>> dp(1005, vector<int>(1005));

int main(){ 
    int n; cin >> n;
    char c;
    dp[0][1] = 1;
    for(int i=1; i<=n; i++){
        for(int j=1; j<=n; j++){
            cin >> c;
            if(c == '.')
                dp[i][j] = (dp[i-1][j] + dp[i][j-1]) % M;
        }
    }
    cout << dp[n][n];
    return 0;
}
```