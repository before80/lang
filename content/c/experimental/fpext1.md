+++
title = "浮点扩展部分 1 ：二进制浮点算术"
date = 2025-04-15T19:33:25+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/experimental/fpext1](https://zh.cppreference.com/w/c/experimental/fpext1)

| ![img](https://upload.cppreference.com/mwiki/images/3/31/Imbox_notice.png) | **并入 ISO C** 此页面上描述的已从 2019 年 3 月起并入主线 ISO C 标准；链接待定 (C23 起) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

​	C 浮点扩展 - 部分 1 ：二进制浮点算术， ISO/IEC TS 18661-1:2014 ，为 C 标准库定义下列新组件，它们为 ISO/IEC/IEEE 60559:2011 （ IEEE-754 的当前版本）所推荐。

| `__STDC_IEC_60559_BFP__`<br />                               | long 类型值为 `201ymmL` 的整数常量，，取代 `__STDC_IEC_559__` (宏常量) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `__STDC_IEC_60559_COMPLEX__`<br />                           | long 类型值为 `201ymmL` 的整数常量，取代 `__STDC_IEC_559_COMPLEX__` (宏常量) |
| 在标头 `<limits.h>` 定义                                     |                                                              |
| CHAR_WIDTH SCHAR_WIDTH UCHAR_WIDTH (FP 扩展1 TS)<br />SHRT_WIDTH USHRT_WIDTH (FP 扩展1 TS)<br />INT_WIDTH UINT_WIDTH<br />LONG_WIDTH ULONG_WIDTH<br />LLONG_WIDTH ULLONG_WIDTH<br /> | 对应类型的宽度，以位数表示 (宏常量)                          |
| 在标头 `<float.h>` 定义                                      |                                                              |
| [CR_DECIMAL_DIG (FP 扩展1 TS)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/CR_DECIMAL_DIG&action=edit&redlink=1) | 所有受支持二进制浮点类型和字符序列间的转换至多准确舍入到 CR_DECIMAL_DIG 位十进制有效数字（至少是 DECIMAL_DIG + 3 ） (宏常量) |
| 在标头 `<fenv.h>` 定义                                       |                                                              |
| femode_t (FP 扩展1 TS)<br />                                 | 实现支持的动态浮点控制模式的总集，包含动态舍入方向模式 (typedef) |
| FE_DFL_MODE (FP 扩展1 TS)<br />                              | 指向默认 femode_t 的指针 (宏常量)                            |
| FE_SNANS_ALWAYS_SIGNAL (FP 扩展1 TS)<br />                   | 若 sNaN 参数导致压制 gNaN 的函数，如 [hypot](https://zh.cppreference.com/w/c/numeric/math/hypot) 或 [fmax](https://zh.cppreference.com/w/c/numeric/math/fmax) ，引发 FE_INVALID 并返回 gNaN ，则定义此宏（为整数常量 1 ） (宏常量) |
| [fesetexcept (FP 扩展1 TS)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fesetexcept&action=edit&redlink=1) | 设置给定的浮点异常标志，并且不导致任何引发它们所产生的副效应 (函数) |
| [fetestexceptflag (FP 扩展1 TS)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fetestexceptflag&action=edit&redlink=1) | 测试给定的标志是否在保存的浮点异常标志表示中 (函数)          |
| [fegetmode (FP 扩展1 TS)<br />fesetmode (FP 扩展1 TS)<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fegetmode_fesetmode&action=edit&redlink=1) | 整体地获取和设置所有实现的动态浮点控制模式 (函数)            |
| 在标头 `<stdint.h>` 定义                                     |                                                              |
| INTn_WIDTH UINTn_WIDTH (FP 扩展1 TS)<br />INT_LEASTn_WIDTH UINT_LEASTn_WIDTH (FP 扩展1 TS)<br />INT_FASTn_WIDTH UINT_FASTn_WIDTH<br />INTPTR_WIDTH UINTPTR_WIDTH<br />INTMAX_WIDTH UINTMAX_WIDTH<br />PTRDIFF_WIDTH<br />SIG_ATOMIC_WIDTH<br />SIZE_WIDTH<br />WCHAR_WIDTH WINT_WIDTH<br /> | 对应类型的宽度，以位数表示 (宏常量)                          |
| 在标头 `<stdlib.h>` 定义                                     |                                                              |
| [strfromd (FP 扩展1 TS)<br />strfromf (FP 扩展1 TS)<br />strfroml<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/strfromf&action=edit&redlink=1) | 用指定的 snprintf 格式转换单个浮点值到字符串 (函数)          |
| 在标头 `<math.h>` 定义                                       |                                                              |
| FP_INT_UPWARD (FP 扩展1 TS)<br />FP_INT_DOWNWARD (FP 扩展1 TS)<br />FP_INT_TOWARDZERO<br />FP_INT_TONEARESTFROMZERO<br />FP_INT_TONEAREST<br /><br /> | 函数 ceil 、 floor 、 trunc 、 round ，及 roundeven 的舍入方向，适用于 fromfp 系列函数 (宏常量) |
| FP_LLOGB0 (FP 扩展1 TS)<br />                                | 若参数为零则 llogb 所返回的值 (宏常量)                       |
| FP_LLOGBNAN (FP 扩展1 TS)<br />                              | 若参数为 NaN 则 llogb 所返回的值 (宏常量)                    |
| [SNANF (FP 扩展1 TS)<br />SNAN (FP 扩展1 TS)<br />SNANL<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/SNAN&action=edit&redlink=1) | 各表示 float 、 double 、 long double 的引发信号的 NaN (宏常量) |
| FP_FAST_FADD FP_FAST_FADDL FP_FAST_DADDL (FP 扩展1 TS)<br />FP_FAST_FSUB FP_FAST_FSUBL FP_FAST_DSUBL (FP 扩展1 TS)<br />FP_FAST_FMUL FP_FAST_FMULL FP_FAST_DMULL<br />FP_FAST_FDIV FP_FAST_FDIVL FP_FAST_DDIVL<br />FP_FAST_FFMA FP_FAST_FFMAL FP_FAST_DFMAL<br />FP_FAST_FSQRT FP_FAST_FSQRTL FP_FAST_DSQRTL<br /> | 倘若定义，则指示对应的函数执行快于较大类型的等价函数后随到目标类型的转型 (宏常量) |
| iseqsig (FP 扩展1 TS)<br />                                  | (宏函数)                                                     |
| iscanonical (FP 扩展1 TS)<br />                              | 测试浮点值是否规范 (宏函数)                                  |
| issignaling (FP 扩展1 TS)<br />                              | 测试浮点值是否引发信号的 NaN (宏函数)                        |
| issubnormal (FP 扩展1 TS)<br />                              | 测试浮点值是否非正规 (宏函数)                                |
| iszero (FP 扩展1 TS)<br />                                   | 测试浮点值是否为零（正、符、无符号） (宏函数)                |
| [fromfp (FP 扩展1 TS)<br />fromfpf (FP 扩展1 TS)<br />fromfpl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fromfp&action=edit&redlink=1) | 用指定舍入方向舍入到有符号整数 (函数)                        |
| [ufromfp (FP 扩展1 TS)<br />ufromfpf (FP 扩展1 TS)<br />ufromfpl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/ufromfp&action=edit&redlink=1) | 用指定舍入方向舍入到无符号整数 (函数)                        |
| [fromfpx (FP 扩展1 TS)<br />fromfpxf (FP 扩展1 TS)<br />fromfpxl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fromfpx&action=edit&redlink=1) | 用指定舍入方向舍入到有符号整数，报告不准确性 (函数)          |
| [ufromfpx (FP 扩展1 TS)<br />ufromfpxf (FP 扩展1 TS)<br />ufromfpxl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/ufromfpx&action=edit&redlink=1) | 用指定舍入方向舍入到无符号整数，报告不准确性 (函数)          |
| [roundeven (FP 扩展1 TS)<br />roundevenf (FP 扩展1 TS)<br />roundevenl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/roundeven&action=edit&redlink=1) | 舍入到最近值，中间点情况下舍入到偶数 (函数)                  |
| [llogb (FP 扩展1 TS)<br />llogbf (FP 扩展1 TS)<br />llogbl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/llogb&action=edit&redlink=1) | 等价于 [logb](https://zh.cppreference.com/w/c/numeric/math/logb) ，除了返回类型是 long (函数) |
| [fmaxmag (FP 扩展1 TS)<br />fmaxmagf (FP 扩展1 TS)<br />fmaxmagl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fmaxmag&action=edit&redlink=1) | 返回拥有较大绝对值的参数的值 (函数)                          |
| [fminmag (FP 扩展1 TS)<br />fminmagf (FP 扩展1 TS)<br />fminmagl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fminmag&action=edit&redlink=1) | 返回拥有较小绝对值的参数的值 (函数)                          |
| [nextup (FP 扩展1 TS)<br />nextupf (FP 扩展1 TS)<br />nextupl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/nextup&action=edit&redlink=1) | 返回下个较大的可表示浮点值 (函数)                            |
| [nextdown (FP 扩展1 TS)<br />nextdownf (FP 扩展1 TS)<br />nextdownl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/nextdown&action=edit&redlink=1) | 返回下个较小的可表示浮点值 (函数)                            |
| [fadd (FP 扩展1 TS)<br />faddl (FP 扩展1 TS)<br />daddl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fadd&action=edit&redlink=1) | 如同以无限精度并只舍入一次到目标类型计算 x+y (函数)          |
| [fsub (FP 扩展1 TS)<br />fsubl (FP 扩展1 TS)<br />dsubl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fsub&action=edit&redlink=1) | 如同以无限精度并只舍入一次到目标类型计算 x-y (函数)          |
| [fmul (FP 扩展1 TS)<br />fmull (FP 扩展1 TS)<br />dmull<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fmul&action=edit&redlink=1) | 如同以无限精度并只舍入一次到目标类型计算 x*y (函数)          |
| [fdiv (FP 扩展1 TS)<br />fdivl (FP 扩展1 TS)<br />ddivl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fdiv&action=edit&redlink=1) | 如同以无限精度并只舍入一次到目标类型计算 x/y (函数)          |
| [ffma (FP 扩展1 TS)<br />ffmal (FP 扩展1 TS)<br />dfmal<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/ffma&action=edit&redlink=1) | 如同以无限精度并只舍入一次到目标类型计算 [fma](https://zh.cppreference.com/w/c/numeric/math/fma) (函数) |
| [fsqrt (FP 扩展1 TS)<br />fsqrtl (FP 扩展1 TS)<br />dsqrtl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/fsqrt&action=edit&redlink=1) | 如同以无限精度并只舍入一次到目标类型计算 [sqrt](https://zh.cppreference.com/w/c/numeric/math/sqrt) (函数) |
| [totalorder (FP 扩展1 TS)<br />totalorderf (FP 扩展1 TS)<br />totalorderl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/totalorder&action=edit&redlink=1) | 用 ISO 60559 全序关系排序二个浮点值 (函数)                   |
| [totalordermag (FP 扩展1 TS)<br />totalordermagf (FP 扩展1 TS)<br />totalordermagl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/totalordermag&action=edit&redlink=1) | 用 ISO 60559 全序关系排序二个浮点值 (函数)                   |
| [canonicalize (FP 扩展1 TS)<br />canonicalizef (FP 扩展1 TS)<br />canonicalizel<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/canonicalize&action=edit&redlink=1) | 获得给定浮点值的 ISO 60559 规范二进制编码 (函数)             |
| [getpayload (FP 扩展1 TS)<br />getpayloadf (FP 扩展1 TS)<br />getpayloadl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/getpayload&action=edit&redlink=1) | 从给定的 NaN 值提取出负载 (函数)                             |
| [setpayload (FP 扩展1 TS)<br />setpayloadf (FP 扩展1 TS)<br />setpayloadl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/setpayload&action=edit&redlink=1) | 以指定负载创建安静的 NaN (函数)                              |
| [setpayloadsig (FP 扩展1 TS)<br />setpayloadsigf (FP 扩展1 TS)<br />setpayloadsigl<br />](https://zh.cppreference.com/mwiki/index.php?title=c/experimental/fpext1/setpayloadsig&action=edit&redlink=1) | 以指定负载创建引发信号的 NaN (函数)                          |
| 在标头 `<tgmath.h>` 定义                                     |                                                              |
| roundeven (FP 扩展1 TS)<br />                                | roundeven 的泛型重载 (函数)                                  |
| llogb (FP 扩展1 TS)<br />                                    | llogb 的泛型重载 (函数)                                      |
| fmaxmag (FP 扩展1 TS)<br />                                  | fmaxmag 的泛型重载 (函数)                                    |
| fminmag (FP 扩展1 TS)<br />                                  | fminmag 的泛型重载 (函数)                                    |
| nextup (FP 扩展1 TS)<br />                                   | nextup 的泛型重载 (函数)                                     |
| nextdown (FP 扩展1 TS)<br />                                 | nextdown 的泛型重载 (函数)                                   |
| fromfp (FP 扩展1 TS)<br />                                   | fromfp 的泛型重载 (函数)                                     |
| ufromfp (FP 扩展1 TS)<br />                                  | ufromfp 的泛型重载 (函数)                                    |
| fromfpx (FP 扩展1 TS)<br />                                  | fromfpx 的泛型重载 (函数)                                    |
| ufromfpx (FP 扩展1 TS)<br />                                 | ufromfpx 的泛型重载 (函数)                                   |
| nextdown (FP 扩展1 TS)<br />                                 | nextdown 的泛型重载 (函数)                                   |
| totalorder (FP 扩展1 TS)<br />                               | totalorder 的泛型重载 (函数)                                 |
| totalordermag (FP 扩展1 TS)<br />                            | totalordermag 的泛型重载 (函数)                              |
| fadd (FP 扩展1 TS)<br />                                     | fadd 的泛型重载 (函数)                                       |
| dadd (FP 扩展1 TS)<br />                                     | dadd 的泛型重载 (函数)                                       |
| fsub (FP 扩展1 TS)<br />                                     | fsub 的泛型重载 (函数)                                       |
| dsub (FP 扩展1 TS)<br />                                     | dsub 的泛型重载 (函数)                                       |
| fmul (FP 扩展1 TS)<br />                                     | fmul 的泛型重载 (函数)                                       |
| dmul (FP 扩展1 TS)<br />                                     | dmul 的泛型重载 (函数)                                       |
| fdiv (FP 扩展1 TS)<br />                                     | fdiv 的泛型重载 (函数)                                       |
| ddiv (FP 扩展1 TS)<br />                                     | ddiv 的泛型重载 (函数)                                       |
| ffma (FP 扩展1 TS)<br />                                     | ffma 的泛型重载 (函数)                                       |
| dfma (FP 扩展1 TS)<br />                                     | dfma 的泛型重载 (函数)                                       |
| fsqrt (FP 扩展1 TS)<br />                                    | fsqrt 的泛型重载 (函数)                                      |
| dsqrt (FP 扩展1 TS)<br />                                    | dsqrt 的泛型重载 (函数)                                      |

## 注意

​	此技术规范弃用标准 C 宏 __STDC_IEC_559__ 及 __STDC_IEC_559_COMPLEX__ 。

​	仅若在包含对应头文件前定义宏 __STDC_WANT_IEC_60559_BFP_EXT__ ，才声明此扩展添加到 C 库的所有函数和宏。

​	在对标准库的添加以外， ISO/IEC TS 18661-1:2014 做了一些对语言核心的改动，值得注意的是将浮点控制分割为静态（由新的 #pragma STDC FENV_ROUND 控制）和动态（由 [fesetround](https://zh.cppreference.com/w/c/numeric/fenv/feround) 控制）。若设置了静态舍入模式，则大多数 math.h 的函数考虑静态舍入模式优先于动态舍入模式。

> 本节未完成 
>
> 原因：添加到 pragma 页面或在此完整描述 pragma ？