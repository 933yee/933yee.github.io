---
title: CSES Rectangle Cutting
date: 2022-09-11 21:41:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1744/ "CSES-Rectangle Cutting")

**作法**
===

DP

**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
vector<vector<int>> dp(505, vector<int>(505, INT_MAX));

int main(){
    int a, b;
    cin >> a >> b;
    for(int i=1; i<=a; i++){
        for(int j=1; j<=b; j++){
            if(i == j){
                dp[i][j] = 0;
                continue;
            }
            for(int k=1; k<i; k++){
                dp[i][j] = min(dp[i][j], dp[i-k][j] + dp[k][j] + 1);
            }
            for(int k=1; k<j; k++){
                dp[i][j] = min(dp[i][j], dp[i][j-k] + dp[i][k] + 1);
            }
        }
    }
    cout << dp[a][b];
    return 0;
}
```