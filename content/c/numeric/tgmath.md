+++
title = "泛型数学 (C99 起)"
date = 2025-04-15T19:15:10+08:00
weight = 50
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/numeric/tgmath](https://zh.cppreference.com/w/c/numeric/tgmath)

​	头文件 [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) 包含头文件 [`<math.h>`](https://zh.cppreference.com/w/c/header/math) 及 [`<complex.h>`](https://zh.cppreference.com/w/c/header/complex)，并定义了几种[泛型宏](https://zh.cppreference.com/w/c/language/generic)。这些宏会根据实参类型决定要调用的实际函数。

​	对于每个宏，在 [`<math.h>`](https://zh.cppreference.com/w/c/header/math) 无后缀版函数中，所对应的实数类型为 double 的形参，即是所谓的*泛型形参*。（例如，[pow](https://zh.cppreference.com/w/c/numeric/math/pow) 的两个形参都是泛型形参，但 [scalbn](https://zh.cppreference.com/w/c/numeric/math/scalbn) 只有第一个形参是泛型形参）

​	如下所述，使用 [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) 宏时，传递给泛型形参的实参类型，会决定宏所选择的函数。若实参的类型与所选函数的形参类型不[兼容](https://zh.cppreference.com/w/c/language/type#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)，则行为未定义。（例如，若将复数实参传入实数限定的 [`<tgmath.h>`](https://zh.cppreference.com/w/c/header/tgmath) 宏： float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) fc; [ceil](http://zh.cppreference.com/w/c/numeric/math/ceil)(fc) 或 double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) dc; double d; [fmax](http://zh.cppreference.com/w/c/numeric/math/fmax)(dc, d) 就是未定义行为的例子）

​	注意：泛型宏在 C99 中曾以实现定义行为实现，但 C11 关键词 [_Generic](https://zh.cppreference.com/w/c/keyword/_Generic) 使得以可移植方式实现这些宏成为可能。

## 复数/实数泛型宏

​	对于所有拥有实数及复数对应的函数，存在泛型宏，调用下列函数之一：

- 实数函数：
  - float 变体 `XXXf`
  - double 变体 `XXX`
  - long double 变体 `XXXl`

- 复数函数：
  - float 变体 `cXXXf`
  - double 变体 `cXXX`
  - long double 变体 `cXXXl`



​	上述规则的一个例外是 `fabs` 宏（见下表）。

​	按以下方式决定调用的函数：

- 若泛型形参的任一实参为虚数，则行为会在每个函数参考页面上各自指定。（具体而言，`sin`、`cos`、`tan`、`sinh`、`cosh`、`tanh`、`asin`、`atan`、`asinh` 及 `atanh` 调用*实数*函数，`sin`、`cos`、`tan`、`sinh`、`tanh`、`asin`、`atan`、`asinh` 及 `atanh` 的返回类型是虚数，而 `cosh` 与 `cosh` 的返回类型是实数）
- 若泛型形参的任一实参为复数，则复数函数会得到调用，否则会调用实数函数。
- 若泛型形参的任一实参为 long double，则调用 long double 变体。否则，若任一实参是 double 或整数，则调用 double 变体。否则会调用 float 变体。

​	泛型宏如下所示：

| 泛型宏 |                         实数函数变体                         |                         实数函数变体                         |                         实数函数变体                         |                         复数函数变体                         |                         复数函数变体                         |                         复数函数变体                         |
| :----: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        |                            float                             |                            double                            |                         long double                          |                            float                             |                            double                            |                         long double                          |
|  fabs  | [`<abs>`](https://zh.cppreference.com/w/c/numeric/math/fabs) | [`<ab>`](https://zh.cppreference.com/w/c/numeric/math/fabs) | [`<abs>`](https://zh.cppreference.com/w/c/numeric/math/fabs) | [`<abs>`](https://zh.cppreference.com/w/c/numeric/complex/cabs) | [`<ab>`](https://zh.cppreference.com/w/c/numeric/complex/cabs) | [`<abs>`](https://zh.cppreference.com/w/c/numeric/complex/cabs) |
|  exp   | [`<xp>`](https://zh.cppreference.com/w/c/numeric/math/exp) | [`<x>`](https://zh.cppreference.com/w/c/numeric/math/exp)  | [`<xp>`](https://zh.cppreference.com/w/c/numeric/math/exp) | [`<exp>`](https://zh.cppreference.com/w/c/numeric/complex/cexp) | [`<ex>`](https://zh.cppreference.com/w/c/numeric/complex/cexp) | [`<exp>`](https://zh.cppreference.com/w/c/numeric/complex/cexp) |
|  log   | [`<og>`](https://zh.cppreference.com/w/c/numeric/math/log) | [`<o>`](https://zh.cppreference.com/w/c/numeric/math/log)  | [`<og>`](https://zh.cppreference.com/w/c/numeric/math/log) | [`<log>`](https://zh.cppreference.com/w/c/numeric/complex/clog) | [`<lo>`](https://zh.cppreference.com/w/c/numeric/complex/clog) | [`<log>`](https://zh.cppreference.com/w/c/numeric/complex/clog) |
|  pow   | [`<ow>`](https://zh.cppreference.com/w/c/numeric/math/pow) | [`<o>`](https://zh.cppreference.com/w/c/numeric/math/pow)  | [`<ow>`](https://zh.cppreference.com/w/c/numeric/math/pow) | [`<pow>`](https://zh.cppreference.com/w/c/numeric/complex/cpow) | [`<po>`](https://zh.cppreference.com/w/c/numeric/complex/cpow) | [`<pow>`](https://zh.cppreference.com/w/c/numeric/complex/cpow) |
|  sqrt  | [`<qrt>`](https://zh.cppreference.com/w/c/numeric/math/sqrt) | [`<qr>`](https://zh.cppreference.com/w/c/numeric/math/sqrt) | [`<qrt>`](https://zh.cppreference.com/w/c/numeric/math/sqrt) | [`<sqrt>`](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | [`<sqr>`](https://zh.cppreference.com/w/c/numeric/complex/csqrt) | [`<sqrt>`](https://zh.cppreference.com/w/c/numeric/complex/csqrt) |
|  sin   | [`<in>`](https://zh.cppreference.com/w/c/numeric/math/sin) | [`<i>`](https://zh.cppreference.com/w/c/numeric/math/sin)  | [`<in>`](https://zh.cppreference.com/w/c/numeric/math/sin) | [`<sin>`](https://zh.cppreference.com/w/c/numeric/complex/csin) | [`<si>`](https://zh.cppreference.com/w/c/numeric/complex/csin) | [`<sin>`](https://zh.cppreference.com/w/c/numeric/complex/csin) |
|  cos   | [`<os>`](https://zh.cppreference.com/w/c/numeric/math/cos) | [`<o>`](https://zh.cppreference.com/w/c/numeric/math/cos)  | [`<os>`](https://zh.cppreference.com/w/c/numeric/math/cos) | [`<cos>`](https://zh.cppreference.com/w/c/numeric/complex/ccos) | [`<co>`](https://zh.cppreference.com/w/c/numeric/complex/ccos) | [`<cos>`](https://zh.cppreference.com/w/c/numeric/complex/ccos) |
|  tan   | [`<an>`](https://zh.cppreference.com/w/c/numeric/math/tan) | [`<a>`](https://zh.cppreference.com/w/c/numeric/math/tan)  | [`<an>`](https://zh.cppreference.com/w/c/numeric/math/tan) | [`<tan>`](https://zh.cppreference.com/w/c/numeric/complex/ctan) | [`<ta>`](https://zh.cppreference.com/w/c/numeric/complex/ctan) | [`<tan>`](https://zh.cppreference.com/w/c/numeric/complex/ctan) |
|  asin  | [`<sin>`](https://zh.cppreference.com/w/c/numeric/math/asin) | [`<si>`](https://zh.cppreference.com/w/c/numeric/math/asin) | [`<sin>`](https://zh.cppreference.com/w/c/numeric/math/asin) | [`<asin>`](https://zh.cppreference.com/w/c/numeric/complex/casin) | [`<asi>`](https://zh.cppreference.com/w/c/numeric/complex/casin) | [`<asin>`](https://zh.cppreference.com/w/c/numeric/complex/casin) |
|  acos  | [`<cos>`](https://zh.cppreference.com/w/c/numeric/math/acos) | [`<co>`](https://zh.cppreference.com/w/c/numeric/math/acos) | [`<cos>`](https://zh.cppreference.com/w/c/numeric/math/acos) | [`<acos>`](https://zh.cppreference.com/w/c/numeric/complex/cacos) | [`<aco>`](https://zh.cppreference.com/w/c/numeric/complex/cacos) | [`<acos>`](https://zh.cppreference.com/w/c/numeric/complex/cacos) |
|  atan  | [`<tan>`](https://zh.cppreference.com/w/c/numeric/math/atan) | [`<ta>`](https://zh.cppreference.com/w/c/numeric/math/atan) | [`<tan>`](https://zh.cppreference.com/w/c/numeric/math/atan) | [`<atan>`](https://zh.cppreference.com/w/c/numeric/complex/catan) | [`<ata>`](https://zh.cppreference.com/w/c/numeric/complex/catan) | [`<atan>`](https://zh.cppreference.com/w/c/numeric/complex/catan) |
|  sinh  | [`<inh>`](https://zh.cppreference.com/w/c/numeric/math/sinh) | [`<in>`](https://zh.cppreference.com/w/c/numeric/math/sinh) | [`<inh>`](https://zh.cppreference.com/w/c/numeric/math/sinh) | [`<sinh>`](https://zh.cppreference.com/w/c/numeric/complex/csinh) | [`<sin>`](https://zh.cppreference.com/w/c/numeric/complex/csinh) | [`<sinh>`](https://zh.cppreference.com/w/c/numeric/complex/csinh) |
|  cosh  | [`<osh>`](https://zh.cppreference.com/w/c/numeric/math/cosh) | [`<os>`](https://zh.cppreference.com/w/c/numeric/math/cosh) | [`<osh>`](https://zh.cppreference.com/w/c/numeric/math/cosh) | [`<cosh>`](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | [`<cos>`](https://zh.cppreference.com/w/c/numeric/complex/ccosh) | [`<cosh>`](https://zh.cppreference.com/w/c/numeric/complex/ccosh) |
|  tanh  | [`<anh>`](https://zh.cppreference.com/w/c/numeric/math/tanh) | [`<an>`](https://zh.cppreference.com/w/c/numeric/math/tanh) | [`<anh>`](https://zh.cppreference.com/w/c/numeric/math/tanh) | [`<tanh>`](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | [`<tan>`](https://zh.cppreference.com/w/c/numeric/complex/ctanh) | [`<tanh>`](https://zh.cppreference.com/w/c/numeric/complex/ctanh) |
| asinh  | [`<sinh>`](https://zh.cppreference.com/w/c/numeric/math/asinh) | [`<sin>`](https://zh.cppreference.com/w/c/numeric/math/asinh) | [`<sinh>`](https://zh.cppreference.com/w/c/numeric/math/asinh) | [`<asinh>`](https://zh.cppreference.com/w/c/numeric/complex/casinh) | [`<asin>`](https://zh.cppreference.com/w/c/numeric/complex/casinh) | [`<asinh>`](https://zh.cppreference.com/w/c/numeric/complex/casinh) |
| acosh  | [`<cosh>`](https://zh.cppreference.com/w/c/numeric/math/acosh) | [`<cos>`](https://zh.cppreference.com/w/c/numeric/math/acosh) | [`<cosh>`](https://zh.cppreference.com/w/c/numeric/math/acosh) | [`<acosh>`](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | [`<acos>`](https://zh.cppreference.com/w/c/numeric/complex/cacosh) | [`<acosh>`](https://zh.cppreference.com/w/c/numeric/complex/cacosh) |
| atanh  | [`<tanh>`](https://zh.cppreference.com/w/c/numeric/math/atanh) | [`<tan>`](https://zh.cppreference.com/w/c/numeric/math/atanh) | [`<tanh>`](https://zh.cppreference.com/w/c/numeric/math/atanh) | [`<atanh>`](https://zh.cppreference.com/w/c/numeric/complex/catanh) | [`<atan>`](https://zh.cppreference.com/w/c/numeric/complex/catanh) | [`<atanh>`](https://zh.cppreference.com/w/c/numeric/complex/catanh) |

## 实数限定函数

​	对于所有无复数对应的函数，除 `modf` 外都存在泛型宏 `XXX`，它会调用实数函数变体的中的一种：

- float 变体 `XXXf`
- double 变体 `XXX`
- long double 变体 `XXXl`

​	以下列方式确定调用的函数：

- 若泛型形参的任一实参为 long double，则调用 long double 变体。否则，若泛型形参的任一实参是 double，则调用 double 变体。否则调用 float 变体。

|   泛型宏   |                         实数函数变体                         |                         实数函数变体                         |                         实数函数变体                         |
| :--------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|            |                            float                             |                            double                            |                         long double                          |
|   atan2    | [`<tan2>`](https://zh.cppreference.com/w/c/numeric/math/atan2) | [`<tan>`](https://zh.cppreference.com/w/c/numeric/math/atan2) | [`<tan2>`](https://zh.cppreference.com/w/c/numeric/math/atan2) |
|    cbrt    | [`<brt>`](https://zh.cppreference.com/w/c/numeric/math/cbrt) | [`<br>`](https://zh.cppreference.com/w/c/numeric/math/cbrt) | [`<brt>`](https://zh.cppreference.com/w/c/numeric/math/cbrt) |
|    ceil    | [`<eil>`](https://zh.cppreference.com/w/c/numeric/math/ceil) | [`<ei>`](https://zh.cppreference.com/w/c/numeric/math/ceil) | [`<eil>`](https://zh.cppreference.com/w/c/numeric/math/ceil) |
|  copysign  | [`<opysign>`](https://zh.cppreference.com/w/c/numeric/math/copysign) | [`<opysig>`](https://zh.cppreference.com/w/c/numeric/math/copysign) | [`<opysign>`](https://zh.cppreference.com/w/c/numeric/math/copysign) |
|    erf     | [`<rf>`](https://zh.cppreference.com/w/c/numeric/math/erf) | [`<r>`](https://zh.cppreference.com/w/c/numeric/math/erf)  | [`<rf>`](https://zh.cppreference.com/w/c/numeric/math/erf) |
|    erfc    | [`<rfc>`](https://zh.cppreference.com/w/c/numeric/math/erfc) | [`<rf>`](https://zh.cppreference.com/w/c/numeric/math/erfc) | [`<rfc>`](https://zh.cppreference.com/w/c/numeric/math/erfc) |
|    exp2    | [`<xp2>`](https://zh.cppreference.com/w/c/numeric/math/exp2) | [`<xp>`](https://zh.cppreference.com/w/c/numeric/math/exp2) | [`<xp2>`](https://zh.cppreference.com/w/c/numeric/math/exp2) |
|   expm1    | [`<xpm1>`](https://zh.cppreference.com/w/c/numeric/math/expm1) | [`<xpm>`](https://zh.cppreference.com/w/c/numeric/math/expm1) | [`<xpm1>`](https://zh.cppreference.com/w/c/numeric/math/expm1) |
|    fdim    | [`<dim>`](https://zh.cppreference.com/w/c/numeric/math/fdim) | [`<di>`](https://zh.cppreference.com/w/c/numeric/math/fdim) | [`<dim>`](https://zh.cppreference.com/w/c/numeric/math/fdim) |
|   floor    | [`<loor>`](https://zh.cppreference.com/w/c/numeric/math/floor) | [`<loo>`](https://zh.cppreference.com/w/c/numeric/math/floor) | [`<loor>`](https://zh.cppreference.com/w/c/numeric/math/floor) |
|    fma     | [`<ma>`](https://zh.cppreference.com/w/c/numeric/math/fma) | [`<m>`](https://zh.cppreference.com/w/c/numeric/math/fma)  | [`<ma>`](https://zh.cppreference.com/w/c/numeric/math/fma) |
|    fmax    | [`<max>`](https://zh.cppreference.com/w/c/numeric/math/fmax) | [`<ma>`](https://zh.cppreference.com/w/c/numeric/math/fmax) | [`<max>`](https://zh.cppreference.com/w/c/numeric/math/fmax) |
|    fmin    | [`<min>`](https://zh.cppreference.com/w/c/numeric/math/fmin) | [`<mi>`](https://zh.cppreference.com/w/c/numeric/math/fmin) | [`<min>`](https://zh.cppreference.com/w/c/numeric/math/fmin) |
|    fmod    | [`<mod>`](https://zh.cppreference.com/w/c/numeric/math/fmod) | [`<mo>`](https://zh.cppreference.com/w/c/numeric/math/fmod) | [`<mod>`](https://zh.cppreference.com/w/c/numeric/math/fmod) |
|   frexp    | [`<rexp>`](https://zh.cppreference.com/w/c/numeric/math/frexp) | [`<rex>`](https://zh.cppreference.com/w/c/numeric/math/frexp) | [`<rexp>`](https://zh.cppreference.com/w/c/numeric/math/frexp) |
|   hypot    | [`<ypot>`](https://zh.cppreference.com/w/c/numeric/math/hypot) | [`<ypo>`](https://zh.cppreference.com/w/c/numeric/math/hypot) | [`<ypot>`](https://zh.cppreference.com/w/c/numeric/math/hypot) |
|   ilogb    | [`<logb>`](https://zh.cppreference.com/w/c/numeric/math/ilogb) | [`<log>`](https://zh.cppreference.com/w/c/numeric/math/ilogb) | [`<logb>`](https://zh.cppreference.com/w/c/numeric/math/ilogb) |
|   ldexp    | [`<dexp>`](https://zh.cppreference.com/w/c/numeric/math/ldexp) | [`<dex>`](https://zh.cppreference.com/w/c/numeric/math/ldexp) | [`<dexp>`](https://zh.cppreference.com/w/c/numeric/math/ldexp) |
|   lgamma   | [`<gamma>`](https://zh.cppreference.com/w/c/numeric/math/lgamma) | [`<gamm>`](https://zh.cppreference.com/w/c/numeric/math/lgamma) | [`<gamma>`](https://zh.cppreference.com/w/c/numeric/math/lgamma) |
|   llrint   | [`<lrint>`](https://zh.cppreference.com/w/c/numeric/math/rint) | [`<lrin>`](https://zh.cppreference.com/w/c/numeric/math/rint) | [`<lrint>`](https://zh.cppreference.com/w/c/numeric/math/rint) |
|  llround   | [`<lround>`](https://zh.cppreference.com/w/c/numeric/math/round) | [`<lroun>`](https://zh.cppreference.com/w/c/numeric/math/round) | [`<lround>`](https://zh.cppreference.com/w/c/numeric/math/round) |
|   log10    | [`<og10>`](https://zh.cppreference.com/w/c/numeric/math/log10) | [`<og1>`](https://zh.cppreference.com/w/c/numeric/math/log10) | [`<og10>`](https://zh.cppreference.com/w/c/numeric/math/log10) |
|   log1p    | [`<og1p>`](https://zh.cppreference.com/w/c/numeric/math/log1p) | [`<og1>`](https://zh.cppreference.com/w/c/numeric/math/log1p) | [`<og1p>`](https://zh.cppreference.com/w/c/numeric/math/log1p) |
|    log2    | [`<og2>`](https://zh.cppreference.com/w/c/numeric/math/log2) | [`<og>`](https://zh.cppreference.com/w/c/numeric/math/log2) | [`<og2>`](https://zh.cppreference.com/w/c/numeric/math/log2) |
|    logb    | [`<ogb>`](https://zh.cppreference.com/w/c/numeric/math/logb) | [`<og>`](https://zh.cppreference.com/w/c/numeric/math/logb) | [`<ogb>`](https://zh.cppreference.com/w/c/numeric/math/logb) |
|   lrint    | [`<rint>`](https://zh.cppreference.com/w/c/numeric/math/rint) | [`<rin>`](https://zh.cppreference.com/w/c/numeric/math/rint) | [`<rint>`](https://zh.cppreference.com/w/c/numeric/math/rint) |
|   lround   | [`<round>`](https://zh.cppreference.com/w/c/numeric/math/round) | [`<roun>`](https://zh.cppreference.com/w/c/numeric/math/round) | [`<round>`](https://zh.cppreference.com/w/c/numeric/math/round) |
| nearbyint  | [`<earbyint>`](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | [`<earbyin>`](https://zh.cppreference.com/w/c/numeric/math/nearbyint) | [`<earbyint>`](https://zh.cppreference.com/w/c/numeric/math/nearbyint) |
| nextafter  | [`<extafter>`](https://zh.cppreference.com/w/c/numeric/math/nextafter) | [`<extafte>`](https://zh.cppreference.com/w/c/numeric/math/nextafter) | [`<extafter>`](https://zh.cppreference.com/w/c/numeric/math/nextafter) |
| nexttoward | [`<exttoward>`](https://zh.cppreference.com/w/c/numeric/math/nextafter) | [`<exttowar>`](https://zh.cppreference.com/w/c/numeric/math/nextafter) | [`<exttoward>`](https://zh.cppreference.com/w/c/numeric/math/nextafter) |
| remainder  | [`<emainder>`](https://zh.cppreference.com/w/c/numeric/math/remainder) | [`<emainde>`](https://zh.cppreference.com/w/c/numeric/math/remainder) | [`<emainder>`](https://zh.cppreference.com/w/c/numeric/math/remainder) |
|   remquo   | [`<emquo>`](https://zh.cppreference.com/w/c/numeric/math/remquo) | [`<emqu>`](https://zh.cppreference.com/w/c/numeric/math/remquo) | [`<emquo>`](https://zh.cppreference.com/w/c/numeric/math/remquo) |
|    rint    | [`<int>`](https://zh.cppreference.com/w/c/numeric/math/rint) | [`<in>`](https://zh.cppreference.com/w/c/numeric/math/rint) | [`<int>`](https://zh.cppreference.com/w/c/numeric/math/rint) |
|   round    | [`<ound>`](https://zh.cppreference.com/w/c/numeric/math/round) | [`<oun>`](https://zh.cppreference.com/w/c/numeric/math/round) | [`<ound>`](https://zh.cppreference.com/w/c/numeric/math/round) |
|  scalbln   | [`<calbln>`](https://zh.cppreference.com/w/c/numeric/math/scalbn) | [`<calbl>`](https://zh.cppreference.com/w/c/numeric/math/scalbn) | [`<calbln>`](https://zh.cppreference.com/w/c/numeric/math/scalbn) |
|   scalbn   | [`<calbn>`](https://zh.cppreference.com/w/c/numeric/math/scalbn) | [`<calb>`](https://zh.cppreference.com/w/c/numeric/math/scalbn) | [`<calbn>`](https://zh.cppreference.com/w/c/numeric/math/scalbn) |
|   tgamma   | [`<gamma>`](https://zh.cppreference.com/w/c/numeric/math/tgamma) | [`<gamm>`](https://zh.cppreference.com/w/c/numeric/math/tgamma) | [`<gamma>`](https://zh.cppreference.com/w/c/numeric/math/tgamma) |
|   trunc    | [`<runc>`](https://zh.cppreference.com/w/c/numeric/math/trunc) | [`<run>`](https://zh.cppreference.com/w/c/numeric/math/trunc) | [`<runc>`](https://zh.cppreference.com/w/c/numeric/math/trunc) |

## 复数限定函数

​	对于所有没有实数对应的复数函数，存在泛型宏 `cXXX`，它会调用复数函数的变体：

- float [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 变体 `cXXXf`
- double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 变体 `cXXX`
- long double [complex](http://zh.cppreference.com/w/c/numeric/complex/complex) 变体 `cXXXl`

​	调用的函数按以下方式决定：

- 若泛型形参的任一实参为实数、复数或虚数，则调用适当的复数函数。

| 泛型宏 |                         复数函数变体                         |                         复数函数变体                         |                         复数函数变体                         |
| :----: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        |                            float                             |                            double                            |                         long double                          |
|  carg  | [`<arg>`](https://zh.cppreference.com/w/c/numeric/complex/carg) | [`<ar>`](https://zh.cppreference.com/w/c/numeric/complex/carg) | [`<arg>`](https://zh.cppreference.com/w/c/numeric/complex/carg) |
|  conj  | [`<onj>`](https://zh.cppreference.com/w/c/numeric/complex/conj) | [`<on>`](https://zh.cppreference.com/w/c/numeric/complex/conj) | [`<onj>`](https://zh.cppreference.com/w/c/numeric/complex/conj) |
| creal  | [`<real>`](https://zh.cppreference.com/w/c/numeric/complex/creal) | [`<rea>`](https://zh.cppreference.com/w/c/numeric/complex/creal) | [`<real>`](https://zh.cppreference.com/w/c/numeric/complex/creal) |
| cimag  | [`<imag>`](https://zh.cppreference.com/w/c/numeric/complex/cimag) | [`<ima>`](https://zh.cppreference.com/w/c/numeric/complex/cimag) | [`<imag>`](https://zh.cppreference.com/w/c/numeric/complex/cimag) |
| cproj  | [`<proj>`](https://zh.cppreference.com/w/c/numeric/complex/cproj) | [`<pro>`](https://zh.cppreference.com/w/c/numeric/complex/cproj) | [`<proj>`](https://zh.cppreference.com/w/c/numeric/complex/cproj) |

## 示例



```c
#include <stdio.h>
#include <tgmath.h>
 
int main(void)
{
    int i = 2;
    printf("sqrt(2) = %f\n", sqrt(i)); // 实参类型为 int，调用 sqrt
 
    float f = 0.5;
    printf("sin(0.5f) = %f\n", sin(f)); // 实参类型为 float，调用 sinf
 
    float complex dc = 1 + 0.5*I;
    float complex z = sqrt(dc); // 实参类型为 float complex，调用 csqrtf
    printf("sqrt(1 + 0.5i) = %f+%fi\n",
           creal(z),  // 实参类型为 float complex，调用 crealf
           cimag(z)); // 实参类型为 float complex，调用 cimagf
}
```

​	输出：

```
sqrt(2) = 1.414214
sin(0.5f) = 0.479426
sqrt(1 + 0.5i) = 1.029086+0.242934i
```