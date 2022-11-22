---
title: CSES Removing Digits
date: 2022-09-11 12:53:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1637/ "CSES-Removing Digits")

**作法**
===

DP


**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
vector<int> dp(1000006, INT_MAX);
bool valid(int v, int k){
    while(v){
        if(v % 10 == k) 
            return true;
        v /= 10;
    }
    return false;
}
int main(){
    int n; cin >> n;
    dp[0] = 0;
    for(int i=0; i<=n; i++){
        for(int j=1; j<=9; j++){
            if(i - j >= 0 && valid(i, j))
                dp[i] = min(dp[i], dp[i-j]+1);
        }
    }
    cout << dp[n];
    return 0;
}
```