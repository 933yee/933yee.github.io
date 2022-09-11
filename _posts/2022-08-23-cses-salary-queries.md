---
title: CSES Salary Queries
date: 2022-08-23 21:11:00 +0800
categories: [Code, CSES]
tags: [cses, segment tree]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/result/4483741/ "CSES-Salary Queries")


**作法**
===
1. 離散化(discretization) + 線段樹(segment tree)

2. 離散化(discretization) + BIT(binary indexed tree)

**Code1**
===

```cpp
#include <bits/stdc++.h>
#define io ios_base::sync_with_stdio(0), cin.tie(0), cout.tie(0);
using namespace std;
vector<int> v(2e5+10), t, s(1e7+10);
vector<vector<int>> op;
int query(int id, int l, int r, int ql, int qr){
    if(qr == 0 || ql > r || qr < l)
        return 0;
    if(ql <= l && qr >= r)
        return s[id];
    int m = (l+r)/2;
    return query(id*2, l, m, ql, qr) + query(id*2+1, m+1, r, ql, qr);
}
void update(int id, int l, int r, int v, int target_id){
    if(l == r){
        s[id] += v;
        return;
    }
    int m = (l+r)/2;
    m >= target_id ? update(id*2, l, m, v, target_id) : update(id*2+1, m+1, r, v, target_id); 
    s[id] = s[id*2] + s[id*2+1];
}
int relabel(int x){
    return lower_bound(t.begin(), t.end(), x) - t.begin() + 1;
}
int relabel_upper(int x){
    return upper_bound(t.begin(), t.end(), x) - t.begin();
}
int main(){
    io
    int n, q;
    cin >> n >> q;
    for(int i=1; i<=n; i++){
        cin >> v[i]; 
        t.emplace_back(v[i]);
    }
    for(int i=1; i<=q; i++){
        char c; 
        int a, b;
        cin >> c >> a >> b;
        if(c == '!')
            t.emplace_back(b);
        op.emplace_back(vector<int>{c == '!', a, b});
    }
    sort(t.begin(), t.end());
    t.erase(unique(t.begin(), t.end()), t.end());
    
    for(int i=1; i<=n; i++){
        update(1, 1, t.size(), 1, relabel(v[i]));
    }
    for(int i=0; i<q; i++){ 
        if(op[i][0] == 1){
            update(1, 1, t.size(), -1, relabel(v[op[i][1]]));
            update(1, 1, t.size(), 1, relabel(op[i][2]));
            v[op[i][1]] = op[i][2];
        }else{
            cout << query(1, 1, t.size(), 1, relabel_upper(op[i][2]))  -  query(1, 1, t.size(), 1, relabel(op[i][1])-1) << '\n';
        }
    }
    return 0;
}
```

**Code2**
===

```cpp
#include <bits/stdc++.h>
#define io ios_base::sync_with_stdio(0), cin.tie(0), cout.tie(0);
using namespace std;
vector<int> v(2e5+10), t, BIT(4e5+10);
vector<vector<int>> op;
void update(int x, int d){
    x = lower_bound(t.begin(), t.end(), x) - t.begin() + 1;
    while(x <= t.size()){
        BIT[x] += d;
        x += x & (-x);
    }
}
int find(int x){
    int ret = 0;
    while(x > 0){
        ret += BIT[x];
        x -= x & (-x);
    }
    return ret;
}
int query(int l, int r){
    int a = lower_bound(t.begin(), t.end(), l) - t.begin();
    int b = upper_bound(t.begin(), t.end(), r) - t.begin();
    return find(b) - find(a);
}
int main(){
    io
    int n, q;
    cin >> n >> q;
    for(int i=1; i<=n; i++){
        cin >> v[i]; 
        t.emplace_back(v[i]);
    }
    for(int i=1; i<=q; i++){
        char c; 
        int a, b;
        cin >> c >> a >> b;
        if(c == '!')
            t.emplace_back(b);
        op.emplace_back(vector<int>{c == '!', a, b});
    }
    sort(t.begin(), t.end());
    t.erase(unique(t.begin(), t.end()), t.end());
    
    for(int i=1; i<=n; i++){
        update(v[i], 1);
    }
    for(int i=0; i<q; i++){ 
        if(op[i][0] == 1){
            update(v[op[i][1]], -1);
            update(op[i][2], 1);
            v[op[i][1]] = op[i][2];
        }else{
            cout << query(op[i][1], op[i][2]) << '\n';
        }
    }
    return 0;
}
```
