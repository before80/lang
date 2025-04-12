+++
title = "算术运算符"
date = 2025-04-12T20:56:55+08:00
weight = 180
type = "docs"
description = ""
isCJKLanguage = true
draft = false
math = true

+++

> 原文：[https://zh.cppreference.com/w/c/language/operator_arithmetic](https://zh.cppreference.com/w/c/language/operator_arithmetic)

​	算术运算符在其操作数上应用标准数学运算。

> 本节未完成 
>
> 原因：为这个和其他表格考虑更通用的，覆盖多个专题的 ToC

| 运算符 | 运算符名 |   示例   |       结果        |
| :----: | :------: | :------: | :---------------: |
|  `+`   |  一元加  |   `+a`   |   a 提升后的值    |
|  `-`   |  一元减  |   `-a`   |    a 的相反数     |
|  `+`   |   加法   | `a + b`  |      a 加 b       |
|  `-`   |   减法   | `a - b`  |    从 a 减去 b    |
|  `*`   |   乘法   | `a * b`  |    a 和 b 的积    |
|  `/`   |   除法   | `a / b`  |   a 除以 b 的商   |
|  `%`   |   余数   | `a % b`  |  a 除以 b 的余数  |
|  `~`   |  逐位非  |   `~a`   |    a 的逐位非     |
|  `&`   |  逐位与  | `a & b`  |  a 和 b 的逐位与  |
|  `|`   |  逐位或  | `a | b`  |  a 和 b 的逐位或  |
|  `^`   | 逐位异或 | `a ^ b`  | a 和 b 的逐位异或 |
|  `<<`  | 逐位左移 | `a << b` |    a 左移 b 位    |
|  `>>`  | 逐位右移 | `a >> b` |    a 右移 b 位    |

## 溢出

​	无符号整数算术始终进行 \\(modulo 2^n\\)，其中 n 是该特定整数中的位数。例如对于 `unsigned int`，加一到 [UINT_MAX](https://zh.cppreference.com/w/c/types/limits) 得到0，而从 0 减一得到 [UINT_MAX](https://zh.cppreference.com/w/c/types/limits)。

​	有符号整数算术运算溢出（结果不符合结果类型）时，行为未定义：可以按照表示（典型为补码）的规则回卷，可以在某些平台上或由于编译器选项（例如 gcc 和 clang 中的 `-ftrapv`）触发陷阱，或可以完全[被编译器优化掉](http://blog.llvm.org/2011/05/what-every-c-programmer-should-know_14.html)。

### 浮点数环境

​	若设置 [`#pragma STDC FENV_ACCESS`](https://zh.cppreference.com/w/c/preprocessor/impl) 为 `ON`，则所有浮点数算术运算符均遵循当前浮点数[舍入方向](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)并报告 [`math_errhandling`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling) 中指定的错误，除非它们是[静态初始化式](https://zh.cppreference.com/w/c/language/initialization)的一部分（该情况下不引发浮点数异常，而舍入模式为到最接近）。

### 浮点数缩略

​	除非设置 [`#pragma STDC FP_CONTRACT`](https://zh.cppreference.com/w/c/preprocessor/impl) 为 `OFF`，否则可能如同中间结果拥有无限范围和精度一般进行所有浮点数算术，这种优化省略掉了当准确按写法求值表达式时，会观察到的舍入误差和浮点数异常。例如，允许以单条融合乘加 CPU 指令实现 `(x*y) + z`，或把 `a = x*x*x*x`; 优化成 `tmp = x*x; a = tmp*tmp`。

​	与缩略无关，浮点数算术的中间结果可以拥有异于其类型所指定的范围和精度，见 [FLT_EVAL_METHOD](https://zh.cppreference.com/w/c/types/limits/FLT_EVAL_METHOD)。

## 一元算术

​	一元算术运算符表达式的形式为

| `+` *表达式* | (1)  |      |
| ------------ | ---- | ---- |
| `-` *表达式* | (2)  |      |

1) 一元加（提升）
2) 一元减（相反数）

| *表达式* | -    | 任意[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)的表达式 |
| -------- | ---- | ------------------------------------------------------------ |

​	一元加和一元减都首先在其操作数上应用[整数提升](https://zh.cppreference.com/w/c/language/conversion)，然后

- 一元加返回提升后的值
- 一元减返回提升后值的相反数（除了 NaN 的相反数是另一 NaN）

表达式类型为提升后的类型，而[值类别](https://zh.cppreference.com/w/c/language/value_category)为非左值。

### 注意

​	在典型（补码）平台上应用到 [INT_MIN](https://zh.cppreference.com/w/c/types/limits)、[LONG_MIN](https://zh.cppreference.com/w/c/types/limits) 或 [LLONG_MIN](https://zh.cppreference.com/w/c/types/limits) 时，一元减引起有符号整数溢出所致的未定义行为。

​	C++ 中一元运算符 `+` 亦能用于其他内建类型，例如数组和函数，但 C 中不能。

```c
#include <stdio.h>
#include <complex.h>
#include <limits.h>
 
int main(void)
{
    char c = 'a';
    printf("sizeof char: %zu sizeof int: %zu\n", sizeof c, sizeof +c);
 
    printf("-1, where 1 is signed: %d\n", -1);
 
    // 有定义行为，由于是在无符号整数上实施算术
    // 从而，其计算为 (-1) 模 (2 的 n 次方) = UINT_MAX，其中 n 为
    // unsigned int 中的位数。若 unsigned int 有 32 位宽，则
    // 得到 (-1) 模 (2 的 32 次方) = 4294967295
    printf("-1, where 1 is unsigned: %u\n", -1u); 
 
    // 未定义行为，由于数学值为 -INT_MIN = INT_MAX + 1
    // （即比 signed int 的最大可能值大 1）
    //
    // printf("%d\n", -INT_MIN);
 
    // 未定义行为，由于数学值为 -LONG_MIN = LONG_MAX + 1
    // （即比 signed long 的最大可能值大 1）
    //
    // printf("%ld\n", -LONG_MIN);
 
    // 未定义行为，由于数学值为 -LLONG_MIN = LLONG_MAX + 1
    // （即比 signed long long 的最大可能值大 1）
    //
    // printf("%lld\n", -LLONG_MIN);
 
    double complex z = 1 + 2*I;
    printf("-(1+2i) = %.1f%+.1f\n", creal(-z), cimag(-z));
}
```

​	可能的输出：

```txt
sizeof char: 1 sizeof int: 4
-1, where 1 is signed: -1
-1, where 1 is unsigned: 4294967295
-(1+2i) = -1.0-2.0
```

## 加法性运算符

​	加法性算术运算符的形式为

| *lhs* `+` *rhs* | (1)  |      |
| --------------- | ---- | ---- |
| *lhs* `-` *rhs* | (2)  |      |

1) 加法：*lhs* 与 *rhs* 必须为下列之一：
   - 都拥有[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)，包含复数和虚数
   - 一个是指向完整对象的指针类型，另一个拥有整数类型
2) 减法：*lhs* 与 *rhs* 必须为下列之一：
   - 都拥有[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)，包含复数和虚数
   - *lhs* 拥有指向完整对象的指针类型，*rhs* 拥有整数类型
   - 都是指向拥有[兼容](https://zh.cppreference.com/w/c/language/types#.E5.85.BC.E5.AE.B9.E7.B1.BB.E5.9E.8B)类型的完整对象指针，忽略限定符



### 算术加法与减法

​	若两个操作数都拥有[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)，则

- 首先，进行[一般算术转换](https://zh.cppreference.com/w/c/language/conversion#.E4.B8.80.E8.88.AC.E7.AE.97.E6.9C.AF.E8.BD.AC.E6.8D.A2)
- 然后，遵循一般数学规则，对操作数提升后的值进行加或减（对于减法，从 *lhs* 减去 *rhs*），但
  - 若操作数之一为 `NaN`，则结果为 `NaN`
  - 无穷大减无穷大为 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
  - 正无穷大加负无穷大为 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)



​	复数和虚数加减法定义如下（注意若两个操作数均为虚数则结果类型为虚数，而若一个操作数为实数而另一为虚数，则结果为复数，同一般算术转换所指定）：

| + 或 - |       u        |       iv       |        u + iv        |
| :----: | :------------: | :------------: | :------------------: |
|   x    |    `x ± u`     |    `x ± iv`    |    `(x ± u) ± iv`    |
|   iy   |   `±u + iy`    |   `i(y ± v)`   |   `±u + i(y ± v)`    |
| x + iy | `(x ± u) + iy` | `x + i(y ± v)` | `(x ± u) + i(y ± v)` |

```txt
// 工作中
// 注意：采用 c/language/conversion 示例的一部分
```

### 指针算术

- 若指针 `P` 指向下标为 `I` 的数组元素，则
  - `P+N` 与 `N+P` 是指向同一数组中下标为 `I+N` 的元素的指针
  - `P-N` 是指向同一数组中下标为 `I-N` 的元素的指针



​	仅若原指针和结果指针都指向同一数组中的元素，或该数组的尾后一位置，行为才有定义。注意在 p 指向数组首元素时，执行 p-1 是未定义行为，并且在某些平台上可能失败。

- 若指针 `P1` 指向下标为 `I` 的数组元素（或尾后一位置）而 `P2` 是指向同一数组的下标为 `J` 的元素（或尾后一位置），则
  - `P1-P2` 拥有等于 `I-J` 的值和 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 类型（有符号整数类型，最大大小典型地为能声明的最大对象的一半）

​	仅当结果适合于 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t) 时，行为才有定义。

​	为指针算术的目的，把指向非数组元素的对象的指针当做指向大小为 1 的数组首元素的指针。

```c
// 工作中
int n = 4, m = 3;
int a[n][m];     // 4 个 VLA 的 VLA，每个有 3 个 int
int (*p)[m] = a; // p == &a[0] 
p = p + 1;       // p == &a[1]（VLA 所用的指针算术一如平常）
(*p)[2] = 99;    // 更改 a[1][2]
```

## 乘法性运算符

​	乘法性运算符的形式为

| *lhs* `*` *rhs* | (1)  |      |
| --------------- | ---- | ---- |
| *lhs* `/` *rhs* | (2)  |      |
| *lhs* `%` *rhs* | (3)  |      |

1) 乘法。*lhs* 与 *rhs* 必须拥有[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)
2) 除法。*lhs* 与 *rhs* 必须拥有[算术类型](https://zh.cppreference.com/w/c/language/arithmetic_types)
3) 余数。*lhs* 与 *rhs* 必须拥有[整数类型](https://zh.cppreference.com/w/c/language/arithmetic_types)

- 首先，进行[一般算术转换](https://zh.cppreference.com/w/c/language/conversion#.E4.B8.80.E8.88.AC.E7.AE.97.E6.9C.AF.E8.BD.AC.E6.8D.A2)。然后……

### 乘法

​	二元运算符 `*` 遵循一般的算术定义，进行其操作数（在一般算术提升后）的乘法，但

- 若操作数之一为 `NaN` ，则结果为 `NaN`
- 无穷大乘零给出 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- 无穷大乘非零给出无穷大（即使对于复参数）

​	因为 C 中，任何带至少一个无穷大部分的[复数值](https://zh.cppreference.com/w/c/language/arithmetic_types)为无穷大，即使另一部分为 `NaN`，故一般算术规则不适用于复复乘法。其他浮点数操作数的组合遵循下表：

|   *    |      u       |      iv       |    u + iv     |
| :----: | :----------: | :-----------: | :-----------: |
|   x    |      xu      |     i(xv)     | (xu) + i(xv)  |
|   iy   |    i(yu)     |      −yv      | (−yv) + i(yu) |
| x + iy | (xu) + i(yu) | (−yv) + i(xv) |  *特殊规则*   |

​	在无穷大处理外，不允许复数乘法上溢中间结果，但在设置 [`#pragma STDC CX_LIMITED_RANGE`](https://zh.cppreference.com/w/c/preprocessor/impl) 为 `ON` 时，该情况下可以如同 `(x+iy)×(u+iv) = (xu-yv)+i(yu+xv)` 一般计算值，因为假定了程序员负责限制操作数的范围并处理无穷大。

​	虽然不允许过度的上溢，复数乘法仍可能引发虚假的浮点数异常（否则实现不上溢版本困难到近乎不可能）。

```c
#include<stdio.h>
#include <stdio.h>
#include <complex.h>
#include <math.h>
int main(void)
{
 
 
// TODO 从 C++ 采取一些更简单的情况
 
 
   double complex z = (1 + 0*I) * (INFINITY + I*INFINITY);
// 教科书公式会给出
// (1+i0)(∞+i∞) ⇒ (1×∞ – 0×∞) + i(0×∞+1×∞) ⇒ NaN + I*NaN
// 但 C 给出复无穷大
   printf("%f + i*%f\n", creal(z), cimag(z));
 
// 教科书公式会给出
// cexp(∞+iNaN) ⇒ exp(∞)×(cis(NaN)) ⇒ NaN + I*NaN
// 但 C 给出 ±∞+i*nan
   double complex y = cexp(INFINITY + I*NAN);
   printf("%f + i*%f\n", creal(y), cimag(y));
 
}
```

​	可能的输出：

```txt
inf + i*inf 
inf + i*nan
```

### 除法

​	二元运算符 `/` 遵循一般的算术定义，将第一操作数除以第二操作数（在一般算术转换后），但

- 一般算术提升后的类型为整数类型时，结果为代数商（非分数），以实现定义方向取整(C99 前)向零截断(C99 起)
- 若操作数之一为 `NaN`，则结果为 `NaN`
- 若第一操作数为复无穷大，而第二操作数为有限，则 `/` 运算符的结果为复无穷大
- 若第一操作数为有限而第二操作数为复无穷大，则 `/` 运算符的结果为零

​	因为 C 中，任何带至少一个无穷大部分的[复数值](https://zh.cppreference.com/w/c/language/arithmetic_types)为无穷大，即使另一部分为 NaN ，故一般算术规则不适用于复复除法。其他浮点数操作数的组合遵循下表：

|   /    |       u        |       iv        |
| :----: | :------------: | :-------------: |
|   x    |      x/u       |     i(−x/v)     |
|   iy   |     i(y/u)     |       y/v       |
| x + iy | (x/u) + i(y/u) | (y/v) + i(−x/v) |

​	在无穷大处理外，不允许复数除法上溢中间结果，除了在设置 [`#pragma STDC CX_LIMITED_RANGE`](https://zh.cppreference.com/w/c/preprocessor/impl) 为 `ON` 时，该情况下可以如同 \\((x+iy) \over (u+iv)\\)   = \\([(xu+yv)+i(yu-xv)] \ over (u2+v2)\\) 一般计算值，因为假定了程序员负责限制操作数的范围并处理无穷大。

​	尽管不允许过度的上溢，但复数除法仍可能引发虚假的浮点数异常（否则实现不上溢版本困难到近乎不可能）。

​	若第二操作数为零，则行为未定义，但若支持 IEEE 浮点数算术，且发生浮点数除法，则

- 非零数除以 `±0.0` 给出符号正确的无穷大并引发 [FE_DIVBYZERO](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)
- `0.0` 除以 `0.0` 给出 `NaN` 并引发 [FE_INVALID](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

### 余数

​	二元运算符 `%` 产出第一操作数除以第二操作数（在一般算术转换后）的余数。

​	余数的符号定义，使得若商 `a/b` 能以结果类型表示，则 `(a/b)*b + a%b == a`。

​	若第二操作数为零，则行为未定义。

​	若商 `a/b` 不能以结果类型表示，则 `a/b` 和 `a%b` 的行为都未定义（这表明 INT_MIN%-1 在补码系统上未定义）。

> 注意
>
> ​	余数运算符不可用于浮点数类型上，库函数 [fmod](https://zh.cppreference.com/w/c/numeric/math/fmod) 提供该功能。

## 逐位逻辑

​	逐位逻辑运算符的形式为

| `~` *rhs*       | (1)  |      |
| --------------- | ---- | ---- |
| *lhs* `&` *rhs* | (2)  |      |
| *lhs* `|` *rhs* | (3)  |      |
| *lhs* `^` *rhs* | (4)  |      |

1) 逐位非
2) 逐位与
3) 逐位或
4) 逐位异或

​	其中

| *lhs*, *rhs* | -    | 整数类型的表达式 |
| ------------ | ---- | ---------------- |

​	首先，运算符 `&`、`^` 和 `|` 在两个操作数上进行[一般算术转换](https://zh.cppreference.com/w/c/language/conversion#.E4.B8.80.E8.88.AC.E7.AE.97.E6.9C.AF.E8.BD.AC.E6.8D.A2)，而运算符 ~ 在其唯一的操作数上进行[整数提升](https://zh.cppreference.com/w/c/language/conversion#.E6.95.B4.E6.95.B0.E6.8F.90.E5.8D.87)。

​	然后，逐位实施对应的逻辑运算符；即按照应用到操作数的每位的逻辑运算（或、与、非、异或），设置或清除结果的对应位。

> 注意
>
> ​	逐位运算符常用于操作位集和位掩码。

> 注意
>
> ​	对于无符号类型（提升后），表达式 ~E 等价于结果类型的最大可表示值减 E 的原值。

```c
#include <stdio.h>
#include <stdint.h>
 
int main(void)
{
    uint32_t a = 0x12345678;
    uint16_t mask = 0x00f0;
 
    printf("Promoted mask:\t%#010x\n"
           "Value:\t\t%#x\n"
           "Setting bits:\t%#x\n"
           "Clearing bits:\t%#x\n"
           "Selecting bits:\t%#010x\n"
           , mask
           , a
           , a | mask
           , a & ~mask
           , a & mask
    );
}
```

可能的输出：

```txt
Promoted mask:  0x000000f0
Value:          0x12345678
Setting bits:   0x123456f8
Clearing bits:  0x12345608
Selecting bits: 0x00000070
```

## 位移运算符

​	位移运算符表达式的形式为：

| *lhs* `<<` *rhs* | (1)  |      |
| ---------------- | ---- | ---- |
| *lhs* `>>` *rhs* | (2)  |      |

1) *lhs* 左移 *rhs* 位
2) *lhs* 右移 *rhs* 位

​	其中

| *lhs*, *rhs* | -    | 整数类型的表达式 |
| ------------ | ---- | ---------------- |

​	首先，在每个操作数上独自进行[整数提升](https://zh.cppreference.com/w/c/language/conversion)（注意：这不同于其他二元算术运算符，它们全都进行一般算术转换）。结果类型为 *lhs* 在提升后的类型。

​	若 *rhs* 为负或大于或等于提升后的 *lhs* 中的位数，则行为未定义。

​	对于无符号 *lhs*，`LHS << RHS` 的值是 \\(LHS * 2^{RHS}\\) 以返回类型最大值加 1 取模（即进行逐位左移，并舍弃移出目标类型的位）。对于有非负值的有符号 *lhs*，若值能以 *lhs* 的提升后类型表示，则 `LHS << RHS` 的值是  \\(LHS  * 2^{RHS}\\)，否则行为未定义。

​	对于无符号 *lhs* 和有非负值的有符号 *lhs*，`LHS >> RHS` 的值是  \\(LHS \over 2^{RHS}\\) 的整数部分。对于负的 `LHS`，`LHS >> RHS` 的值是实现定义的，大多数实现中，这进行算术右移（故结果仍为负）。从而在大多数实现中，右移有符号的 `LHS` 会以原符号位填充新的高位（即若原数非负则为 0，而若原数为负则为 1）。

```c
#include <stdio.h>
enum {ONE=1, TWO=2};
int main(void)
{
    char c = 0x10;
    unsigned long long ulong_num = 0x123;
    printf("0x123 << 1  = %#llx\n"
           "0x123 << 63 = %#llx\n"   // 对无符号数，溢出截断高位
           "0x10  << 10 = %#x\n",    // char 被提升到 int
           ulong_num << 1, ulong_num << 63, c << 10);
    long long long_num = -1000;
    printf("-1000 >> 1 = %lld\n", long_num >> ONE);  // 实现定义
}
```

​	可能的输出：

```txt
0x123 << 1  = 0x246
0x123 << 63 = 0x8000000000000000
0x10  << 10 = 0x4000
-1000 >> 1 = -500
```

## 参阅

算术运算符的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/operator_arithmetic)