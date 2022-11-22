---
title: CSES Money Sums
date: 2022-09-11 22:19:00 +0800
categories: [Code, CSES]
tags: [cses, dp]     # TAG names should always be lowercase
math: true
---

---
## [Problem Link](https://cses.fi/problemset/task/1745/ "CSES-Money Sums")

**作法**
===
1. set
2. bitset

**Code1**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
set<int> s;
int main(){
    int n; cin >> n;
    for(int i=0; i<n; i++){
        int x; cin >> x;
        vector<int> tmp;
        for(auto& i:s) tmp.emplace_back(i + x);
        for(auto& i:tmp) s.emplace(i);
        s.emplace(x);
    }
    cout << s.size() << '\n';
    for(auto& i:s) cout << i << ' ';
    return 0;
}
```

**Code2**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
bitset<1000005> bs;
int main(){
    int n, x; 
    cin >> n;
    bs[0] = 1;
    while(n--){
        cin >> x;
        bs |= (bs << x);
    }
    cout << bs.count()-1 << '\n';
    for(int i=1; i<=1000000; i++){
        if(bs[i])
            cout << i << ' ';
    }
    return 0;
}
```