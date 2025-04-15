+++
title = "fpext4"
date = 2025-04-15T19:36:10+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false
math = true

+++

> 原文[https://zh.cppreference.com/w/c/experimental/fpext4](https://zh.cppreference.com/w/c/experimental/fpext4)

​	C 浮点扩展 - 部分 4 ：补充函数， ISO/IEC TS 18661-4:2015 ，为 C 标准库定义下列新组件，它们为 ISO/IEC/IEEE 60559:2011 （ IEEE-754 的当前版本）所推荐

​	以下所列的补充数学函数已并入 C2x 标准。

## 预定义功能特性测试宏

| `__STDC_IEC_60559_FUNCS__`<br /> | 拥有 `long` 类型和值 `201506L` 的整数常量 (宏常量) |
| ---------------------------------- | -------------------------------------------------- |

## 补充数学函数

| 在标头 `<math.h>` 定义                                       |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exp2m1 exp2m1f exp2m1l (FP 扩展4 TS)<br />exp2m1fN exp2m1fNx (FP 扩展4 TS)<br />exp2m1dN exp2m1dNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/exp2m1&action=edit&redlink=1) | 计算 \\(2^x  - 1\\) (函数)                                   |
| [exp10 exp10f exp10l (FP 扩展4 TS)<br />exp10fN exp10fNx (FP 扩展4 TS)<br />exp10dN exp10dNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/exp10&action=edit&redlink=1) | 计算 \\(10^x \\) (函数)                                      |
| [exp10m1 exp10m1f exp10m1l (FP 扩展4 TS)<br />exp10m1fN exp10m1fNx (FP 扩展4 TS)<br />exp10m1dN exp10m1dNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/exp10m1&action=edit&redlink=1) | 计算  \\(10^x - 1 \\) (函数)                                 |
| [logp1 logp1f logp1l (FP 扩展4 TS)<br />logp1fN logp1fNx (FP 扩展4 TS)<br />logp1dN logp1dNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/logp1&action=edit&redlink=1) | 计算 \\(ln(1+x)\\)  （与 [log1p](https://zh.cppreference.com/w/c/numeric/math/log1p) 相同） (函数) |
| [log2p1 log2p1f log2p1l (FP 扩展4 TS)<br />log2p1fN log2p1fNx (FP 扩展4 TS)<br />log2p1dN log2p1dNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/log2p1&action=edit&redlink=1) | 计算  \\(log_2^{(1+x)}\\)  (函数)                            |
| [log10p1 log10p1f log10p1l (FP 扩展4 TS)<br />log10p1fN log10p1fNx (FP 扩展4 TS)<br />log10p1dN log10p1dNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/log10p1&action=edit&redlink=1) | 计算\\(log_10^{(1+x)}\\)   (函数)                            |
| [rsqrt rsqrtf rsqrtl (FP 扩展4 TS)<br />rsqrtfN rsqrtfNx (FP 扩展4 TS)<br />rsqrtdN rsqrtdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/rsqrt&action=edit&redlink=1) | 计算平方根倒数\\(x^{-1 \over 2}\\)(函数)                     |
| [compoundn compoundnf compoundnl (FP 扩展4 TS)<br />compoundnfN compoundnfNx (FP 扩展4 TS)<br />compoundndN compoundndNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/compoundn&action=edit&redlink=1) | 计算复利 \\((1+x)^n\\)   (函数)                              |
| [rootn rootnf rootnl (FP 扩展4 TS)<br />rootnfN rootnfNx (FP 扩展4 TS)<br />rootndN rootndNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/rootn&action=edit&redlink=1) | 计算 x 的 n 次方根\\(x^{1 \over n} \\)    (函数)             |
| [pown pownf pownl (FP 扩展4 TS)<br />pownfN pownfNx (FP 扩展4 TS)<br />powndN powndNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/pown&action=edit&redlink=1) | 计算 x 的 n 次幂，其中 n 为整数 (函数)                       |
| [powr powrf powrl (FP 扩展4 TS)<br />powrfN powrfNx (FP 扩展4 TS)<br />powrdN powrdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/powr&action=edit&redlink=1) | 计算 x 的 y 次幂\\(x^y \\)   (函数)                          |
| [acospi acospif acospil (FP 扩展4 TS)<br />acospifN acospifNx (FP 扩展4 TS)<br />acospidN acospidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/acospi&action=edit&redlink=1) | 计算\\(\arccos(x) \over π\\)    （以半圆周为单位度量角） (函数) |
| [asinpi asinpif asinpil (FP 扩展4 TS)<br />asinpifN asinpifNx (FP 扩展4 TS)<br />asinpidN asinpidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/asinpi&action=edit&redlink=1) | 计算 \\(arcsin(x) \over π\\)   （以半圆周为单位度量角） (函数) |
| [atanpi atanpif atanpil (FP 扩展4 TS)<br />atanpifN atanpifNx (FP 扩展4 TS)<br />atanpidN atanpidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/atanpi&action=edit&redlink=1) | 计算 \\(\ arctan(x) \over π \\) （以半圆周为单位度量角） (函数) |
| [atan2pi atan2pif atan2pil (FP 扩展4 TS)<br />atan2pifN atan2pifNx (FP 扩展4 TS)<br />atan2pidN atan2pidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/atan2pi&action=edit&redlink=1) | 计算 \\(\arctan(y/x) \over  π\\)   （以半圆周为单位度量角） (函数) |
| [cospi cospif cospil (FP 扩展4 TS)<br />cospifN cospifNx (FP 扩展4 TS)<br />cospidN cospidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/cospi&action=edit&redlink=1) | 计算 \\(\cos(πx)\\)   （以半圆周为单位度量角） (函数)        |
| [sinpi sinpif sinpil (FP 扩展4 TS)<br />sinpifN sinpifNx (FP 扩展4 TS)<br />sinpidN sinpidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/sinpi&action=edit&redlink=1) | 计算\\(sin(πx) \\)  （以半圆周为单位度量角） (函数)          |
| [tanpi tanpif tanpil (FP 扩展4 TS)<br />tanpifN tanpifNx (FP 扩展4 TS)<br />tanpidN tanpidNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/tanpi&action=edit&redlink=1) | 计算\\(\tan{(πx)}\\)   （以半圆周为单位度量角） (函数)       |

##### 缩减函数

| 在标头 `<math.h>` 定义                                     |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [reduc_sum reduc_sumf reduc_suml (FP 扩展4 TS)<br />reduc_sumfN reduc_sumfNx (FP 扩展4 TS)<br />reduc_sumdN reduc_sumdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/reduc_sum&action=edit&redlink=1) | 计算数组的 n 个元素之和 (函数)                               |
| [reduc_sumabs reduc_sumabsf reduc_sumabsl (FP 扩展4 TS)<br />reduc_sumabsfN reduc_sumabsfNx (FP 扩展4 TS)<br />reduc_sumabsdN reduc_sumabsdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/reduc_sumabs&action=edit&redlink=1) | 计算数组的 n 个元素绝对值之和 (函数)                         |
| [reduc_sumsq reduc_sumsqf reduc_sumsql (FP 扩展4 TS)<br />reduc_sumsqfN reduc_sumsqfNx (FP 扩展4 TS)<br />reduc_sumsqdN reduc_sumsqdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/reduc_sumsq&action=edit&redlink=1) | 计算数组的 n 个元素的平方和 (函数)                           |
| [reduc_sumprod reduc_sumprodf reduc_sumprodl (FP 扩展4 TS)<br />reduc_sumprodfN reduc_sumprodfNx (FP 扩展4 TS)<br />reduc_sumproddN reduc_sumproddNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/reduc_sumprod&action=edit&redlink=1) | 计算两个数组各自 n 个元素之间的点积 (函数)                   |
| [scaled_prod scaled_prodf scaled_prodl (FP 扩展4 TS)<br />scaled_prodfN scaled_prodfNx (FP 扩展4 TS)<br />scaled_proddN scaled_proddNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/scaled_prod&action=edit&redlink=1) | 计算数组 n 个元素的积，结果为有效数位值和缩放系数 (函数)     |
| [scaled_prodsum scaled_prodsumf scaled_prodsuml (FP 扩展4 TS)<br />scaled_prodsumfN scaled_prodsumfNx (FP 扩展4 TS)<br />scaled_prodsumdN scaled_prodsumdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/scaled_prodsum&action=edit&redlink=1) | 计算二个数组 n 对元素逐对和的积，结果为有效数位值和缩放系数 (函数) |
| [scaled_proddiff scaled_proddifff scaled_proddiffl (FP 扩展4 TS)<br />scaled_proddifffN scaled_proddifffNx (FP 扩展4 TS)<br />scaled_proddiffdN scaled_proddiffdNx<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext4/scaled_proddiff&action=edit&redlink=1) | 计算二个数组 n 对元素逐对差的积，结果为有效数位值和缩放系数 (函数) |

##### 各函数的准确舍入版本

| 在标头 `<math.h>` 定义                |                                                              |
| --------------------------------------- | ------------------------------------------------------------ |
| crexp(可选) (FP 扩展4 TS)<br />       | [exp](https://zh.cppreference.com/w/c/numeric/math/exp) 的准确舍入版本 (函数) |
| crexpm1(可选) (FP 扩展4 TS)<br />     | [expm1](https://zh.cppreference.com/w/c/numeric/math/expm1) 的准确舍入版本 (函数) |
| crexp2(可选) (FP 扩展4 TS)<br />      | [exp2](https://zh.cppreference.com/w/c/numeric/math/exp2) 的准确舍入版本 (函数) |
| crexp2m1(可选) (FP 扩展4 TS)<br />    | exp2m1 的准确舍入版本 (函数)                                 |
| crexp10(可选) (FP 扩展4 TS)<br />     | exp10 的准确舍入版本 (函数)                                  |
| crexp10m1(可选) (FP 扩展4 TS)<br />   | exp10m1 的准确舍入版本 (函数)                                |
| crlog(可选) (FP 扩展4 TS)<br />       | [log](https://zh.cppreference.com/w/c/numeric/math/log) 的准确舍入版本 (函数) |
| crlog2(可选) (FP 扩展4 TS)<br />      | log2 的准确舍入版本 (函数)                                   |
| crlog10(可选) (FP 扩展4 TS)<br />     | [log10](https://zh.cppreference.com/w/c/numeric/math/log10) 的准确舍入版本 (函数) |
| crlog1p(可选) (FP 扩展4 TS)<br />     | [log1p](https://zh.cppreference.com/w/c/numeric/math/log1p) 的准确舍入版本 (函数) |
| crlogp1(可选) (FP 扩展4 TS)<br />     | logp1 的准确舍入版本 (函数)                                  |
| crlog2p1(可选) (FP 扩展4 TS)<br />    | log2p1 的准确舍入版本 (函数)                                 |
| crlog10p1(可选) (FP 扩展4 TS)<br />   | log10p1 的准确舍入版本 (函数)                                |
| crrsqrt(可选) (FP 扩展4 TS)<br />     | rsqrt 的准确舍入版本 (函数)                                  |
| crcompoundn(可选) (FP 扩展4 TS)<br /> | compoundn 的准确舍入版本 (函数)                              |
| crrootn(可选) (FP 扩展4 TS)<br />     | rootn 的准确舍入版本 (函数)                                  |
| crpown(可选) (FP 扩展4 TS)<br />      | pown 的准确舍入版本 (函数)                                   |
| crpow(可选) (FP 扩展4 TS)<br />       | [pow](https://zh.cppreference.com/w/c/numeric/math/pow) 的准确舍入版本 (函数) |
| crpowr(可选) (FP 扩展4 TS)<br />      | powr 的准确舍入版本 (函数)                                   |
| crsin(可选) (FP 扩展4 TS)<br />       | [sin](https://zh.cppreference.com/w/c/numeric/math/sin) 的准确舍入版本 (函数) |
| crcos(可选) (FP 扩展4 TS)<br />       | [cos](https://zh.cppreference.com/w/c/numeric/math/cos) 的准确舍入版本 (函数) |
| crtan(可选) (FP 扩展4 TS)<br />       | [tan](https://zh.cppreference.com/w/c/numeric/math/tan) 的准确舍入版本 (函数) |
| crsinpi(可选) (FP 扩展4 TS)<br />     | sinpi 的准确舍入版本 (函数)                                  |
| crcospi(可选) (FP 扩展4 TS)<br />     | cospi 的准确舍入版本 (函数)                                  |
| crtanpi(可选) (FP 扩展4 TS)<br />     | tanpi 的准确舍入版本 (函数)                                  |
| crasinpi(可选) (FP 扩展4 TS)<br />    | asinpi 的准确舍入版本 (函数)                                 |
| cracospi(可选) (FP 扩展4 TS)<br />    | acospi 的准确舍入版本 (函数)                                 |
| cracospi(可选) (FP 扩展4 TS)<br />    | acospi 的准确舍入版本 (函数)                                 |
| cratanpi(可选) (FP 扩展4 TS)<br />    | atanpi 的准确舍入版本 (函数)                                 |
| cratan2pi(可选) (FP 扩展4 TS)<br />   | atan2pi 的准确舍入版本 (函数)                                |
| crasin(可选) (FP 扩展4 TS)<br />      | [asin](https://zh.cppreference.com/w/c/numeric/math/asin) 的准确舍入版本 (函数) |
| cracos(可选) (FP 扩展4 TS)<br />      | [acos](https://zh.cppreference.com/w/c/numeric/math/acos) 的准确舍入版本 (函数) |
| cratan(可选) (FP 扩展4 TS)<br />      | [atan](https://zh.cppreference.com/w/c/numeric/math/atan) 的准确舍入版本 (函数) |
| cratan2(可选) (FP 扩展4 TS)<br />     | [atan2](https://zh.cppreference.com/w/c/numeric/math/atan2) 的准确舍入版本 (函数) |
| crsinh(可选) (FP 扩展4 TS)<br />      | [sinh](https://zh.cppreference.com/w/c/numeric/math/sinh) 的准确舍入版本 (函数) |
| crcosh(可选) (FP 扩展4 TS)<br />      | [cosh](https://zh.cppreference.com/w/c/numeric/math/cosh) 的准确舍入版本 (函数) |
| crtanh(可选) (FP 扩展4 TS)<br />      | [tanh](https://zh.cppreference.com/w/c/numeric/math/tanh) 的准确舍入版本 (函数) |
| crasinh(可选) (FP 扩展4 TS)<br />     | [asinh](https://zh.cppreference.com/w/c/numeric/math/asinh) 的准确舍入版本 (函数) |
| cracosh(可选) (FP 扩展4 TS)<br />     | [acosh](https://zh.cppreference.com/w/c/numeric/math/acosh) 的准确舍入版本 (函数) |
| cratanh(可选) (FP 扩展4 TS)<br />     | [atanh](https://zh.cppreference.com/w/c/numeric/math/atanh) 的准确舍入版本 (函数) |
| crhypot(可选) (FP 扩展4 TS)<br />     | [hypot](https://zh.cppreference.com/w/c/numeric/math/hypot) 的准确舍入版本 (函数) |

##### 各函数的复数版本

| 在标头 `<complex.h>` 定义             |                             |
| --------------------------------------- | --------------------------- |
| cexp2m1(可选) (FP 扩展4 TS)<br />     | exp2m1 的复数版本 (函数)    |
| cexp10(可选) (FP 扩展4 TS)<br />      | exp10 的复数版本 (函数)     |
| cexp10m1(可选) (FP 扩展4 TS)<br />    | exp10m1 的复数版本 (函数)   |
| clogp1(可选) (FP 扩展4 TS)<br />      | logp1 的复数版本 (函数)     |
| clog2p1(可选) (FP 扩展4 TS)<br />     | log2p1 的复数版本 (函数)    |
| clog10p1(可选) (FP 扩展4 TS)<br />    | log10p1 的复数版本 (函数)   |
| crsqrt (可选) (FP 扩展4 TS)<br />     | rsqrt 的复数版本 (函数)     |
| ccompoundn (可选) (FP 扩展4 TS)<br /> | compoundn 的复数版本 (函数) |
| crootn(可选) (FP 扩展4 TS)<br />      | rootn 的复数版本 (函数)     |
| cpown (可选) (FP 扩展4 TS)<br />      | pown 的复数版本 (函数)      |
| cpowr(可选) (FP 扩展4 TS)<br />       | powr 的复数版本 (函数)      |
| cacospi(可选) (FP 扩展4 TS)<br />     | acospi 的复数版本 (函数)    |
| casinpi(可选) (FP 扩展4 TS)<br />     | asinpi 的复数版本 (函数)    |
| catanpi(可选) (FP 扩展4 TS)<br />     | atanpi 的复数版本 (函数)    |
| ccospi(可选) (FP 扩展4 TS)<br />      | cospi 的复数版本 (函数)     |
| csinpi(可选) (FP 扩展4 TS)<br />      | sinpi 的复数版本 (函数)     |
| ctanpi(可选) (FP 扩展4 TS)<br />      | tanpi 的复数版本 (函数)     |

## 注意

​	仅若在包含 math.h 前定义宏 `__STDC_WANT_IEC_60559_FUNCS_EXT__` ，才声明此扩展添加到 C 库的所有函数。

​	仅若在包含 math.h 前定义宏 `__STDC_WANT_IEC_60559_DFP_EXT__` ，才定义每个函数的十进制浮点变体。

​	仅若在包含 math.h 前定义宏 `__STDC_WANT_IEC_60559_TYPES_EXT__` ，才定义每个函数的扩展精度变体。

​	所有函数的准确舍入版本（带 `cr-` 前缀者）都是可选的。