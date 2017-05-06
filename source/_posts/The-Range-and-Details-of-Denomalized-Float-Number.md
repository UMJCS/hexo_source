---
title: The Range and Details of Denomalized Float Number
date: 2017-05-04 23:22:22
tags:
---
在实际操作计算机的时候，一些很大的浮点数（１.24*10^123)以及一些很小的浮点数(1.23*10^-125),都难以用整数的储存方式有效的储存相应的精度。
于是计算机中浮点数的表达和储存就有其独特的一套规则，这篇文章不仅会简单的解释一下浮点数的储存及表示，更重要的是解释一些特例，包括Denomalized and it's Range,以及不同数据结构下的浮点数表达和范围。
<!--more-->
## Binary Point
Just like what we familiar with,the point of decimal,Binary point is represent as Binary form,replace decimal of binary and replace power of 10 of power of 2.
For example: 1.101*2^-2 = 0.01101=1*2^-2+1*2^-3+1*2^-5

## The Sign Bit

The sign bit is as simple as it gets. 0 denotes a positive number, and 1 denotes a negative number. Flipping the value of this bit flips the sign of the number.

## The Exponent

The exponent field needs to represent both positive and negative exponents. To do this, a bias is added to the actual exponent in order to get the stored exponent. For IEEE single-precision floats, this value is 127.

Thus, an exponent of zero means that 127 is stored in the exponent field. A stored value of 200 indicates an exponent of (200–127), or 73. For reasons discussed later, exponents of −127 (all 0s) and +128 (all 1s) are reserved for special numbers.

For double precision, the exponent field is 11 bits, and has a bias of 1023.


### (-1)S x (1 + Significand) x 2(Exponent-127)

---
以上都是正常情况下浮点数的表达，但是浮点数表达中有一些特殊的情况

Exponent  | Significand | Object |
----------------------------|----------|----------|
0         | 0        |     0        
1-254 | anything |+/- fl. pt.
255 |0 |+/- ∞
255 | !=0 |NAN
0 |!=0|Denomalized

### 下面我们就来仔细看一下Denomalized的范围

If the exponent is all 0s, and the mantissa is non-zero, then the value is treated as a denormalized number. The denormalized numbers does not have an assumed leading 1 before the binary point.

For Single precision, this represents a number (-1)s × 0.m × 2-126, where s is the sign bit and m is the mantissa. For double precision, it represents as (-1)s × 0.m × 2-1022.

*The min case is that m=1×10^-23,max case is that m=1-1×10^-23*

![“数的范围”](/img/float01.jpg)
