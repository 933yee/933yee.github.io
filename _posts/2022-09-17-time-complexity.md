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
    : 當 c=11, n<sub>0</sub> = 5 時，10n<sup>2</sup>+4n+2 $$\le$$ 11n<sup>2</sup> for all n $$\ge$$ 5  
<br>
<br>

**特性**
- f(n) = O(g(n)) 代表 O(g(n)) 為 f(n) 的upper bound，因此 n = O(n) = O(n<sup>2.5</sup>) = O(n<sup>3</sup>) = O(n<sup>n</sup>)。一般會讓 g(n) 的值愈小愈好。
- Big-O常用於取得一個程式的 worst-case running time。

<br>

**Big-Omega($$\Omega$$)**
===

定義
: f(n) = $$\Omega$$(g(n)) iff there exists <span style="color:red">  c, n<sub>0</sub> > 0 </span> such that 
<span style="color:red">f(n)$$\ge$$ c $$\cdot$$ g(n) </span>  for all 
<span style="color:red"> n  $$\ge$$ n<sub>0</sub> </span>
<br>
<br>

意義
: 只需要找到 n<sub>0</sub> 和常數c使得所有符合n$$\ge$$ n<sub>0</sub> 的整數滿足f(n) $$\ge$$ c $$\cdot$$ g(n)，則f(n) = $$\Omega$$(g(n))成立。
<br>
<br>

**例子**
- 3n+2 = $$\Omega$$(n)
    : 當 c=3, n<sub>0</sub> = 1 時，3n+2 $$\ge$$ 3n for all n $$\ge$$ 1  

- 100n+6 = $$\Omega$$(n)
    : 當 c=100, n<sub>0</sub> = 1 時，100n+6 $$\ge$$ 100n for all n $$\ge$$ 1  

- 10n<sup>2</sup>+4n+2 = $$\Omega$$(n<sup>2</sup>)
    : 當 c=1, n<sub>0</sub> = 1 時，10n<sup>2</sup>+4n+2 $$\ge$$ n<sup>2</sup> for all n $$\ge$$ 1
<br>
<br>

**特性**
- f(n) = $$\Omega$$(g(n)) 代表 $$\Omega$$(g(n)) 為 f(n) lower bound。
- $$\Omega$$ 常用於取得一個程式的 best-case running time。

<br>

**Big-Theta($$\theta$$)**
===

定義
: f(n) = $$\theta$$(g(n)) iff <span style="color:red"> f(n) = O(g(n)) </span> and <span style="color:red"> f(n) = $$\Omega$$(g(n))</span>。 
<br>
<br>

意義
: 比 Big-O 和 Big-$$\Omega$$ 精確。
<br>
<br>

**例子**
- 3n+2 = $$\theta$$(n)
- 100n+6 = $$\theta$$(n)
- 10n<sup>2</sup>+4n+2 = $$\theta$$(n<sup>2</sup>)
<br>
<br>

**特性**
- f(n) = $$\theta$$(g(n)) 代表 $$\theta$$(g(n)) 為 f(n) tight bound。
- $$\theta$$ 常用於取得一個程式的 average-case running time。