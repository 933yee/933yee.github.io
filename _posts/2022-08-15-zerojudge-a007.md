---
title: ZeroJudge-a007 判斷質數
date: 2022-08-16 11:04::00 +0800
categories: [Code, ZeroJudge]
tags: [zerojudge]     # TAG names should always be lowercase
math: true
---

---
## [Question Link](https://zerojudge.tw/ShowProblem?problemid=a007 "ZeroJudge-a007")

**題目敘述**
===
輸入多筆測資，每筆測資包含一個整數 x (2 ≦ x ≦ 2147483647)，判斷 x 是否為質數。

**作法**
===
很明顯的，這道題目必須建立質數表來減少判斷的時間，這邊選擇使用[**埃式篩法**](https://zh.m.wikipedia.org/zh-tw/%E5%9F%83%E6%8B%89%E6%89%98%E6%96%AF%E7%89%B9%E5%B0%BC%E7%AD%9B%E6%B3%95)。然而，由於 x 的值最多可達 2147483647，直接開陣列判斷的話會炸開。我們可以從簡單的問題著手: **如何判斷一個數是質數**?
<br>
<br>
對於13而言，只需判斷 ≦ $$\sqrt{13}$$ 的質數就好，如果前半部的數都無法整除 13，後半部的部分也不可能整除。同理，要判斷 x = 2147483647 是否為質數，只需要將 x 除以 ≦ $$\sqrt{x}$$ 的質數來判斷就好。$$\sqrt{2147483647}$$ 的整數部分為 46340，所以質數表建到 46340 即可。 

**Code**
===

```cpp
#include <bits/stdc++.h>
using namespace std;
vector<int> v;
vector<bool> is_prime(46341, true);
int main(){
    ios_base::sync_with_stdio(0);
    cin.tie(0);
    is_prime[1] = false;
    for(int i=2; i<=46340; i++){ // 建表
        if(!is_prime[i]) continue;
        else v.emplace_back(i); // 小於46341的質數
        for(int j = i*i; j<= 46340; j+=i){
            is_prime[j] = false;
        }
    }
    int n;
    while(cin >> n){
        if(n > 46340){
            bool flag = false;
            for(int& i:v){
                if(n % i == 0){
                    flag = true;
                    break;
                }
            }
            if(flag) cout << "非質數\n";
            else cout << "質數\n";
        }else{
            if(is_prime[n]) cout << "質數\n";
            else cout << "非質數\n";
        }
    }
}
```