---
title: CSES Fibonacci Numbers
date: 2022-08-16 15:52::00 +0800
categories: [Code, CSES]
tags: [cses]     # TAG names should always be lowercase
math: true
---

---
## [Question Link](https://cses.fi/problemset/task/1722 "CSES-Fibonacci Numbers")

**作法**
===

矩陣 + 快速冪

**Code**
===

```cpp
#include <bits/stdc++.h>
#define ll long long
using namespace std;
const ll M = 1e9+7;
vector<ll> matrix_cal(vector<ll> a, vector<ll>b){
    vector<ll> ret(4);
    ret[0] = (a[0]*b[0] + a[1]*b[2])%M;
    ret[1] = (a[0]*b[1] + a[1]*b[3])%M;
    ret[2] = (a[2]*b[0] + a[3]*b[2])%M;
    ret[3] = (a[2]*b[1] + a[3]*b[3])%M;
    return ret;
}
vector<ll> binpow(ll n){
    if(n == -1) return vector<ll>{0};
    if(n == 0 || n == 1) return vector<ll>{1, 1, 1, 0};
    vector<ll> hf = binpow(n/2);
    return n % 2 ? matrix_cal(matrix_cal(hf, hf), vector<ll>{1, 1, 1, 0}) : matrix_cal(hf, hf);
}

int main(){
    ll n;
    cin >> n;
    cout << binpow(n-1)[0] << '\n';
}
```