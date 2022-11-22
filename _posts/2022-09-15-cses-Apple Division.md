---
title: CSES Apple Division
date: 2022-09-15 11:40:00 +0800
categories: [Code, CSES]
tags: [cses, dfs]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1623/ "CSES-Apple Division")

**作法**
===

DFS

**Code**
===

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;
ll n, sum;
vector<ll> apples;
ll dfs(ll pos, ll cur){
    if(pos == n){
        return abs(sum - 2 * cur);
    }
    ll ret = LLONG_MAX;
    for(int i=pos; i<n; i++){
        ret = min(ret, dfs(i + 1, cur + apples[i]));
    }
    return ret;
}
int main(){
    cin >> n;
    apples.resize(n);
    for(ll i=0; i<n; i++){
        cin >> apples[i];
        sum += apples[i];
    }
    cout << dfs(0, 0);
}
```