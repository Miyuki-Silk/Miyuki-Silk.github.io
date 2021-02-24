---
title: 【卢卡斯定理/Lucas】
date: 2021-02-24 20:01:06
tags: OIer
cover: http://i1.fuimg.com/733524/4ba584c068df3b93.png
mathjax: true
---
#### 公式刷新不出来请多试几次！！！

用法：Lucas 定理用于求解大组合数取模的问题，其中 p 必须为素数

公式：对于质数p，有

$$\binom{n}{m}\bmod p = \binom{\left\lfloor n/p \right\rfloor}{\left\lfloor m/p\right\rfloor}\cdot\binom{n\bmod p}{m\bmod p}\bmod p$$

可以知道 n mod p 和 m mod p 一定是小于p的数，可以直接求解，而$$\displaystyle\binom{\left\lfloor n/p \right\rfloor}{\left\lfloor m/p\right\rfloor}$$依然可以继续用Lucas定理求解。这也要求p的范围不能过大，一般在$$10^5$$左右即可。

边界条件：当 m == 0 时，返回1。

## Code:
``` cpp
inline int C(int n, int m)
{
    return 1ll * fac[n] * inv[m] % P * inv[n - m] % P;
}

inline int Lucas(int n, int m)
{
    if(!n || !m) return 1;
    return 1ll * lucas(n / P, m / P) * C(n % P, m % P) % P;
}
```