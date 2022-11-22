---
title: CSES Edit Distance
date: 2022-09-11 20:58:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1639/ "CSES-Edit Distance")

**作法**
===

DP

**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
vector<vector<int>> dp(5005, vector<int>(5005));
int main(){
    string s, t;
    cin >> s >> t;
    for(int i=1; i<=5000; i++){
        dp[i][0] = dp[0][i] = i;
    }
    for(int i=1; i<=s.size(); i++){
        for(int j=1; j<=t.size(); j++){
            if(s[i-1] == t[j-1])
                dp[i][j] = dp[i-1][j-1];
            else
                dp[i][j] = min(dp[i-1][j-1], min(dp[i-1][j], dp[i][j-1])) + 1;
        }
    }
    cout << dp[s.size()][t.size()];
    return 0;
}
```