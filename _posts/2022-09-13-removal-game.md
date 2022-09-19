---
title: CSES Removal Game
date: 2022-09-13 00:20:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1097/ "CSES-Removal Game")

**作法**
===

DP

**Code**
===

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;
vector<ll> score(5005);
vector<vector<ll>> dp(5005, vector<ll>(5005));
vector<vector<bool>> seen(5005, vector<bool>(5005));
ll f(int l, int r){
    if(l == r) return score[r] - score[l-1];
    if(seen[l][r]) return dp[l][r];
    seen[l][r] = true;
    dp[l][r] = score[r] - score[l-1] - min(f(l+1, r), f(l, r-1));
    return dp[l][r];
}
int main(){
    int n; cin >> n;
    for(int i=1; i<=n; i++){
        cin >> score[i];
        score[i] += score[i-1];
    }
    cout << f(1, n);
    return 0;
}
```