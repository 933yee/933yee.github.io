---
title: Time Complexity
date: 2022-09-17 18:05:00 +0800
categories: [Code, Others, Time Complexity]
tags: [time complexity]     # TAG names should always be lowercase
math: true
---

**Big-O (O)**
===

定義
: f(n) = O(g(n)) iff there exists <span style="color:red">  c, n<sub>0</sub> > 0 </span> such that 
<span style="color:red">f(n)$$\le$$ c $$\cdot$$ g(n) </span>  for all 
<span style="color:red"> n  $$\ge$$ n<sub>0</sub> </span>
<br>
<br>

意義
: 只需要找到 n<sub>0</sub> 和常數c使得所有符合n$$\ge$$ n<sub>0</sub> 的整數滿足f(n) $$\le$$ c $$\cdot$$ g(n)，則f(n) = O(g(n))成立。
<br>
<br>

**例子**
- 3n+2 = O(n)
    : 當 c=4, n<sub>0</sub> = 2 時，3n+2 $$\le$$ 4n for all n $$\ge$$ 2  

- 100n+6 = O(n)
    : 當 c=101, n<sub>0</sub> = 6 時，100n+6 $$\le$$ 101n for all n $$\ge$$ 6  

- 10n<sup>2</sup>+4n+2 = O(n<sup>2</sup>)
    : 當 c=11, n<sub>0</sub> = 5 時，10n<sup>2</sup>+4n+2 $$\le$$ 11n<sub>2</sub> for all n $$\ge$$ 5  

特性
: f(n) = O(g(n)) 代表 O((n))為f(n)的上界，因此 n = O(n) = O(n<sup>2.5</sup>) = O(n<sup>3</sup>) = O(n<sup>n</sup>)。
一般通常讓 g(n) 的值愈小愈好。
<br>
<br>

用途
: Big-O通常用於取得一個程式的 worst-case running time。