+++
title = "浮点数常量"
date = 2025-04-12T20:00:46+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false
math = true

+++

> 原文：[https://zh.cppreference.com/w/c/language/floating_constant](https://zh.cppreference.com/w/c/language/floating_constant)

​	允许直接在表达式中使用浮点数类型的值。

## 语法

​	浮点数常量是[非左值](https://zh.cppreference.com/w/c/language/value_category)表达式，拥有下列形式：

*有效数字* *指数* ﻿(可选) *后缀* ﻿(可选)	

​	其中 *有效数字* 拥有形式：

*整数部分* ﻿(可选) `.`(可选) *小数部分* ﻿(可选)

​	*指数* 拥有形式：

​	`e` | `E` *指数符号* ﻿(可选) *数字序列*  (1)

​	`p` | `P` *指数符号* ﻿(可选) *数字序列* (2)  (C99 起)

1) 十进制浮点数常量的指数语法
2) 十六进制浮点数常量的指数语法

​	数位间可插入作为分隔符的单引号（`'`），在编译时忽略它们。(C23 起)

## 解释

​	若 *有效数字* 以字符序列 `0x` 或 `0X` 开始，则浮点数常量为*十六进制浮点数常量*。否则，它是*十进制浮点数常量*。对于*十六进制浮点数常量*，将 *有效数字* 转译为十六进制小数，而将指数的 *数字序列* 转译为有效数字要乘的 2 的整数次幂。(C99 起)

```c
double d = 0x1.2p3; // 十六进制小数 1.2（十进制 1.125）乘 2^3，即 9.0
```

​	对于*十进制浮点数常量*， *有效数字* 被转译为十进制小数，而将指数的 *数字序列* 转译为有效数字要乘的 10 的整数次幂。

```c
double d = 1.2e3; // 十进制小数 1.2 乘 10^3，即 1200.0
```

### 后缀

​	无后缀浮点数常量拥有 double 类型。若 *后缀* 为字母 `f` 或 `F`，则浮点数常量拥有 float 类型。若 *后缀* 为 `l` 或 `L`，则浮点数常量拥有 long double 类型。

​	若实现预定义宏 `__STDC_IEC_60559_BFP__`，则额外支持下列后缀与对应的浮点数常量：(C23 起)

- 若 *后缀* 为 `df` 或 `DF`，则浮点数常量拥有 `_Decimal32` 类型；
- 若 *后缀* 为 `dd` 或 `DD`，则浮点数常量拥有 `_Decimal64` 类型；
- 若 *后缀* 为 `dl` 或 `DL`，则浮点数常量拥有 `_Decimal128` 类型。

​	十六进制浮点数常量中不允许十进制浮点数类型的后缀。(C23 起)

### 可选部分

​	若有指数而不用小数部分，则可以忽略小数分隔符：

```c
double x = 1e0; // 浮点数 1.0 （不用小数点）
```

​	对于十进制浮点数常量，*指数* 部分是可选的。若忽略它，则小数点不是可选的，而且 *整数部分* 或 *小数部分* 必须存在。

```c
double x = 1.; // 浮点数 1.0（小数部分可选）
double y = .1; // 浮点数 0.1（整数部分可选）
```

​	十六进制浮点数常量的指数非可选，以避免误认 `f` 后缀为十六进制数字所导致的歧义结果。(C99 起)

### 可表示值

​	浮点数常量的求值结果是最邻近的可表示值，或紧邻于最邻近可表示值的最大或最小可表示值，以实现定义方式选择（换言之，翻译期的[默认浮点数方向](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)是实现定义的）。

​	所有拥有相同源码形式的浮点数常量都转换到有相同值的同一内部格式。有不同形式的浮点数常量，例如 `1.23` 与 `1.230`，不需要转换到同一内部格式和值。

​	若 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD) 指示，可以转换浮点数常量为大于其所指示类型的范围和精度。例如，常量 `0.1f` 可能在表达式中表现为 `0.1L`。若 [FLT_RADIX](https://zh.cppreference.com/w/c/types/limits) 为 2，则十六进制浮点数常量的求值结果，是浮点数常量所表示的正确舍入到目标类型的准确值。(C99 起)

​	拥有相同数值 `x`，但有不同量指数的十进制浮点数类型的浮点数常量，例如 `1230.dd`、 `1230.0dd` 及 `1.23e3dd`，拥有可区别的内部表示。十进制浮点数类型的浮点数常量的量指数 `q` 在可能时，以 \\(10^q\\) 表示位于 *有效数字* 最低位的位置的 1 的方式确定。若按以上方式确定的量指数 `q` 与系数 \\(c = x⋅10^{−q} \\)不能以浮点数常量的类型准确表示，则在类型的界限内按需增加 `q` ，并对应地减少 `c` ，进行需要的舍入。舍入可能导致零或无穷大。若在 `q` 抵达最大值后（可能为舍入后的） `c` 仍在容许范围外，则产生的浮点数常量拥有正无穷大值。(C23 起)

## 注解

​	默认[舍入方向](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)和[精度](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)在浮点数常量转换成内部表示时有效，而且不会引发[浮点数异常](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，即使 [`#pragma STDC FENV_ACCESS`](https://zh.cppreference.com/w/c/preprocessor/impl) 生效（对于字符串的执行时转换，可使用 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof)）。注意它和浮点数类型的[算术常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)有别。

​	浮点数常量中的字母是无关大小写的，除了在十进制浮点数类型的后缀中不能一同使用大写和小写(C23 起)： `0x1.ep+3` 与 `0X1.EP+3` 表示同一浮点数 `15.0`。

​	[setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 中指定的小数点对浮点数常量语法无效：小数点始终是点。

​	不同于整数，不是每个浮点数都能以十进制或十六进制(C99 起)常量语法表示：宏 [`NAN`](https://zh.cppreference.com/w/c/numeric/math/NAN) 和 [`INFINITY`](https://zh.cppreference.com/w/c/numeric/math/INFINITY) 以及如 [nan](https://zh.cppreference.com/w/c/numeric/math/nan) 的函数提供生成这些特殊值的方式(C99 起)。注意 `0x1.FFFFFEp128f`，可能作为 IEEE float NaN 出现，实际上它在该格式中溢出到无穷大。

​	没有负浮点数常量；如 `-1.2` 的表达式被视为[算术运算符](https://zh.cppreference.com/w/c/language/operator_arithmetic)一元负作用于浮点数常量 `1.2` 。注意可通过 `-0.0` 构造特殊值负零。

## 示例

```c
#include <stdio.h>
 
int main(void)
{
    printf("15.0     = %a\n", 15.0);
    printf("0x1.ep+3 = %f\n", 0x1.ep+3);
 
    // 超出 double 范围的常量。
    printf("+2.0e+308 --> %g\n",  2.0e+308);
    printf("+1.0e-324 --> %g\n",  1.0e-324);
    printf("-1.0e-324 --> %g\n", -1.0e-324);
    printf("-2.0e+308 --> %g\n", -2.0e+308);
}
```

​	输出：

```txt
15.0     = 0x1.ep+3
0x1.ep+3 = 15.000000
+2.0e+308 --> inf
+1.0e-324 --> 0
-1.0e-324 --> -0
-2.0e+308 --> -inf
```

## 参阅

**浮点数字面量**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/floating_literal)**