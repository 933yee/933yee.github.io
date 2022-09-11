---
title: CSES Book Shop
date: 2022-09-11 13:31:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1158/ "CSES-Book Shop")

**作法**
===

DP


**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
vector<vector<int>> dp(1005, vector<int>(100005));
vector<pair<int, int>> books(100005);
int main(){
    int n, x;
    cin >> n >> x;
    for(int i=1; i<=n; i++){
        cin >> books[i].first;
    }
    for(int i=1; i<=n; i++){
        cin >> books[i].second;
    }

    for(int i=1; i<=n; i++){
        for(int j=0; j<=x; j++){
            dp[i][j] = dp[i-1][j];
            if(j - books[i].first >= 0)
                dp[i][j] = max(dp[i][j], dp[i-1][j-books[i].first] + books[i].second);
        }
    }
    cout << dp[n][x];
    return 0;
}
```