+++
title = "整数常量"
date = 2025-04-12T19:48:58+08:00
weight = 70
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/integer_constant](https://zh.cppreference.com/w/c/language/integer_constant)

​	允许整数类型的值直接用于表达式。

## 语法

​	整数常量是拥有下列类型的[非左值]({{< ref "/c/language/expressions/value_category" >}})表达式

| *十进制常量* *整数后缀* ﻿(可选)   | (1)  |          |
| -------------------------------- | ---- | -------- |
| *八进制常量* *整数后缀* ﻿(可选)   | (2)  |          |
| *十六进制常量* *整数后缀* ﻿(可选) | (3)  |          |
| *二进制常量* *整数后缀* ﻿(可选)   | (4)  | (C23 起) |

​	其中

- *十进制常量* 是非零十进制数字（`1`、`2`、`3`、`4`、`5`、`6`、`7`、`8`、`9`），跟随零个或更多十进制数字（`0`、`1`、`2`、`3`、`4`、`5`、`6`、`7`、`8`、`9`）

- *八进制常量* 是数字零（`0`）跟随零个或更多八进制数字（`0`、`1`、`2`、`3`、`4`、`5`、`6`、`7`）

- *十六进制常量* 是字符序列 `0x` 或字符序列 `0X` 跟随一个或更多十六进制数字（`0`、`1`、`2`、`3`、`4`、`5`、`6`、`7`、`8`、`9`、`a`、`A`、`b`、`B`、`c`、`C`、`d`、`D`、`e`、`E`、`f`、`F`）

- *二进制常量* 是字符序列 `0b` 或字符序列 `0B` 跟随一个或更多二进制数字（`0`、`1`）

- *整数后缀*，若提供，则可为下列之一（不过无符号后缀可以和其他后缀之一组合；如果使用两个后缀，则它们可以任何顺序出现：

  - *无符号后缀*（字符 `u` 或字符 `U`）
  - *长后缀*（字符 `l` 或字符 `L`）或 *长长后缀*（字符序列 `ll` 或 `LL`）(C99 起)
  - *位精确整数后缀*（字符序列 `wb` 或字符序列 `WB`） (C23 起)

  

​	数位间可插入作为分隔符的可选的单引号（`'`）。编译器会忽略它们。(C23 起)

## 解释

1) 十进制整数常量（以 10 为底，首位为最高位）。
2) 八进制整数常量（以 8 为底，首位为最高位）。
3) 十六进制整数常量（以 16 为底，首位为最高位，字母 `a` 到 `f` 表示十进制值 10 到 15）。
4) 二进制整数常量（以 2 为底，首位为最高位）。

​	下列对象被初始化为相同值：

```c
int d = 42;
int o = 052;
int x = 0x2a;
int X = 0X2A;
int b = 0b101010; // C23
```

​	下列对象也被初始化为相同值：

```c
unsigned long long l1 = 18446744073709550592ull; // C99
unsigned long long l2 = 18'446'744'073'709'550'592llu; // C23
unsigned long long l3 = 1844'6744'0737'0955'0592uLL; // C23
unsigned long long l4 = 184467'440737'0'95505'92LLU; // C23
```

### 整数常量的类型

​	整数常量类型是从依赖数字底和所用 *整数后缀* 的类型列表中，值所能吻合的首个类型。

|         后缀         |                           十进制底                           |                            其他底                            |
| :------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: |
|        无后缀        | `int`<br />`long int` <br />unsigned long int (C99 前) <br />`long long int` (C99 起) | `int`<br />`unsigned int` <br />`long int` <br />`unsigned long int` <br />`long long int`(C99 起) <br />`unsigned long long int`(C99 起) |
|      `u` 或 `U`      | `unsigned int`<br />`unsigned long int`<br /> `unsigned long long int`(C99 起) | `unsigned int`<br />`unsigned long int` <br />`unsigned long long int`(C99 起) |
|      `l` 或 `L`      | `long int`<br />unsigned long int(C99 前) <br />`long long int`(C99 起) | `long int`<br />`unsigned long int`<br /> `long long int`(C99 起) <br />`unsigned long long int`(C99 起) |
|  `l`/`L` 与 `u`/`U`  |  `unsigned long int`<br />`unsigned long long int`(C99 起)   |  `unsigned long int`<br />`unsigned long long int`(C99 起)   |
|     `ll` 或 `LL`     |                   `long long int`(C99 起)                    | `long long int`(C99 起)<br />`unsigned long long int`(C99 起) |
| `ll`/`LL` 与 `u`/`U` |               `unsigned long long int`(C99 起)               |               `unsigned long long int`(C99 起)               |
|     `wb` 或 `WB`     | `_BitInt(N)` 其中位宽 N 为大于 1 且可容纳值和符号位的最小的 N (C23 起) | `_BitInt(N)` 其中位宽 N 为大于 1 且可容纳值和符号位的最小的 N (C23 起) |
| `wb`/`WB` 和 `u`/`U` | `unsigned _BitInt(N)` 其中位宽 N 为大于 1 且可容纳值位的最小的 N (C23 起) | `unsigned _BitInt(N)` 其中位宽 N 为大于 1 且可容纳值位的最小的 N (C23 起) |

​	若整数常量过大从而无法符合后缀/底结合所允许的任何类型，它没有 `wb`、`WB`、`uwb` 或 `UWB` 后缀，(C23 起)且编译器支持扩展整数类型（譬如 `__int128` ），则常量可能以扩展整数类型给出；否则程序为谬构。

## 注解

​	整数常量中的字母无关大小写： `0xDeAdBaBeU` 和 `0XdeadBABEu` 表示同一个数（一个例外是 *long-long-suffix* ，必须是 `ll` 或 `LL` ，不能是 `lL` 或 `Ll` ）(C99 起)。

​	没有负整数常量。如 -1 的表达式是将[一元负运算符]({{< ref "/c/language/expressions/operator_arithmetic" >}})应用到常量所表示的值。

​	当用于 [`#if`]({{< ref "/c/language/preprocessor/conditional" >}}) 或 [`#elif`]({{< ref "/c/language/preprocessor/conditional" >}}) 的控制表达式时，所有有符号整数常量都表现为如同拥有 [intmax_t]({{< ref "/c/types/integer" >}}) 类型，且所有无符号整数常量都表现为如同有 [uintmax_t]({{< ref "/c/types/integer" >}}) 类型。(C99 起)

​	整数常量可用于[整数常量表达式]({{< ref "/c/language/expressions/constant_expression" >}})。

​	由于[最大吞噬](https://zh.cppreference.com/w/c/language/translation_phases#.E6.9C.80.E5.A4.A7.E5.90.9E.E5.99.AC)规则，以 `e` 和 `E` 结束的十六进制整数常量在后随运算符 `+` 或 `-` 时，源码中必须以空白符或括号将它们与运算符分隔：

```c
int x = 0xE+2;   // 错误
int y = 0xa+2;   // OK
int z = 0xE +2;  // OK
int q = (0xE)+2; // OK
```

​	否则形成一个非法的预处理数字记号，这会进一步导致分析失败。

## 示例

```c
#include <inttypes.h>
#include <stdio.h>
int main(void)
{
    printf("123 = %d\n", 123);
    printf("0123 = %d\n", 0123);
    printf("0x123 = %d\n", 0x123);
    printf("12345678901234567890ull = %llu\n", 12345678901234567890ull);
    // 类型为 64 位类型（ unsigned long long 或可能的 unsigned long ）
    // 即使无 long 后缀
    printf("12345678901234567890u = %"PRIu64"\n", 12345678901234567890u );
 
    // printf("%lld\n", -9223372036854775808); // 错误：
        // 值 9223372036854775808 不能适合 signed long long，
        // 它是无后缀十进制整数常量所允许的最大值
 
    printf("%llu\n", -9223372036854775808ull );
    // 应用到无符号值的一元减将它从 2^64 减去
    // 这给出无符号 9223372036854775808 
 
    printf("%lld\n", -9223372036854775807ll - 1);
    // 组成有符号值 -9223372036854775808 的正确方式
}
```

​	输出：

```txt
123 = 123
0123 = 83
0x123 = 291
12345678901234567890ull = 12345678901234567890
12345678901234567890u = 12345678901234567890
9223372036854775808
-9223372036854775808
```

## 参阅

**整数字面量**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/integer_literal)**
