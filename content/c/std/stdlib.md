
+++
title = "<stdlib.h>"
date = 2025-04-24T18:51:20+08:00
weight = 220
type = "docs"
description = "通用工具：内存管理、程序工具、字符串转换、随机数、算法"
isCJKLanguage = true
draft = false

+++

## 类型




## 枚举




## 宏



### EXIT_FAILURE

原址：[https://zh.cppreference.com/w/c/program/EXIT_status](https://zh.cppreference.com/w/c/program/EXIT_status)

作用：表示程序的执行结果  (宏常量)

备注：
```c
// 在标头 <stdlib.h> 定义
#define EXIT_SUCCESS /* 由实现定义 */
#define EXIT_FAILURE /* 由实现定义 */
```

​	`EXIT_SUCCESS` 和 `EXIT_FAILURE` 宏展开成能用作 [exit](https://zh.cppreference.com/w/c/program/exit) 的实参的整数常量表达式（从而作为从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)返回的值），并指示程序执行状态。

| 常量           | 说明         |
| -------------- | ------------ |
| `EXIT_SUCCESS` | 程序执行成功 |
| `EXIT_FAILURE` | 程序执行失败 |

**注解**

​	`EXIT_SUCCESS` 和值零都能指示程序执行成功的状态，尽管并不要求 `EXIT_SUCCESS` 等于零。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE* fp = fopen("data.txt","r");
    if (fp == NULL)
    {
       fprintf(stderr,"fopen() failed in file %s at line # %d", __FILE__, __LINE__);
       exit(EXIT_FAILURE);
    }
 
    /* 正常进程持续至此。 */
    fclose(fp);
    printf("Normal Return\n");
 
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
fopen() failed in file main.cpp at line # 9
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22/3 General utilities <stdlib.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22/3 General utilities <stdlib.h> （第 248 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22/3 General utilities <stdlib.h> （第 340 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20/3 General utilities <stdlib.h> （第 306 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10 General utilities <stdlib.h>

**参阅**

**EXIT_SUCCESS, EXIT_FAILURE** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/EXIT_status)**





### EXIT_SUCCESS

原址：[https://zh.cppreference.com/w/c/program/EXIT_status](https://zh.cppreference.com/w/c/program/EXIT_status)

作用：表示程序的执行结果  (宏常量)

备注：
```c
// 在标头 <stdlib.h> 定义
#define EXIT_SUCCESS /* 由实现定义 */
#define EXIT_FAILURE /* 由实现定义 */
```

​	`EXIT_SUCCESS` 和 `EXIT_FAILURE` 宏展开成能用作 [exit](https://zh.cppreference.com/w/c/program/exit) 的实参的整数常量表达式（从而作为从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)返回的值），并指示程序执行状态。

| 常量           | 说明         |
| -------------- | ------------ |
| `EXIT_SUCCESS` | 程序执行成功 |
| `EXIT_FAILURE` | 程序执行失败 |

**注解**

​	`EXIT_SUCCESS` 和值零都能指示程序执行成功的状态，尽管并不要求 `EXIT_SUCCESS` 等于零。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    FILE* fp = fopen("data.txt","r");
    if (fp == NULL)
    {
       fprintf(stderr,"fopen() failed in file %s at line # %d", __FILE__, __LINE__);
       exit(EXIT_FAILURE);
    }
 
    /* 正常进程持续至此。 */
    fclose(fp);
    printf("Normal Return\n");
 
    return EXIT_SUCCESS;
}
```

​	输出：

```txt
fopen() failed in file main.cpp at line # 9
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22/3 General utilities <stdlib.h> （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22/3 General utilities <stdlib.h> （第 248 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22/3 General utilities <stdlib.h> （第 340 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20/3 General utilities <stdlib.h> （第 306 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10 General utilities <stdlib.h>

**参阅**

**EXIT_SUCCESS, EXIT_FAILURE** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/EXIT_status)**





### __STDC_VERSION_STDLIB_H__

原址：

作用：

备注：






## 函数



### _Exit

原址：[https://zh.cppreference.com/w/c/program/_Exit](https://zh.cppreference.com/w/c/program/_Exit)

作用：引发正常的程序终止但不清理  (函数)

备注：
```c
// 在标头 <stdlib.h> 定义
void _Exit( int exit_code );// (C99 起) (C11 前)
_Noreturn void _Exit( int exit_code );// (C11 起) (C23 前)
[[noreturn]] void _Exit( int exit_code );// (C23 起)
```

​	导致发生程序正常终止，但不完全清理资源。

​	不调用传递给 [at_quick_exit()](https://zh.cppreference.com/w/c/program/at_quick_exit) 或 [atexit()](https://zh.cppreference.com/w/c/program/atexit) 的函数。是否将未写入数据冲入打开的流、关闭打开的流或移除临时文件是实现定义的。

​	若 `exit_code` 为 0 或 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status)，则将指示成功终止的状态返回给宿主环境。若 `exit_code` 为 [EXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示*不成功*终止的实现定义状态。其他情况下返回实现定义的状态值。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |
|           |      |                |

**返回值**

​	（无）

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
/* _Exit 不调用 atexit 所注册的函数。 */
void f1(void)
{
    puts("pushed first");
}
 
void f2(void)
{
    puts("pushed second");
}
 
int main(void)
{
    printf("Enter main()\n");
    atexit(f1);
    atexit(f2);
    fflush(stdout);   /* _Exit 可能不冲入未写入的缓冲数据 */
    _Exit(0);
}
```

​	输出：

```txt
Enter main()
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.4.5 The _Exit function （第 256 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.4.5 The _Exit function （第 352 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.4.4 The _Exit function （第 316 页）

**参阅**

| [abort<br />](https://zh.cppreference.com/w/c/program/abort) | 引发非正常的程序终止（不清理） (函数) |
| ------------------------------------------------------------ | ------------------------------------- |
| [exit<br />](https://zh.cppreference.com/w/c/program/exit) | 引发正常的程序终止并清理 (函数)       |
| **_Exit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/_Exit)** |                                       |





### abort

原址：[https://zh.cppreference.com/w/c/program/abort](https://zh.cppreference.com/w/c/program/abort)

作用：引发非正常的程序终止（不清理）  (函数)

备注：
```c
// 在标头 <stdlib.h> 定义
void abort(void);// (C11 前)
_Noreturn void abort(void);// (C11 起) (C23 前)
[[noreturn]] void abort(void);// (C23 起)
```

​	导致程序异常终止，除非传递给 [signal](https://zh.cppreference.com/w/c/program/signal) 的信号处理函数正在捕捉 [SIGABRT](https://zh.cppreference.com/w/c/program/SIG_types) 且该处理函数不返回。

​	不调用传递给 [atexit()](https://zh.cppreference.com/w/c/program/atexit) 的函数。是否关闭打开的资源，例如文件，是实现定义的。向宿主环境返回指示不成功执行的实现定义状态。

**参数**

​	（无）

**返回值**

​	（无）

**注解**

​	POSIX [指定](https://pubs.opengroup.org/onlinepubs/9699919799/functions/abort.html) `abort()` 函数撤除阻塞，或忽略 `SIGABRT` 信号。

​	某些编译器内建子程序，例如 [`__builtin_trap`](https://gcc.gnu.org/onlinedocs/gcc/Other-Builtins.html)（gcc、clang 及 icc）或 [`__fastfail`](https://learn.microsoft.com/en-us/cpp/intrinsics/fastfail)/[`__debugbreak`](https://learn.microsoft.com/en-us/cpp/intrinsics/debugbreak)（msvc），能用于尽可能快地终止程序。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void) 
{
    FILE *fp = fopen("data.txt","r");
    if (fp == NULL)
    {
        fprintf(stderr, "error opening file data.txt in function main()\n");
        abort();
    }
 
    /* 正常处理持续至此。 */
    fclose(fp);
    printf("Normal Return\n");
    return 0;
}
```

​	输出：

```txt
error opening file data.txt in function main()
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.4.1 The abort function （第 255 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.4.1 The abort function （第 350 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.4.1 The abort function （第 315 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.4.1 The abort function

**参阅**

| [exit<br />](https://zh.cppreference.com/w/c/program/exit) | 引发正常的程序终止并清理 (函数)                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [atexit<br />](https://zh.cppreference.com/w/c/program/atexit) | 注册一个要在调用 [`<xit(>`](https://zh.cppreference.com/w/c/program/exit) 时调用的函数 (函数) |
| [quick_exit (C11)<br />](https://zh.cppreference.com/w/c/program/quick_exit) | 引发正常的程序终止但不完全清理 (函数)                        |
| **abort** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/abort)** |                                                              |





### abort_handler_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### abs

原址：[http://zh.cppreference.com/w/c/numeric/math/abs](http://zh.cppreference.com/w/c/numeric/math/abs)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int        abs( int n );
long       labs( long n );
long long llabs( long long n );// (C99 起)
// 在标头 <inttypes.h> 定义
intmax_t imaxabs( intmax_t n );// (C99 起)
```

​	计算整数的绝对值。若返回类型无法表示结果，则行为未定义。

**参数**

| n    | -    | 整数值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	`n` 的绝对值（即 `|n|`），若它能被表示。

**注解**

​	在补码系统中，最小负值的绝对值处于对应整数范围外，例如对于 32 位补码类型 `int`，[INT_MIN](https://zh.cppreference.com/w/c/types/limits) 为 `-2147483648`，但其绝对值应有的结果是 `2147483648`，大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)（其值为 `2147483647`）。

**示例**

```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("abs(+3) = %d\n", abs(+3));
    printf("abs(-3) = %d\n", abs(-3));
 
//  printf("%+d\n", abs(INT_MIN)); // 在补码系统上是未定义行为
}
```

​	输出：

```txt
abs(+3) = 3
abs(-3) = 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.1 The imaxabs function （第 TBD 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.1 The imaxabs function （第 159 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 259 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.1 The imaxabs function （第 218 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 356 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.1 The imaxabs function （第 199-200 页）

  - 7.20.6.1 The abs, labs and llabs functions （第 320 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.6.1 The abs function

  - 4.10.6.3 The labs function

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)           |
| **abs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/abs)** |                                         |





### aligned_alloc

原址：

作用：

备注：





### at_quick_exit

原址：[https://zh.cppreference.com/w/c/program/at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit)

作用：注册要在调用 quick_exit 时调用的函数  (函数)

备注：
```c
// 在标头 <stdlib.h> 定义
int at_quick_exit( void (*func)(void) );// (C11 起)
```

​	注册 `func` 所指向的函数，使它在程序快速终止（通过 [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)）时得到调用。

​	`at_quick_exit` 是线程安全的：从多个线程调用此函数不会导入数据竞争。实现应当支持注册至少 `32` 个函数。确切的极限是由实现定义的。

​	所注册的函数在[程序正常终止](https://zh.cppreference.com/w/c/program/exit)时并不会被调用。如果需要函数在这种情况下被调用，必须使用 [atexit](https://zh.cppreference.com/w/c/program/atexit)。

**参数**

| func | -    | 指向要在程序快速终止调用的函数的指针 |
| ---- | ---- | ------------------------------------ |
|      |      |                                      |

**返回值**

​	若注册成功则为 `0`，否则为非零值。

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
void f1(void)
{
    puts("pushed first");
    fflush(stdout);
}
 
void f2(void)
{
    puts("pushed second");
}
 
int main(void)
{
    at_quick_exit(f1);
    at_quick_exit(f2);
    quick_exit(0);
}
```

​	输出：

```txt
pushed second
pushed first
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.4.3 The at_quick_exit function （第 255 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.4.3 The at_quick_exit function （第 351 页）

**参阅**

| [abort<br />](https://zh.cppreference.com/w/c/program/abort) | 引发非正常的程序终止（不清理） (函数)                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exit<br />](https://zh.cppreference.com/w/c/program/exit) | 引发正常的程序终止并清理 (函数)                              |
| [atexit<br />](https://zh.cppreference.com/w/c/program/atexit) | 注册一个要在调用 [`<xit(>`](https://zh.cppreference.com/w/c/program/exit) 时调用的函数 (函数) |
| [quick_exit (C11)<br />](https://zh.cppreference.com/w/c/program/quick_exit) | 引发正常的程序终止但不完全清理 (函数)                        |
| **at_quick_exit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/at_quick_exit)** |                                                              |





### atexit

原址：[https://zh.cppreference.com/w/c/program/atexit](https://zh.cppreference.com/w/c/program/atexit)

作用：注册一个要在调用 exit() 时调用的函数  (函数)

备注：
```c
// 在标头 <stdlib.h> 定义
int atexit( void (*func)(void) );
```

​	注册 `func` 所指向的函数，使它在程序正常终止（通过 [exit()](https://zh.cppreference.com/w/c/program/exit) 或从 `main()` 返回）时得到调用。将以注册顺序的逆序调用这些函数，即首先执行最后调用的函数。

​	可以注册同一函数多于一次。

​	实现保证支持注册至少 `32` 个函数。确切的极限是由实现定义的。

**参数**

| func | -    | 指向要在程序正常终止时调用的函数的指针 |
| ---- | ---- | -------------------------------------- |
|      |      |                                        |

**返回值**

​	若注册成功则为 `0`，否则为非零值。

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
void f1(void)
{
    puts("f1");
}
 
void f2(void)
{
    puts("f2");
}
 
int main(void)
{
    if ( ! atexit(f1) && ! atexit(f2) && ! atexit(f2) )
        return EXIT_SUCCESS ;
 
    // atexit registration failed
    return EXIT_FAILURE ;
 
}   // <- 若注册成功则会调用 f2, f2, f1
```

​	输出：

```txt
f2
f2
f1
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.4.2 The atexit function （第 255 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.4.2 The atexit function （第 350 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.4.2 The atexit function （第 315 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 7.10.4.2 The atexit function （第 156 页）

**参阅**

| [at_quick_exit (C11)<br />](https://zh.cppreference.com/w/c/program/at_quick_exit) | 注册要在调用 [`<uick_exi>`](https://zh.cppreference.com/w/c/program/quick_exit) 时调用的函数 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **atexit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/atexit)** |                                                              |





### atof

原址：[http://zh.cppreference.com/w/c/string/byte/atof](http://zh.cppreference.com/w/c/string/byte/atof)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
double atof( const char* str );
```

​	转译 `str` 所指向的字节字符串中的浮点数。

​	函数会舍弃任何空白符（由 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定），直至找到首个非空白符。然后它会取用尽可能多的字符，以构成合法的浮点数表示，并将它们转换成浮点值。合法的浮点值可以为下列之一：

- 十进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - 非空的十进制数字序列，可选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `e` 或 `E`，并跟随可选的正或负号，以及非空十进制数字序列（以 *10* 为底定义指数）



- 十六进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - `0x` 或 `0X`
  - 非空的十六进制数字序列，选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `p` 或 `P`，并跟随可选的正或负号，以及非空十进制数字序列（以 *2* 为底定义指数）

- 无穷大表达式。它由下列部分组成：

  - (可选) 正或负号
  - `INF` 或 `INFINITY`，忽略大小写

- 非数（NaN）表达式。它由下列部分组成：

  - (可选) 正或负号
  - `NAN` 或 `**NAN(**`*char_sequence* ﻿`**)**`，忽略 `NAN` 部分的大小写。 *char_sequence* 只能由数字、拉丁字母和下划线构成。结果是一个静态的 NaN 浮点值。

(C99 起)



- 任何其他可由当前 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)接受的表达式。

**参数**

| str  | -    | 指向待转译的空终止字符串的指针 |
| ---- | ---- | ------------------------------ |
|      |      |                                |

**返回值**

​	成功时返回对应于 `str` 内容的 `double` 的值。若转换的值在返回类型的范围外，则返回值未定义。若无可进行的转换，则返回 `0.0`。

**注解**

​	其名字含义为“ASCII to float”。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("%g\n", atof("  -0.0000000123junk"));
    printf("%g\n", atof("0.012"));
    printf("%g\n", atof("15e16"));
    printf("%g\n", atof("-0x1afp-2"));
    printf("%g\n", atof("inF"));
    printf("%g\n", atof("Nan"));
    printf("%g\n", atof("1.0e+309"));   // UB：超出 double 范围
    printf("%g\n", atof("0.0"));
    printf("%g\n", atof("junk"));       // 无可进行的转换
}
```

​	可能的输出：

```txt
-1.23e-08
0.012
1.5e+17
-107.75
inf
nan
inf
0
0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.1 The atof function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.1 The atof function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.1 The atof function （第 341 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.1 The atof function （第 307 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.1 The atof function

**参阅**

| [strtof (C99)<br />strtod (C99)<br />strtold <br />](https://zh.cppreference.com/w/c/string/byte/strtof) | 将字节字符串转换成浮点数 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| **atof** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/atof)** |                                 |





### atoi

原址：[http://zh.cppreference.com/w/c/string/byte/atoi](http://zh.cppreference.com/w/c/string/byte/atoi)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int       atoi ( const char* str );// (1)
long      atol ( const char* str );// (2)
long long atoll( const char* str );// (3)(C99 起)
```

​	转换 `str` 所指的字节字符串中的整数。隐含的基数总为 *10*。

​	舍弃任何空白符，直至找到首个非空白符，然后接收尽可能多的字符以组成合法的整数表示，并转换之为整数。合法的整数含下列部分：

- (可选) 正或负号
- 数位

​	如果结果的值无法被表示，即转换后的值落在对应返回类型之外，则其行为未定义。

**参数**

| str  | -    | 指向要转译的空终止字符串的指针 |
| ---- | ---- | ------------------------------ |
|      |      |                                |

**返回值**

​	成功时为对应于 `str` 的内容的整数。若转换的值落在对应的返回类型范围外，则返回值未定义。

​	若无法进行转换，则返回 `0`。

**注解**

​	其名字代表“ASCII to integer”。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("%i\n", atoi(" -123junk"));
    printf("%i\n", atoi(" +321dust"));
    printf("%i\n", atoi("0"));
    printf("%i\n", atoi("0042")); // 当做代用前导零的十进制数
    printf("%i\n", atoi("0x2A")); // 仅转换前导零，丢弃 "x2A"
    printf("%i\n", atoi("junk")); // 无可进行的转换
    printf("%i\n", atoi("2147483648")); // UB：在 int 范围外
}
```

​	可能的输出：

```txt
-123
321
0
42
0
0
-2147483648
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 249 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 341 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.2 The atoi, atol, and atoll functions （第 307 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.2 The atoi function

  - 4.10.1.3 The atol function

**参阅**

| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)       |
| ------------------------------------------------------------ | ----------------------------------- |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数) |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)           |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)     |
| **atoi, atol, atoll** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/atoi)** |                                     |





### atol

原址：[http://zh.cppreference.com/w/c/string/byte/atoi](http://zh.cppreference.com/w/c/string/byte/atoi)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int       atoi ( const char* str );// (1)
long      atol ( const char* str );// (2)
long long atoll( const char* str );// (3)(C99 起)
```

​	转换 `str` 所指的字节字符串中的整数。隐含的基数总为 *10*。

​	舍弃任何空白符，直至找到首个非空白符，然后接收尽可能多的字符以组成合法的整数表示，并转换之为整数。合法的整数含下列部分：

- (可选) 正或负号
- 数位

​	如果结果的值无法被表示，即转换后的值落在对应返回类型之外，则其行为未定义。

**参数**

| str  | -    | 指向要转译的空终止字符串的指针 |
| ---- | ---- | ------------------------------ |
|      |      |                                |

**返回值**

​	成功时为对应于 `str` 的内容的整数。若转换的值落在对应的返回类型范围外，则返回值未定义。

​	若无法进行转换，则返回 `0`。

**注解**

​	其名字代表“ASCII to integer”。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("%i\n", atoi(" -123junk"));
    printf("%i\n", atoi(" +321dust"));
    printf("%i\n", atoi("0"));
    printf("%i\n", atoi("0042")); // 当做代用前导零的十进制数
    printf("%i\n", atoi("0x2A")); // 仅转换前导零，丢弃 "x2A"
    printf("%i\n", atoi("junk")); // 无可进行的转换
    printf("%i\n", atoi("2147483648")); // UB：在 int 范围外
}
```

​	可能的输出：

```txt
-123
321
0
42
0
0
-2147483648
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 249 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 341 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.2 The atoi, atol, and atoll functions （第 307 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.2 The atoi function

  - 4.10.1.3 The atol function

**参阅**

| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)       |
| ------------------------------------------------------------ | ----------------------------------- |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数) |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)           |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)     |
| **atoi, atol, atoll** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/atoi)** |                                     |





### atoll

原址：[http://zh.cppreference.com/w/c/string/byte/atoi](http://zh.cppreference.com/w/c/string/byte/atoi)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int       atoi ( const char* str );// (1)
long      atol ( const char* str );// (2)
long long atoll( const char* str );// (3)(C99 起)
```

​	转换 `str` 所指的字节字符串中的整数。隐含的基数总为 *10*。

​	舍弃任何空白符，直至找到首个非空白符，然后接收尽可能多的字符以组成合法的整数表示，并转换之为整数。合法的整数含下列部分：

- (可选) 正或负号
- 数位

​	如果结果的值无法被表示，即转换后的值落在对应返回类型之外，则其行为未定义。

**参数**

| str  | -    | 指向要转译的空终止字符串的指针 |
| ---- | ---- | ------------------------------ |
|      |      |                                |

**返回值**

​	成功时为对应于 `str` 的内容的整数。若转换的值落在对应的返回类型范围外，则返回值未定义。

​	若无法进行转换，则返回 `0`。

**注解**

​	其名字代表“ASCII to integer”。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("%i\n", atoi(" -123junk"));
    printf("%i\n", atoi(" +321dust"));
    printf("%i\n", atoi("0"));
    printf("%i\n", atoi("0042")); // 当做代用前导零的十进制数
    printf("%i\n", atoi("0x2A")); // 仅转换前导零，丢弃 "x2A"
    printf("%i\n", atoi("junk")); // 无可进行的转换
    printf("%i\n", atoi("2147483648")); // UB：在 int 范围外
}
```

​	可能的输出：

```txt
-123
321
0
42
0
0
-2147483648
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 249 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.2 The atoi, atol, and atoll functions （第 341 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.2 The atoi, atol, and atoll functions （第 307 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.2 The atoi function

  - 4.10.1.3 The atol function

**参阅**

| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)       |
| ------------------------------------------------------------ | ----------------------------------- |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数) |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)           |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)     |
| **atoi, atol, atoll** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/atoi)** |                                     |





### bsearch

原址：[http://zh.cppreference.com/w/c/algorithm/bsearch](http://zh.cppreference.com/w/c/algorithm/bsearch)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void* bsearch( const void *key, const void *ptr, size_t count, size_t size,
               int (*comp)(const void*, const void*) );// (1)
void* bsearch_s( const void *key, const void *ptr, rsize_t count, rsize_t size,
                 int (*comp)(const void *, const void *, void *),

                 void *context );// (2)(C11 起)
/*QVoid*/* bsearch( const void *key, /*QVoid*/ *ptr, size_t count, size_t size,
                    int (*comp)(const void*, const void*) );// (3)(C23 起)
/*QVoid*/* bsearch_s( const void *key, /*QVoid*/ *ptr, rsize_t count, rsize_t size,
                      int (*comp)(const void *, const void *, void *),

                      void *context );// (4)(C23 起)
```

1） 在 `ptr` 所指向的数组中寻找等于 `key` 所指向的元素。该数组含 `count` 个大小为 `size` 字节的元素，并且已相对于 `key` 划分，也就是说，所有比较小于关键目标的元素必须出现于所有比较等于的元素之前，而且所有比较等于关键目标的元素要出现于所有比较大于关键目标的元素之前。完全排序的数组满足这些要求。用 `comp` 所指向的函数比较元素。若数组未依照与 `comp` 标准相同的相对于 `*key` 的升序划分，则行为未定义。

2） 同 (1) ，除了传递给 `comp` 额外状态参数 `context` ，并在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

  - `count` 或 `size` 大于 RSIZE_MAX
  - `key` 、 `ptr` 或 `comp` 是空指针（除非 `count` 为零）

3,4) 分别等价于 (1) 与 (2) 的泛型宏。令 `T` 为一个无限定的对象类型（包括 `void`）。

  - 若 `ptr` 类型为 `const T*` ，则返回类型为 `const void*` 。
  - 否则，若 `ptr` 类型为 `T*` ，则返回类型为 `void*` 。
  - 否则行为未定义。

若抑制这些泛型函数之一的宏定义以访问实际函数（例如使用 `(bsearch)`、 `(bsearch_s)` 或函数指针），则实际函数声明 (1) 或 (2) 变为可见。

​	若数组包含多个 `comp` 指示为与欲查找元素相等的元素，则结果返回的具体元素是未指定的。

​	直接使用实际函数 (1) 与 (2) 是被弃用的。 (C23 起)

**参数**

| key     | -    | 指向要查找的元素的指针                                       |
| ------- | ---- | ------------------------------------------------------------ |
| ptr     | -    | 指向要检验的数组的指针                                       |
| count   | -    | 数组的元素数目                                               |
| size    | -    | 数组每个元素的字节数                                         |
| comp    | -    | 比较函数。如果首个参数*小于* ﻿第二个，那么返回负整数值，如果首个参数*大于* ﻿第二个，那么返回正整数值，如果两个参数等价，那么返回零。 将 `key` 传给首个参数，数组中的元素传给第二个。 ​	比较函数的签名应等价于如下形式：​	`int cmp(const void *a, const void *b);`​	该函数必须不修改传递给它的对象，而且在调用比较相同对象时必须返回一致的结果，与它们在数组中的位置无关。​	 |
| context | -    | 比较器的状态（例如，对照序列），作为第三个参数传递给 `comp`  |

**返回值**

1） 指向与 `*key` 比较相等的指针，在找不到元素时返回空指针。

2） 同 (1) ，除了在运行时约束违规时也返回空指针。

3,4) 分别同 (1) 与 (2) ，除了 cv 限定得到调整。

**注解**

​	与名称无关， C 和 POSIX 标准都未要求此函数用二分查找实现，也未保证任何复杂度。

​	与其他检查边界的函数不同， `bsearch_s` 不将零大小数组视作运行时约束违规，而是指出找不到元素（另一个接受零大小数组的函数是 qsort_s ）。

​	在 `bsearch_s` 之前， `bsearch` 的用户通常用全局变量表示比较器的状态。

**示例**

```c
#include <stdlib.h>
#include <stdio.h>
 
struct data {
    int nr;
    char const *value;
} dat[] = {
    {1, "Foo"}, {2, "Bar"}, {3, "Hello"}, {4, "World"}
};
 
int data_cmp(void const *lhs, void const *rhs) 
{
    struct data const *const l = lhs;
    struct data const *const r = rhs;
 
    if (l->nr < r->nr) return -1;
    else if (l->nr > r->nr) return 1;
    else return 0;
 
    // return (l->nr > r->nr) - (l->nr < r->nr); // 可行的简洁写法
    // return l->nr - r->nr; // 错误的简洁写法（若给出 INT_MIN 就会失败）
}
 
int main(void) 
{
    struct data key = { .nr = 3 };
    struct data const *res = bsearch(&key, dat, sizeof dat / sizeof dat[0],
                                     sizeof dat[0], data_cmp);
    if (res) {
        printf("No %d: %s\n", res->nr, res->value);
    } else {
        printf("No %d not found\n", key.nr);
    }
}
```

​	输出：

```txt
No 3: Hello
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.5.1 The bsearch function （第 258 页）

  - K.3.6.3.1 The bsearch_s function （第 441-442 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.5.1 The bsearch function （第 355 页）

  - K.3.6.3.1 The bsearch_s function （第 608-609 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.5.1 The bsearch function （第 318-319 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.5.1 The bsearch function

**参阅**

| [qsort <br />qsort_s (C11)<br />](https://zh.cppreference.com/w/c/algorithm/qsort) | 在一个包含未指定类型的元素的范围上进行排序 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------- |
| **bsearch** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/algorithm/bsearch)** |                                                   |





### bsearch_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### call_once

原址：[http://zh.cppreference.com/w/c/thread/call_once](http://zh.cppreference.com/w/c/thread/call_once)

作用：

备注：
```c
// 在标头 <threads.h> 定义
void call_once( once_flag* flag, void (*func)(void) );// (1)(C11 起)
typedef /* 未指明 */ once_flag// (2)(C11 起)
#define ONCE_FLAG_INIT /* 未指明 */// (3)(C11 起)
```

1） 调用函数 `func` 恰好一次，即使从多个线程调用。函数 `func` 的完成与先前或后继的用同一 `flag` 对象的对 `call_once` 调用同步。

2） 足以保有 `call_once` 所用标志的完整对象类型。

3） 展开成能用于初始化 `once_flag` 类型对象的值。

**参数**

| flag | -    | 指向用于确保只调用一次 `func` 的 `call_once` 对象的指针 |
| ---- | ---- | ------------------------------------------------------- |
| func | -    | 只执行一次的函数                                        |

**返回值**

​	（无）

**注意**

​	此函数的 POSIX 等价物是 [`pthread_once`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_once.html)。

**示例**

```c
#include <stdio.h>
#include <threads.h>
 
void do_once(void) {
    puts("called once");
}
 
static once_flag flag = ONCE_FLAG_INIT;
int func(void* data)
{
    call_once(&flag, do_once);
}
 
int main(void)
{
    thrd_t t1, t2, t3, t4;
    thrd_create(&t1, func, NULL);
    thrd_create(&t2, func, NULL);
    thrd_create(&t3, func, NULL);
    thrd_create(&t4, func, NULL);
 
    thrd_join(t1, NULL);
    thrd_join(t2, NULL);
    thrd_join(t3, NULL);
    thrd_join(t4, NULL);
}
```

​	输出：

```txt
called once
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.26.2.1 The call_once function （第 275 页）

  - 7.26.1/3 ONCE_FLAG_INIT （第 274 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.26.2.1 The call_once function （第 378 页）

  - 7.26.1/3 ONCE_FLAG_INIT （第 376 页）

**参阅**

**call_once** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/thread/call_once)**





### calloc

原址：[http://zh.cppreference.com/w/c/memory/calloc](http://zh.cppreference.com/w/c/memory/calloc)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void* calloc( size_t num, size_t size );
```

​	为 `num` 个 `size` 大小的对象的数组分配内存，并将分配存储中的所有字节初始化为零。

​	若分配成功，会返回指向分配内存块最低位（首位）字节的指针，它为任何具有[基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90)的对象类型适当地对齐。

​	若 `size` 为零，则行为是实现定义的（可返回空指针，或返回不可用于访问存储的非空指针）。

​	`calloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。 ​	解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 free_sized 及 free_aligned_sized(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用*同步于*分配同一块或部分相同的内存区域的 `calloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `calloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。 (C11 起)

**参数**

| num  | -    | 对象数目       |
| ---- | ---- | -------------- |
| size | -    | 每个对象的大小 |

**返回值**

​	成功时，返回指向新分配内存开头的指针。为避免内存泄漏，必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 解分配返回的指针。

​	失败时，返回空指针。

**注解**

​	因为对齐需求的缘故，分配的字节数不必等于 `num * size` 。

​	初始化所有位为零不保证浮点数或指针分别被初始化为 `0.0` 或空指针值（尽管这在所有常见平台上都为真）。

​	本来（C89中），已经为了接纳这种代码增加对零大小的支持：

```
OBJ *p = calloc(0, sizeof(OBJ)); // “零长度”占位
...
while(1)
{ 
    p = realloc(p, c * sizeof(OBJ)); // 重分配，直至大小稳定
    ... // 可能会修改 c 或跳出循环的代码
}
```

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int *p1 = calloc(4, sizeof(int));    // 分配并清零 4 个 int 的数组
    int *p2 = calloc(1, sizeof(int[4])); // 等价，直接命名数组类型
    int *p3 = calloc(4, sizeof *p3);     // 等价，免去重复类型名
 
    if(p2)
    {
        for(int n=0; n<4; ++n) // 打印数组
            printf("p2[%d] == %d\n", n, p2[n]);
    }
 
    free(p1);
    free(p2);
    free(p3);
}
```

​	输出：

```txt
p2[0] == 0
p2[1] == 0
p2[2] == 0
p2[3] == 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.3.2 The calloc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.3.2 The calloc function （第 253 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.3.2 The calloc function （第 348 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.3.1 The calloc function （第 313 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.3.1 The calloc function

**参阅**

**calloc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/memory/c/calloc)**





### div

原址：[http://zh.cppreference.com/w/c/numeric/math/div](http://zh.cppreference.com/w/c/numeric/math/div)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
div_t     div( int x, int y );// (1)
ldiv_t    ldiv( long x, long y );// (2)
lldiv_t   lldiv( long long x, long long y );// (3)(C99 起)
// 在标头 <inttypes.h> 定义
imaxdiv_t imaxdiv( intmax_t x, intmax_t y );// (4)(C99 起)
```

​	计算分子 `x` 除以分母 `y` 的商和余数。

​	同时计算商和余数。商为舍弃小数部分（向零取整）的代数商。余数满足 `quot * y + rem == x`。 (C99 前)

​	同时计算商（表达式 `x / y` 的结果）和余数（表达式 `x % y` 的结果）。 (C99 起)

**参数**

| x, y | -    | 整数值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若余数和商都能表示成对应类型的对象（分别为 `int`、`long`、`long long`、`[intmax_t](http://zh.cppreference.com/w/c/types/integer)`），则将两者作为返回作为定义如下的 `div_t`、`ldiv_t`、`lldiv_t`、`imaxdiv_t` 类型对象返回：

**div_t**

```c
struct div_t { int quot; int rem; };
```

​	或

```c
struct div_t { int rem; int quot; };
```

**ldiv_t**

```c
struct ldiv_t { long quot; long rem; };
```

​	或

```c
struct ldiv_t { long rem; long quot; };
```

**lldiv_t**

```c
struct lldiv_t { long long quot; long long rem; };
```

​	或

```c
struct lldiv_t { long long rem; long long quot; };
```

**imaxdiv_t**

```c
struct imaxdiv_t { intmax_t quot; intmax_t rem; };
```

​	或

```c
struct imaxdiv_t { intmax_t rem; intmax_t quot; };
```

​	若余数或商无法表示，则行为未定义。

**注意**

​	C99 前，若操作数之一为负，则内建的除法和取余运算符中的商取整方向和余数符号是实现定义的，但它在 `div` 和 `ldiv` 中良好定义。

​	多数平台上，单条 CPU 指令可同时获得商和余数，而此函数可以活用这点，尽管编译器通常能在适合处合并临近的 / 和 %。

**示例**

```c
#include <assert.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
 
void reverse(char* first, char* last)
{
    for (--last; first < last; ++first, --last)
    {
        char c = *last;
        *last = *first;
        *first = c;
    }
}
 
// 缓冲区溢出的情况下返回空缓冲区
char* itoa(int n, int base, char* buf, size_t buf_size)
{
    assert(2 <= base && base <= 16 && buf && buf_size);
    div_t dv = {.quot = n};
    char* p = buf;
    do
    {
        if (!--buf_size)
            return (*buf = '\0'), buf;
        dv = div(dv.quot, base);
        *p++ = "0123456789abcdef"[abs(dv.rem)];
    }
    while(dv.quot);
    if (n < 0)
        *p++ = '-';
    *p = '\0';
    reverse(buf, p);
    return buf;
}
 
int main(void)
{
    char buf[16];
    printf("%s\n", itoa(0, 2, buf, sizeof buf));
    printf("%s\n", itoa(007, 3, buf, sizeof buf));
    printf("%s\n", itoa(12346, 10, buf, sizeof buf));
    printf("%s\n", itoa(-12346, 10, buf, sizeof buf));
    printf("%s\n", itoa(-42, 2, buf, sizeof buf));
    printf("%s\n", itoa(INT_MAX, 16, buf, sizeof buf));
    printf("%s\n", itoa(INT_MIN, 16, buf, sizeof buf));
}
```

​	可能的输出：

```txt
0
21
12346
-12346
-101010
7fffffff
-80000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.2 The imaxdiv function （第 TBD 页）

  - 7.22.6.2 The div, ldiv and lldiv functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.2 The imaxdiv function （第 159 页）

  - 7.22.6.2 The div, ldiv and lldiv functions （第 259 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.2 The imaxdiv function （第 219 页）

  - 7.22.6.2 The div, ldiv and lldiv functions （第 356 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.2 The imaxdiv function （第 200 页）

  - 7.20.6.2 The div, ldiv and lldiv functions （第 320 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10 div_t, ldiv_t

  - 4.10.6.2 The div function

  - 4.10.6.4 The ldiv function

**参阅**

| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)                 |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **div** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/div)** |                                                 |

**外部链接**

| 1.   | [欧几里得除法](https://en.wikipedia.org/wiki/Euclidean_division) — 来自 Wikipedia |
| ---- | ------------------------------------------------------------ |
| 2.   | [取模（和截断除法）](https://en.wikipedia.org/wiki/Modulo) — 来自 Wikipedia |





### exit

原址：[https://zh.cppreference.com/w/c/program/exit](https://zh.cppreference.com/w/c/program/exit)

作用：引发正常的程序终止并清理  (函数)

备注：





### free

原址：[http://zh.cppreference.com/w/c/memory/free](http://zh.cppreference.com/w/c/memory/free)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void free( void* ptr );
```

​	解分配之前由 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、aligned_alloc()(C11 起) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc) 分配的空间。

​	若 `ptr` 为空指针，则函数不进行操作。

​	若 `ptr` 的值不等于之前从 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、[realloc()](https://zh.cppreference.com/w/c/memory/realloc) 或 aligned_alloc()(C11 起) 返回的值，则行为未定义。

​	若 `ptr` 所指代的内存区域已经被解分配，则行为未定义，即是说已经以 `ptr` 为实参调用过 `free()`、free_sized()、free_aligned_sized()(C23 起) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc)，而且没有后继的 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、[realloc()](https://zh.cppreference.com/w/c/memory/realloc) 或 aligned_alloc()(C11 起) 调用以 `ptr` 为结果。

​	若在 `free()` 返回后通过指针 `ptr` 访问内存，则行为未定义（除非另一个分配函数恰好返回等于 `ptr` 的值）。

​	`free` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。 ​	解分配一块内存区域的 `free` 调用*同步于*分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。 (C11 起)

**参数**

| ptr  | -    | 指向要解分配的内存的指针 |
| ---- | ---- | ------------------------ |
|      |      |                          |

**返回值**

​	（无）

**注解**

​	此函数接收空指针（并对其不处理）以减少特例的数量。不管分配成功与否，分配函数返回的指针都能传递给 `free()` 。

**示例**

```c
#include <stdlib.h>
 
int main(void)
{
    int *p1 = malloc(10*sizeof *p1);
    free(p1); // 每一个分配的指针都必须释放
 
    int *p2 = calloc(10, sizeof *p2);
    int *p3 = realloc(p2, 1000*sizeof *p3);
    if(p3) // p3 非空表示 p2 已被 realloc 释放
       free(p3);
    else // p3 为空表示 p2 未被释放
       free(p2);
}
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.3.3 The free function （第 365 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.3.3 The free function （第 254 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.3.3 The free function （第 348 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.3.2 The free function （第 313 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.3.2 The free function

**参阅**

| [malloc<br />](https://zh.cppreference.com/w/c/memory/malloc) | 分配内存 (函数)                           |
| ------------------------------------------------------------ | ----------------------------------------- |
| [free_sized (C23)<br />](https://zh.cppreference.com/w/c/memory/free_sized) | 归还之前分配的指定大小的内存 (函数)       |
| [free_aligned_sized (C23)<br />](https://zh.cppreference.com/w/c/memory/free_aligned_sized) | 归还之前分配的指定大小和对齐的内存 (函数) |
| **free** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/memory/c/free)** |                                           |





### free_aligned_sized

原址：

作用：

备注：





### free_sized

原址：

作用：

备注：





### getenv

原址：[http://zh.cppreference.com/w/c/program/getenv](http://zh.cppreference.com/w/c/program/getenv)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
char *getenv( const char *name );// (1)
errno_t getenv_s( size_t *restrict len, char *restrict value,
                  rsize_t valuesz, const char *restrict name );// (2)(C11 起)
```

1） 在宿主指定的环境列表中，查找名为 `name` 的环境变量，并返回关联到匹配环境变量的字符串。环境变量的集合及修改它的方法是实现定义的。

 此函数不保证是线程安全的。另一个对 `getenv` 的调用，和对 POSIX 函数 [setenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/setenv.html)、[unsetenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/unsetenv.html) 及[putenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/putenv.html) 的调用，可能会使先前的调用返回的指针失效，或者修改先前调用所得的字符串。

 修改 `getenv` 返回的字符串会引起未定义行为。

2） 同 (1)，但将环境变量的值写入用户提供的缓冲区 `value`（除非它为 `NULL`），而且将写入的字节数存储于用户提供的位置 `*len`（除非它为 `NULL`）。若环境变量未设置于环境中，则 `*len` 会被写入零（除非是 `NULL`），且 `'\0'` 会被写入 `value[0]`（除非是 `NULL`）。另外，在运行时检测下列错误并调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数

  - `name` 是空指针
  - `valuesz` 大于 RSIZE_MAX
  - `value` 是空指针且 `valuesz` 非零

**参数**

| name    | -    | 标识要查找的环境变量名称的空终止字符串                       |
| ------- | ---- | ------------------------------------------------------------ |
| len     | -    | 指向用户提供的位置，`getenv_s` 将会在其中存储环境变量的长度  |
| value   | -    | 指向用户提供的字符数组，`getenv_s` 将会在其中存储环境变量内容 |
| valuesz | -    | 允许 `getenv_s` 对目标写入的最大字节数（缓冲区大小）         |

**返回值**

1） 标识环境变量的值的字符串，若找不到该环境变量则为空指针。

2） 若找到环境变量则为零，若找不到该环境变量或发生运行时强制违规，则为非零。错误的情况下，将 `*len` 写入零（除非 `len` 为空指针）。

**注解**

​	POSIX 系统上，亦可通过全局变量 `environ` 访问[环境变量](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap08.html#tag_08)，它于 `<unistd.h>` 中声明为 `extern char **environ;`，并可通过可选的 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function)第三参数 `envp` 访问。

​	以空指针为 `value`，以零为 `valuesz` 调用 `getenv_s`，可用于确定保有整个结果所需的缓冲区大小。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char *name = "PATH";
    const char *env_p = getenv(name);
    if (env_p)
        printf("Your %s is %s\n", name, env_p);
}
```

​	可能的输出：

```txt
Your PATH is /home/gamer/.local/bin:/usr/local/bin:/usr/bin:/bin:/usr/share/games
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.4.6 The getenv function （第 TBD 页）

  - K.3.6.2.1 The getenv_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.4.6 The getenv function （第 256-257 页）

  - K.3.6.2.1 The getenv_s function （第 440-441 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.4.6 The getenv function （第 352-353 页）

  - K.3.6.2.1 The getenv_s function （第 606-607 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.4.5 The getenv function （第 317 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.4.4 The getenv function

**参阅**

**getenv** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/getenv)**





### getenv_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### ignore_handler_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### labs

原址：[http://zh.cppreference.com/w/c/numeric/math/abs](http://zh.cppreference.com/w/c/numeric/math/abs)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int        abs( int n );
long       labs( long n );
long long llabs( long long n );// (C99 起)
// 在标头 <inttypes.h> 定义
intmax_t imaxabs( intmax_t n );// (C99 起)
```

​	计算整数的绝对值。若返回类型无法表示结果，则行为未定义。

**参数**

| n    | -    | 整数值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	`n` 的绝对值（即 `|n|`），若它能被表示。

**注解**

​	在补码系统中，最小负值的绝对值处于对应整数范围外，例如对于 32 位补码类型 `int`，[INT_MIN](https://zh.cppreference.com/w/c/types/limits) 为 `-2147483648`，但其绝对值应有的结果是 `2147483648`，大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)（其值为 `2147483647`）。

**示例**

```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("abs(+3) = %d\n", abs(+3));
    printf("abs(-3) = %d\n", abs(-3));
 
//  printf("%+d\n", abs(INT_MIN)); // 在补码系统上是未定义行为
}
```

​	输出：

```txt
abs(+3) = 3
abs(-3) = 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.1 The imaxabs function （第 TBD 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.1 The imaxabs function （第 159 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 259 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.1 The imaxabs function （第 218 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 356 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.1 The imaxabs function （第 199-200 页）

  - 7.20.6.1 The abs, labs and llabs functions （第 320 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.6.1 The abs function

  - 4.10.6.3 The labs function

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)           |
| **abs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/abs)** |                                         |





### ldiv

原址：[http://zh.cppreference.com/w/c/numeric/math/div](http://zh.cppreference.com/w/c/numeric/math/div)

作用：

备注：

```c
// 在标头 <stdlib.h> 定义
div_t     div( int x, int y );// (1)
ldiv_t    ldiv( long x, long y );// (2)
lldiv_t   lldiv( long long x, long long y );// (3)(C99 起)
// 在标头 <inttypes.h> 定义
imaxdiv_t imaxdiv( intmax_t x, intmax_t y );// (4)(C99 起)
```

​	计算分子 `x` 除以分母 `y` 的商和余数。

​	同时计算商和余数。商为舍弃小数部分（向零取整）的代数商。余数满足 `quot * y + rem == x`。 (C99 前)

​	同时计算商（表达式 `x / y` 的结果）和余数（表达式 `x % y` 的结果）。 (C99 起)

**参数**

| x, y | -    | 整数值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若余数和商都能表示成对应类型的对象（分别为 `int`、`long`、`long long`、`[intmax_t](http://zh.cppreference.com/w/c/types/integer)`），则将两者作为返回作为定义如下的 `div_t`、`ldiv_t`、`lldiv_t`、`imaxdiv_t` 类型对象返回：

**div_t**

```c
struct div_t { int quot; int rem; };
```

​	或

```c
struct div_t { int rem; int quot; };
```

**ldiv_t**

```c
struct ldiv_t { long quot; long rem; };
```

​	或

```c
struct ldiv_t { long rem; long quot; };
```

**lldiv_t**

```c
struct lldiv_t { long long quot; long long rem; };
```

​	或

```c
struct lldiv_t { long long rem; long long quot; };
```

**imaxdiv_t**

```c
struct imaxdiv_t { intmax_t quot; intmax_t rem; };
```

​	或

```c
struct imaxdiv_t { intmax_t rem; intmax_t quot; };
```

​	若余数或商无法表示，则行为未定义。

**注意**

​	C99 前，若操作数之一为负，则内建的除法和取余运算符中的商取整方向和余数符号是实现定义的，但它在 `div` 和 `ldiv` 中良好定义。

​	多数平台上，单条 CPU 指令可同时获得商和余数，而此函数可以活用这点，尽管编译器通常能在适合处合并临近的 / 和 %。

**示例**

```c
#include <assert.h>
#include <limits.h>
#include <math.h>
#include <stdio.h>
#include <stdlib.h>
 
void reverse(char* first, char* last)
{
    for (--last; first < last; ++first, --last)
    {
        char c = *last;
        *last = *first;
        *first = c;
    }
}
 
// 缓冲区溢出的情况下返回空缓冲区
char* itoa(int n, int base, char* buf, size_t buf_size)
{
    assert(2 <= base && base <= 16 && buf && buf_size);
    div_t dv = {.quot = n};
    char* p = buf;
    do
    {
        if (!--buf_size)
            return (*buf = '\0'), buf;
        dv = div(dv.quot, base);
        *p++ = "0123456789abcdef"[abs(dv.rem)];
    }
    while(dv.quot);
    if (n < 0)
        *p++ = '-';
    *p = '\0';
    reverse(buf, p);
    return buf;
}
 
int main(void)
{
    char buf[16];
    printf("%s\n", itoa(0, 2, buf, sizeof buf));
    printf("%s\n", itoa(007, 3, buf, sizeof buf));
    printf("%s\n", itoa(12346, 10, buf, sizeof buf));
    printf("%s\n", itoa(-12346, 10, buf, sizeof buf));
    printf("%s\n", itoa(-42, 2, buf, sizeof buf));
    printf("%s\n", itoa(INT_MAX, 16, buf, sizeof buf));
    printf("%s\n", itoa(INT_MIN, 16, buf, sizeof buf));
}
```

​	可能的输出：

```txt
0
21
12346
-12346
-101010
7fffffff
-80000000
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.2 The imaxdiv function （第 TBD 页）

  - 7.22.6.2 The div, ldiv and lldiv functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.2 The imaxdiv function （第 159 页）

  - 7.22.6.2 The div, ldiv and lldiv functions （第 259 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.2 The imaxdiv function （第 219 页）

  - 7.22.6.2 The div, ldiv and lldiv functions （第 356 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.2 The imaxdiv function （第 200 页）

  - 7.20.6.2 The div, ldiv and lldiv functions （第 320 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10 div_t, ldiv_t

  - 4.10.6.2 The div function

  - 4.10.6.4 The ldiv function

**参阅**

| [fmod <br />fmodf (C99)<br />fmodl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fmod) | 计算浮点数除法运算的余数 (函数)                 |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [remainder (C99)<br />remainderf (C99)<br />remainderl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remainder) | 计算浮点数除法运算的带符号余数 (函数)           |
| [remquo (C99)<br />remquof (C99)<br />remquol (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/remquo) | 计算除法运算的带符号余数，以及商的后三位 (函数) |
| **div** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/div)** |                                                 |

**外部链接**

| 1.   | [欧几里得除法](https://en.wikipedia.org/wiki/Euclidean_division) — 来自 Wikipedia |
| ---- | ------------------------------------------------------------ |
| 2.   | [取模（和截断除法）](https://en.wikipedia.org/wiki/Modulo) — 来自 Wikipedia |







### llabs

原址：[http://zh.cppreference.com/w/c/numeric/math/abs](http://zh.cppreference.com/w/c/numeric/math/abs)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int        abs( int n );
long       labs( long n );
long long llabs( long long n );// (C99 起)
// 在标头 <inttypes.h> 定义
intmax_t imaxabs( intmax_t n );// (C99 起)
```

​	计算整数的绝对值。若返回类型无法表示结果，则行为未定义。

**参数**

| n    | -    | 整数值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	`n` 的绝对值（即 `|n|`），若它能被表示。

**注解**

​	在补码系统中，最小负值的绝对值处于对应整数范围外，例如对于 32 位补码类型 `int`，[INT_MIN](https://zh.cppreference.com/w/c/types/limits) 为 `-2147483648`，但其绝对值应有的结果是 `2147483648`，大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)（其值为 `2147483647`）。

**示例**

```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    printf("abs(+3) = %d\n", abs(+3));
    printf("abs(-3) = %d\n", abs(-3));
 
//  printf("%+d\n", abs(INT_MIN)); // 在补码系统上是未定义行为
}
```

​	输出：

```txt
abs(+3) = 3
abs(-3) = 3
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.8.2.1 The imaxabs function （第 TBD 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.8.2.1 The imaxabs function （第 159 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 259 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.8.2.1 The imaxabs function （第 218 页）

  - 7.22.6.1 The abs, labs and llabs functions （第 356 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.8.2.1 The imaxabs function （第 199-200 页）

  - 7.20.6.1 The abs, labs and llabs functions （第 320 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.6.1 The abs function

  - 4.10.6.3 The labs function

**参阅**

| [fabs <br />fabsf (C99)<br />fabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/math/fabs) | 计算浮点数的绝对值（\|x\|\|x\|） (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| [cabs (C99)<br />cabsf (C99)<br />cabsl (C99)<br />](https://zh.cppreference.com/w/c/numeric/complex/cabs) | 计算复数的模（绝对值） (函数)           |
| **abs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/math/abs)** |                                         |





### lldiv

原址：

作用：

备注：





### malloc

原址：[http://zh.cppreference.com/w/c/memory/malloc](http://zh.cppreference.com/w/c/memory/malloc)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void* malloc( size_t size );
```

​	分配 `size` 字节的未初始化内存。

​	若分配成功，则返回为任何拥有[基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90)的对象类型对齐的指针。

​	若 `size` 为零，则 `malloc` 的行为实现是其实现（生成）时定义的。例如可返回空指针。亦可返回非空指针；但不应当[解引用](https://zh.cppreference.com/w/c/language/operator_member_access)这种指针，而且应将它传递给 [free](https://zh.cppreference.com/w/c/memory/free) 以避免内存泄漏。

​	`malloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。 ​	解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 free_sized 及 free_aligned_sized(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用*同步于*分配同一块或部分相同的内存区域的 `malloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `malloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。 (C11 起)

**参数**

| size | -    | 要分配的字节数 |
| ---- | ---- | -------------- |
|      |      |                |

**返回值**

​	成功时，返回指向新分配内存的指针。为避免内存泄漏，必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc) 解分配返回的指针。

​	失败时，返回空指针。

**示例**

```c
#include <stdio.h>   
#include <stdlib.h> 
 
int main(void) 
{
    int *p1 = malloc(4*sizeof(int));  // 足以分配 4 个 int 的数组
    int *p2 = malloc(sizeof(int[4])); // 等价，直接命名数组类型
    int *p3 = malloc(4*sizeof *p3);   // 等价，免去重复类型名
 
    if(p1) {
        for(int n=0; n<4; ++n) // 置入数组
            p1[n] = n*n;
        for(int n=0; n<4; ++n) // 打印出来
            printf("p1[%d] == %d\n", n, p1[n]);
    }
 
    free(p1);
    free(p2);
    free(p3);
}
```

​	输出：

```txt
p1[0] == 0
p1[1] == 1
p1[2] == 4
p1[3] == 9
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.3.4 The malloc function （第 254 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.3.4 The malloc function （第 349 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.3.3 The malloc function （第 314 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.3.3 The malloc function

**参阅**

| [free<br />](https://zh.cppreference.com/w/c/memory/free)  | 归还之前分配的内存 (函数) |
| ------------------------------------------------------------ | ------------------------- |
| **malloc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/memory/c/malloc)** |                           |





### mblen

原址：[http://zh.cppreference.com/w/c/string/multibyte/mblen](http://zh.cppreference.com/w/c/string/multibyte/mblen)

作用：

备注：

```c
// 在标头 <stdlib.h> 定义
int mblen( const char* s, size_t n );
```

​	确定 `s` 指向其首字节的多字节字符的字节大小。

​	若 `s` 是空指针，则重置全局转换状态并(C23 前)确定是否使用迁移序列。

​	此函数等价于调用 `[mbtowc](http://zh.cppreference.com/w/c/string/multibyte/mbtowc)((wchar_t*)0, s, n)`，除了 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 的转换状态不受影响。

**参数**

| s    | -    | 指向多字节字符的指针       |
| ---- | ---- | -------------------------- |
| n    | -    | `s` 中能被检验的字节数限制 |

**返回值**

​	若 `s` 不是空指针，则返回多字节字符所含的字节数，或若 `s` 所指的首字节不组成合法多字节字符则返回 `-1`，或若 `s` 指向空字符 `'\0'` 则返回 `0`。

​	若 `s` 是空指针，则重置内部转换状态为初始迁移状态，(C23 前)若当前多字节编码非状态依赖（不使用迁移序列）则返回 `0`，或者若当前多字节编码为状态依赖（使用迁移序列）则返回非零。

**注解**

​	每次对 `mblen` 的调用更新内部全局转换状态（ [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的静态对象，只为此函数所知）。若多字节编码使用迁移状态，则必须留意以避免回撤或多次扫描。任何情况下，多线程不应无同步地调用 `mblen`：可用 [mbrlen](https://zh.cppreference.com/w/c/string/multibyte/mbrlen) 代替。 (C23 前)

​	不允许 `mblen` 拥有内部状态。 (C23 起)

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
// 多字节字符串的字符数是 mblen() 的和
// 注意：更简单的手段是 mbstowcs(NULL, str, sz)
size_t strlen_mb(const char* ptr)
{
    size_t result = 0;
    const char* end = ptr + strlen(ptr);
    mblen(NULL, 0); // 重置转换状态
    while(ptr < end) {
        int next = mblen(ptr, end - ptr);
        if (next == -1) {
           perror("strlen_mb");
           break;
        }
        ptr += next;
        ++result;
    }
    return result;
}
 
void dump_bytes(const char* str)
{
    for (const char* end = str + strlen(str); str != end; ++str)
        printf("%02X ", (unsigned char)str[0]);
    printf("\n");
}
 
int main(void)
{
    setlocale(LC_ALL, "en_US.utf8");
    const char* str = "z\u00df\u6c34\U0001f34c";
    printf("字符串 \"%s\" 包含 %zu 个字符，但为 %zu 字节：",
            str, strlen_mb(str), strlen(str));
    dump_bytes(str);
}
```

​	可能的输出：

```txt
字符串 "zß水🍌" 包含 4 个字符，但为 10 字节：7A C3 9F E6 B0 B4 F0 9F 8D 8C
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.7.1 The mblen function （第 260 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.7.1 The mblen function （第 357 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.7.1 The mblen function （第 321 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.7.1 The mblen function

参阅

| [mbtowc<br />](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) | 转换下一个多字节字符为宽字符 (函数)           |
| ------------------------------------------------------------ | --------------------------------------------- |
| [mbrlen (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrlen) | 给定状态，返回下一个多字节字符的字节数 (函数) |
| **mblen** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte/mblen)** |                                               |





### mbstowcs

原址：[http://zh.cppreference.com/w/c/string/multibyte/mbstowcs](http://zh.cppreference.com/w/c/string/multibyte/mbstowcs)

作用：

备注：

```c
// 在标头 <stdlib.h> 定义
// (1)
size_t mbstowcs( wchar_t          *dst, const char          *src, size_t len)// (C99 前)
size_t mbstowcs( wchar_t *restrict dst, const char *restrict src, size_t len)// (C99 起)
errno_t mbstowcs_s(size_t *restrict retval, wchar_t *restrict dst,
                  rsize_t dstsz, const char *restrict src, rsize_t len);// (2)(C11 起)
```

1） 将从首元素为 `src` 所指的数组中的多字节字符串转换为其宽字符表示。被转换的字符存储于 `dst` 所指向数组的相继元素。写入目标数组的宽字符数不多于 `len`。

 如同以调用 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 来转换每个字符，除了 mbtowc 转换状态不受影响。若满足任一条件则转换停止：

 \* 转换并存储了多字节空字符。

 \* 遇到（当前 C 本地环境中的）非法多字节字符。

 \* 将要存储的下个宽字符会超出 `len`。

 若 `src` 与 `dst` 重叠，则行为未定义

2） 同 (1)，但

 \* 如同以 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)，而非 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 进行转换

 \* 函数用输出参数 `retval` 返回结果

 \* 若在写入 `len` 个宽字符后未写入空字符到 `dst`，则存储 `L'\0'` 于 `dst[len]`，这表示总计写入 len+1 个宽字符

 \* 若 `dst` 是空指针，则存储本会产生的宽字符数于 `*retval`

 \* 函数破坏目标数组从空终止到 `dstsz` 为止的内容

 \* 若 `src` 与 `dst` 重叠，则行为未指定。

 \* 在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `retval` 或 `src` 是空指针
  - `dstsz` 或 `len` 大于 RSIZE_MAX/sizeof(wchar_t)（除非 `dst` 为空）
  - `dstsz` 非零（除非 `dst` 为空）
  - `src` 数组中的前 `dstsz` 个多字节中无空字符且 `len` 大于 `dstsz`（除非 `dst` 为空）

**注意**

​	多数实现中，`mbstowcs` 在处理字符串进程中更新一个 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的全局静态对象，因而不能由两个线程同时调用，这种情况下应当使用 [mbsrtowcs](https://zh.cppreference.com/w/c/string/multibyte/mbsrtowcs)。

​	POSIX 指定一个常见扩展：若 `dst` 是空指针，则此函数返回假若转换则写入 `dst` 的宽字符数。同样的行为对于 `mbstowcs_s` 和 [mbsrtowcs](https://zh.cppreference.com/w/c/string/multibyte/mbsrtowcs) 是标准。

**参数**

| dst    | -    | 指向要存储宽字符串的宽字符数组的指针         |
| ------ | ---- | -------------------------------------------- |
| src    | -    | 指向要转换的空终止多字节字符串的首元素的指针 |
| len    | -    | dst 所指向的数组中的可用宽字节数             |
| dstsz  | -    | 将写入的最大宽字节数（`dst` 数组的大小）     |
| retval | -    | 指向 size_t 对象的指针，将存储结果           |

**返回值**

1） 成功时，返回目标数组的宽字符数，不含终止符 `L'\0'`。转换错误时（若遇到非法多字节字符），返回 `([size_t](http://zh.cppreference.com/w/c/types/size_t))-1`。

2） 成功时为零（该情况下写入或本该写入到 `dst` 的不含终止零的宽字符存储于 `*retval`），错误时为非零，在运行时制约违规的情况，存储 `([size_t](http://zh.cppreference.com/w/c/types/size_t))-1` 于 `*retval`（除非 `retval` 为空）并设置 `dst[0]` 为 `L'\0'`（除非 `dst` 为空或 `dstmax` 为零或大于 RSIZE_MAX）

**示例**

```c
#include <stdio.h>
#include <locale.h>
#include <stdlib.h>
#include <wchar.h>
 
int main(void)
{
    setlocale(LC_ALL, "en_US.utf8");
    const char* mbstr = u8"z\u00df\u6c34\U0001F34C"; // 即 u8"zß水🍌"
    wchar_t wstr[5];
    mbstowcs(wstr, mbstr, 5);
    wprintf(L"多字节字符串：%s\n", mbstr);
    wprintf(L"宽字符串：%ls\n", wstr);
}
```

​	输出：

```txt
多字节字符串：zß水🍌
宽字符串：zß水🍌
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.8.1 The mbstowcs function （第 359 页）

  - K.3.6.5.1 The mbstowcs_s function （第 611-612 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.8.1 The mbstowcs function （第 323 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.8.1 The mbstowcs function

**参阅**

| [mbsrtowcs (C95)<br />mbsrtowcs_s (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbsrtowcs) | 给定状态，转换窄多字节字符串为宽字符串 (函数) |
| ------------------------------------------------------------ | --------------------------------------------- |
| [wcstombs <br />wcstombs_s (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/wcstombs) | 转换宽字符串为窄多字节字符串 (函数)           |
| **mbstowcs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte/mbstowcs)** |                                               |



### mbstowcs_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### mbtowc

原址：[http://zh.cppreference.com/w/c/string/multibyte/mbtowc](http://zh.cppreference.com/w/c/string/multibyte/mbtowc)

作用：

备注：

```c
// 在标头 <stdlib.h> 定义
int mbtowc( wchar_t*          pwc, const char*          s, size_t n )// (C99 前)
int mbtowc( wchar_t* restrict pwc, const char* restrict s, size_t n )// (C99 起)
```

​	将 `s` 指向其首字节的多字节字符转换成宽字符，若 `pwc` 非空则写入 `*pwc`。

​	若 `s` 为空指针，则重置全局转换状态并确定是否使用迁移序列。

**注解**

​	每次对 `mbtowc` 的调用更新内部全局转换状态（[mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的静态对象，只为此函数所知）。若多字节编码使用迁移状态，则必须留意以避免回撤或多次扫描。任何情况下，多线程不应调用 `mbtowc` 而不同步：可用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc) 代替。

**参数**

| pwc  | -    | 指向输出用宽字符的指针       |
| ---- | ---- | ---------------------------- |
| s    | -    | 指向多字节字符的指针         |
| n    | -    | `s` 中能被检验的字节数的限制 |

**返回值**

​	若 `s` 不是空指针，则返回多字节字符所含的字节数，或若 `s` 所指的首字节不组成合法多字节字符则返回 `-1`，或若 `s` 指向空字符 `'\0'` 则返回 `0`。

​	若 `s` 是空指针，则重置内部转换状态为初始迁移状态，并若当前多字节编码非状态依赖（不使用迁移序列）则返回 `0`，或若当前多字节编码为状态依赖（使用迁移序列）则返回非零值。

**示例**

```c
#include <locale.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <wchar.h>
 
// 打印多字节字符串到宽面向的 stdout
// 等价于 wprintf(L"%s\n", ptr);
void print_mb(const char* ptr)
{
    mbtowc(NULL, NULL, 0); // 重置初始转换状态
    const char* end = ptr + strlen(ptr);
    int ret = 0;
    for (wchar_t wc; (ret = mbtowc(&wc, ptr, end - ptr)) > 0; ptr += ret)
        wprintf(L"%lc", wc);
    wprintf(L"\n");
}
 
int main(void)
{
    setlocale(LC_ALL, "en_US.utf8");
    // UTF-8 窄多字节编码
    print_mb("z\u00df\u6c34\U0001F34C"); // 即 "zß水🍌"
}
```

​	输出：

```txt
zß水🍌
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.7.2 The mbtowc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.7.2 The mbtowc function （第 260 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.7.2 The mbtowc function （第 358 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.7.2 The mbtowc function （第 322 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.7.2 The mbtowc function

**参阅**

| [mbrtowc (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc) | 给定状态，转换下一个多字节字符为宽字符 (函数) |
| ------------------------------------------------------------ | --------------------------------------------- |
| [mblen<br />](https://zh.cppreference.com/w/c/string/multibyte/mblen) | 返回下一个多字节字符的字节数 (函数)           |
| **mbtowc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte/mbtowc)** |                                               |







### memalignment

原址：

作用：

备注：





### qsort

原址：[http://zh.cppreference.com/w/c/algorithm/qsort](http://zh.cppreference.com/w/c/algorithm/qsort)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void qsort( void* ptr, size_t count, size_t size,
            int (*comp)(const void*, const void*) );// (1)
errno_t qsort_s( void* ptr, rsize_t count, rsize_t size,
                 int (*comp)(const void*, const void*, void*),

                 void* context );// (2)(C11 起)
```

1） 对 `ptr` 所指向的数组以升序排序。数组包含 `count` 个长度为 `size` 字节的元素。用 `comp` 所指向的函数比较对象。

2） 同 (1)，除了传递给 `comp` 附加环境参数 `context`，还会在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

  - `count` 或 `size` 大于 RSIZE_MAX
  - `ptr` 或 `comp` 是空指针（除非 `count` 为零）

​	若 `comp` 指示两元素相等，则它们排序后的结果是未指定的。

**参数**

| ptr     | -    | 指向待排序的数组的指针                                       |
| ------- | ---- | ------------------------------------------------------------ |
| count   | -    | 数组的元素数目                                               |
| size    | -    | 数组每个元素的字节大小                                       |
| comp    | -    | 比较函数。如果首个参数*小于* ﻿第二个，那么返回负整数值，如果首个参数*大于* ﻿第二个，那么返回正整数值，如果两个参数等价，那么返回零。 ​	比较函数的签名应等价于如下形式：​	`int cmp(const void *a, const void *b);`​	该函数必须不修改传递给它的对象，而且在调用比较相同对象时必须返回一致的结果，与它们在数组中的位置无关。​	 |
| context | -    | 附加信息（例如，校排序列），作为第三个参数传递给 `comp`      |

**返回值**

1） （无）

2） 成功时为零，若检测到运行时制约违规，则为非零

**注意**

​	不管其名字如何，C 和 POSIX 标准都未要求此函数用[快速排序](https://en.wikipedia.org/wiki/Quicksort)实现，也未保证任何复杂度或稳定性。

​	与其他边界检查函数不同，`qsort_s` 不将零大小数组视作运行时强制违规，而是不修改数组并成功返回（另一个接受零大小数组的函数是 bsearch_s）。

​	[Windows CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/qsort-s) 中的 `qsort_s` 实现与 C 标准不兼容。微软的版本被声明为： `void qsort_s(void *base, [size_t](http://zh.cppreference.com/w/c/types/size_t) num, [size_t](http://zh.cppreference.com/w/c/types/size_t) width,
​       int (*compare )(void *, const void *, const void *), void * context);`。 它不返回值，而比较函数具有与标准相反的形参顺序：首先传递的是 `context`。

**示例**

```c
#include <limits.h>
#include <stdio.h>
#include <stdlib.h>
 
int compare_ints(const void* a, const void* b)
{
    int arg1 = *(const int*)a;
    int arg2 = *(const int*)b;
 
    if (arg1 < arg2) return -1;
    if (arg1 > arg2) return 1;
    return 0;
 
    // return (arg1 > arg2) - (arg1 < arg2); // 可行的简写
    // return arg1 - arg2; // 错误的简写：整数溢出时为未定义行为，比如此处使用 INT_MIN 时
}
 
int main(void)
{
    int ints[] = {-2, 99, 0, -743, 2, INT_MIN, 4};
    int size = sizeof ints / sizeof *ints;
 
    qsort(ints, size, sizeof(int), compare_ints);
 
    for (int i = 0; i < size; i++)
        printf("%d ", ints[i]);
 
    printf("\n");
}
```

​	输出：

```txt
-2147483648 -743 -2 0 2 4 99
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.5.2 The qsort function （第 TBD 页）

  - K.3.6.3.2 The qsort_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.5.2 The qsort function （第 258-259 页）

  - K.3.6.3.2 The qsort_s function （第 442-443 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.5.2 The qsort function （第 355-356 页）

  - K.3.6.3.2 The qsort_s function （第 609 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.5.2 The qsort function （第 319 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.5.2 The qsort function

**参阅**

| [bsearch <br />bsearch_s (C11)<br />](https://zh.cppreference.com/w/c/algorithm/bsearch) | 在未指定类型的数组中搜索一个元素 (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| **qsort** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/algorithm/qsort)** |                                         |





### qsort_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### quick_exit

原址：[https://zh.cppreference.com/w/c/program/quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)

作用：引发正常的程序终止但不完全清理  (函数)

备注：





### rand

原址：[http://zh.cppreference.com/w/c/numeric/random/rand](http://zh.cppreference.com/w/c/numeric/random/rand)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int rand();
```

​	返回 `0` 与 [RAND_MAX](https://zh.cppreference.com/w/c/numeric/random/RAND_MAX) 间的随机整数值（包含 0 与 `RAND_MAX`）。

​	[srand()](https://zh.cppreference.com/w/c/numeric/random/srand) 播种 `rand()` 所用的伪随机数生成器。若在任何对 `srand()` 的调用前使用 `rand()`，则 `rand()` 表现如同它以 `srand(1)` 播种。每次以 `srand()` 播种 `rand()` 时，它必须产生相同的值数列。

​	不保证 `rand()` 为线程安全。

**参数**

​	（无）

**返回值**

​	`0` 与 [RAND_MAX](https://zh.cppreference.com/w/c/numeric/random/RAND_MAX) 间包含边界的随机整数值。

**注意**

​	无对产生的随机数质量的保证。过去，某些 `rand()` 的实现在随机性、分布和产生的数列周期中有严重缺陷（在一个广为人知的例子中，最低位在调用间简单地于 `1` 和 `0` 间改变）。不推荐将 `rand()` 用于严肃的随机数生成需求，如加密。

​	POSIX 要求 `rand` 所用的伪随机数生成器的周期至少为 *232
*。

​	POSIX 提供 rand 的线程安全版本，名为 `rand_r`，它由于 [`drand48`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/drand48.html) 函数族而过时。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
 
int main(void)
{
    srand(time(NULL)); // 以当前时间为随机生成器的种子
    int random_variable = rand();
    printf("Random value on [0,%d]: %d\n", RAND_MAX, random_variable);
 
    // 扔 6 面色子 20 次
    for (int n = 0; n != 20; ++n) {
        int x = 7;
        while(x > 6) 
            x = 1 + rand() / ((RAND_MAX + 1u) / 6); // 注意： 1 + rand() % 6 有偏差！
        printf("%d ", x); 
    }
}
```

​	可能的输出：

```txt
Random value on [0,2147483647]: 448749574
3 1 3 1 4 2 2 1 3 6 4 4 3 1 6 2 3 2 6 1
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.2.1 The rand function （第 252 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.2.1 The rand function （第 346 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.2.1 The rand function （第 312 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.2.1 The rand function

**参阅**

| [srand<br />](https://zh.cppreference.com/w/c/numeric/random/srand) | 播种伪随机数生成器 (函数)          |
| ------------------------------------------------------------ | ---------------------------------- |
| [RAND_MAX<br />](https://zh.cppreference.com/w/c/numeric/random/RAND_MAX) | `rand()` 生成的最大可能值 (宏常量) |
| **rand** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/random/rand)** |                                    |





### realloc

原址：[http://zh.cppreference.com/w/c/memory/realloc](http://zh.cppreference.com/w/c/memory/realloc)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void *realloc( void *ptr, size_t new_size );
```

​	重新分配给定的内存区域。若 `ptr` 非 NULL，则它必须是之前为 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc) 或 `realloc()` 所分配，并且仍未被 [free](https://zh.cppreference.com/w/c/memory/free) 或 `realloc` 的调用所释放。否则，结果未定义。

​	重新分配按以下二者之一执行：

a) 可能的话，扩张或收缩 `ptr` 所指向的现有内存区域。新旧大小中的较小者范围内的区域的内容保持不变。若扩张范围，则数组新增部分的内容是未定义的。

b) 分配一个大小为 `new_size` 字节的新内存块，并复制大小等于新旧大小中较小者的内存区域，然后释放旧内存块。

​	若无足够内存，则不释放旧内存块，并返回空指针。

​	若 `ptr` 为 [NULL](https://zh.cppreference.com/w/c/types/NULL)，则行为与调用 `[malloc](http://zh.cppreference.com/w/c/memory/malloc)(new_size)` 相同。

​	否则，

​	若 `new_size` 为零，则行为是实现定义的（可能返回空指针，该情况下可能或可能不释放旧内存，或可能返回某个不能用于访问存储的非空指针）。这种用法被弃用（经由 [C DR 400](https://open-std.org/JTC1/SC22/WG14/www/docs/n2396.htm#dr_400)）。(C17 起) (C23 前)

​	若 `new_size` 为零，则行为未定义。 (C23 起)

​	`realloc` 是线程安全的：它表现得如同只访问通过其实参可见的内存区域，而非任何静态存储。 ​	先前令 [free](https://zh.cppreference.com/w/c/memory/free) 或 `realloc` 归还一块内存区域的调用，*同步于*任何分配函数的调用，包括分配相同或部分相同内存区域的 `realloc` 。这种同步出现于任何解分配函数所做的内存访问后，和任何 `realloc` 所做内存访问前。所有操作一块特定内存区域的分配及解分配函数拥有单独全序。 (C11 起)

**参数**

| ptr      | -    | 指向需要重新分配的内存区域的指针 |
| -------- | ---- | -------------------------------- |
| new_size | -    | 数组的新大小（字节数）           |

**返回值**

​	成功时，返回指向新分配内存的指针。返回的指针必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 归还。原指针 `ptr` 失效，而且任何通过它的访问是未定义行为（即使重分配是就地的）。

​	失败时，返回空指针。原指针 `ptr` 保持有效，并需要通过 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 归还。

**注解**

​	本来（C89 中），增加对零大小的支持是为了容纳这种代码：

```
OBJ *p = calloc(0, sizeof(OBJ)); // “零长度”占位
/*...*/
while(1) { 
    p = realloc(p, c * sizeof(OBJ)); // 重分配，直至大小稳定
    /* 可能会修改 c 或跳出循环的代码 */
}
```

**示例**

```c
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
void print_storage_info(const int* next, const int* prev, int ints)
{
    if (next)
        printf("%s location: %p. Size: %d ints (%ld bytes).\n",
               (next != prev ? "New" : "Old"), (void*)next, ints, ints * sizeof(int));
    else
        printf("Allocation failed.\n");
}
 
int main(void)
{
    const int pattern[] = {1, 2, 3, 4, 5, 6, 7, 8};
    const int pattern_size = sizeof pattern / sizeof(int);
    int *next = NULL, *prev = NULL;
 
    if ((next = (int*)malloc(pattern_size * sizeof *next))) // 分配数组
    {
        memcpy(next, pattern, sizeof pattern); // 填充数组
        print_storage_info(next, prev, pattern_size);
    }
    else
        return EXIT_FAILURE;
 
    // 以如下各值作为新的存储大小，在循环中重新分配。
    const int realloc_size[] = {10, 12, 512, 32768, 65536, 32768};
 
    for (int i = 0; i != sizeof realloc_size / sizeof(int); ++i)
    {
        if ((next = (int*)realloc(prev = next, realloc_size[i] * sizeof(int))))
        {
            print_storage_info(next, prev, realloc_size[i]);
            assert(!memcmp(next, pattern, sizeof pattern));  // 持有模式内容
        }
        else // 若 realloc 失败，则需要释放原指针
        {
            free(prev);
            return EXIT_FAILURE;
        }
    }
 
    free(next); // 最后，释放存储
    return EXIT_SUCCESS;
}
```

​	可能的输出：

```txt
New location: 0x144c010. Size: 8 ints (32 bytes).
Old location: 0x144c010. Size: 10 ints (40 bytes).
New location: 0x144c450. Size: 12 ints (48 bytes).
Old location: 0x144c450. Size: 512 ints (2048 bytes).
Old location: 0x144c450. Size: 32768 ints (131072 bytes).
New location: 0x7f490c5bd010. Size: 65536 ints (262144 bytes).
Old location: 0x7f490c5bd010. Size: 32768 ints (131072 bytes).
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.3.5 The realloc function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.3.5 The realloc function （第 254 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.3.5 The realloc function （第 349 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.3.4 The realloc function （第 314 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.3.4 The realloc function

**参阅**

**realloc** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/memory/c/realloc)**





### set_constraint_handler_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### srand

原址：[http://zh.cppreference.com/w/c/numeric/random/srand](http://zh.cppreference.com/w/c/numeric/random/srand)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
void srand( unsigned seed );
```

​	以值 `seed` 播种 [rand()](https://zh.cppreference.com/w/c/numeric/random/rand) 所用的随机数生成器。

​	若在任何到 `srand()` 的调用前使用 `rand()`，则 `rand()` 表现为如同它被以 `srand(1)` 播种。

​	每次以同一 `seed` 播种 `rand()` 时，它必须产生相同的值数列。

​	`srand()` 不保证为线程安全。

**参数**

| seed 种子值 | -    |      |
| ----------- | ---- | ---- |
|             |      |      |

**返回值**

​	（无）

**注意**

​	通常来说，应该只播种一次随机数生成器，在程序开始处，任何到 `rand()` 的调用前。不应重复播种，或每次冀愿生成新一批随机数时重播种。

​	标准实践是使用以 `[time](http://zh.cppreference.com/w/c/chrono/time)(0)` 为种子调用的结果。然而 `time()` 返回 `[time_t](http://zh.cppreference.com/w/c/chrono/time_t)` 值，而不保证 `time_t` 是整数类型。 尽管实践中，主流实现都定义 `time_t` 为整数类型，且此亦为 POSIX 所要求。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
 
int main(void)
{
    srand(time(0)); // 以当前时间为随机数生成器的种子
    int random_variable = rand();
    printf("Random value on [0,%d]: %d\n", RAND_MAX, random_variable);
}
```

​	可能的输出：

```txt
Random value on [0 2147483647]: 1373858591
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.2.2 The srand function （第 252-253 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.2.2 The srand function （第 346-347 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.2.2 The srand function （第 312-313 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.2.2 The srand function

**参阅**

| [rand<br />](https://zh.cppreference.com/w/c/numeric/random/rand) | 产生一个伪随机数 (函数)                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [RAND_MAX<br />](https://zh.cppreference.com/w/c/numeric/random/RAND_MAX) | `[rand](http://zh.cppreference.com/w/c/numeric/random/rand)()` 生成的最大可能值 (宏常量) |
| **srand** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/numeric/random/srand)** |                                                              |





### strfromd

原址：

作用：

备注：





### strfromd128

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_DFP__`：






### strfromd32

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_DFP__`：






### strfromd64

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_DFP__`：






### strfromdN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfromdNx

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfromencbindN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfromencdecdN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfromencfN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfromf

原址：

作用：

备注：





### strfromfN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfromfNx

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strfroml

原址：

作用：

备注：





### strtod

原址：[http://zh.cppreference.com/w/c/string/byte/strtof](http://zh.cppreference.com/w/c/string/byte/strtof)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
float       strtof ( const char* restrict str, char** restrict str_end );// (1)(C99 起)
// (2)
double      strtod ( const char*          str, char**          str_end );// (C99 前)
double      strtod ( const char* restrict str, char** restrict str_end );// (C99 起)
long double strtold( const char* restrict str, char** restrict str_end );// (3)(C99 起)
```

​	转译 `str` 所指向的字节字符串中的浮点数。

​	函数会舍弃任何空白符（由 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定），直至找到首个非空白符。然后它会取用尽可能多的字符，以构成合法的浮点数表示，并将它们转换成浮点值。合法的浮点值可以为下列之一：

- 十进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - 非空的十进制数字序列，可选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `e` 或 `E`，并跟随可选的正或负号，以及非空十进制数字序列（以 *10* 为底定义指数）



- 十六进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - `0x` 或 `0X`
  - 非空的十六进制数字序列，选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `p` 或 `P`，并跟随可选的正或负号，以及非空十进制数字序列（以 *2* 为底定义指数）

- 无穷大表达式。它由下列部分组成：

  - (可选) 正或负号
  - `INF` 或 `INFINITY`，忽略大小写

- 非数（NaN）表达式。它由下列部分组成：

  - (可选) 正或负号
  - `NAN` 或 `**NAN(**`*char_sequence* ﻿`**)**`，忽略 `NAN` 部分的大小写。 *char_sequence* 只能由数字、拉丁字母和下划线构成。结果是一个静态的 NaN 浮点值。

(C99 起)



- 任何其他可由当前 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)接受的表达式。

​	函数设置 `str_end` 所指向的指针指向最后被转译字符的后一字符，若 `str_end` 为空指针，则忽略它。

**参数**

| str     | -    | 指向要转译的空终止字节字符串的指针 |
| ------- | ---- | ---------------------------------- |
| str_end | -    | 指向指向字符指针的指针             |

**返回值**

​	成功时为对应 `str` 内容的浮点数。若转换出的值落在对应返回类型的范围外，则发生值域错误（将 [errno](https://zh.cppreference.com/w/c/error/errno) 设为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、[HUGE_VALF](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL) 或 [HUGE_VALL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)。若无法进行转换，则返回 `0` 并将 `*str_end` 设为 `str`。

**示例**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 带错误处理的解析
    const char* p = "111.11 -2.22 Nan nan(2) inF 0X1.BC70A3D70A3D7P+6  1.18973e+4932zzz";
    printf("Parsing '%s':\n", p);
    char* end = NULL;
    for (double f = strtod(p, &end); p != end; f = strtod(p, &end))
    {
        printf("'%.*s' -> ", (int)(end - p), p);
        p = end;
        if (errno == ERANGE)
        {
            printf("range error, got ");
            errno = 0;
        }
        printf("%f\n", f);
    }
 
    // 无错误处理的解析
    printf("\"  -0.0000000123junk\"  -->  %g\n", strtod("  -0.0000000123junk", NULL));
    printf("\"junk\"                 -->  %g\n", strtod("junk", NULL));
}
```

​	可能的输出：

```txt
Parsing '111.11 -2.22 Nan inF 0X1.BC70A3D70A3D7P+6  1.18973e+4932zzz':
'111.11' -> 111.110000
' -2.22' -> -2.220000
' Nan' -> nan
' nan(2)' -> nan
' inF' -> inf
' 0X1.BC70A3D70A3D7P+6' -> 111.110000
'  1.18973e+4932' -> range error, got inf
"  -0.0000000123junk"  -->  -1.23e-08
"junk"                 -->  0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 249-251 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 342-344 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.3 The strtod, strtof, and strtold functions （第 308-310 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.4 The strtod function

**参阅**

| [atof<br />](https://zh.cppreference.com/w/c/string/byte/atof) | 将字节字符串转换成浮点数 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| [wcstof (C99)<br />wcstod (C99)<br />wcstold (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstof) | 转换宽字符串为浮点数 (函数)     |
| **strtof, strtod, strtold** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtof)** |                                 |





### strtod128

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_DFP__`：






### strtod32

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_DFP__`：






### strtod64

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_DFP__`：






### strtodN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtodNx

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtoencbindN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtoencdecdN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtoencfN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtof

原址：[http://zh.cppreference.com/w/c/string/byte/strtof](http://zh.cppreference.com/w/c/string/byte/strtof)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
float       strtof ( const char* restrict str, char** restrict str_end );// (1)(C99 起)
// (2)
double      strtod ( const char*          str, char**          str_end );// (C99 前)
double      strtod ( const char* restrict str, char** restrict str_end );// (C99 起)
long double strtold( const char* restrict str, char** restrict str_end );// (3)(C99 起)
```

​	转译 `str` 所指向的字节字符串中的浮点数。

​	函数会舍弃任何空白符（由 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定），直至找到首个非空白符。然后它会取用尽可能多的字符，以构成合法的浮点数表示，并将它们转换成浮点值。合法的浮点值可以为下列之一：

- 十进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - 非空的十进制数字序列，可选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `e` 或 `E`，并跟随可选的正或负号，以及非空十进制数字序列（以 *10* 为底定义指数）



- 十六进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - `0x` 或 `0X`
  - 非空的十六进制数字序列，选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `p` 或 `P`，并跟随可选的正或负号，以及非空十进制数字序列（以 *2* 为底定义指数）

- 无穷大表达式。它由下列部分组成：

  - (可选) 正或负号
  - `INF` 或 `INFINITY`，忽略大小写

- 非数（NaN）表达式。它由下列部分组成：

  - (可选) 正或负号
  - `NAN` 或 `**NAN(**`*char_sequence* ﻿`**)**`，忽略 `NAN` 部分的大小写。 *char_sequence* 只能由数字、拉丁字母和下划线构成。结果是一个静态的 NaN 浮点值。

(C99 起)



- 任何其他可由当前 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)接受的表达式。

​	函数设置 `str_end` 所指向的指针指向最后被转译字符的后一字符，若 `str_end` 为空指针，则忽略它。

**参数**

| str     | -    | 指向要转译的空终止字节字符串的指针 |
| ------- | ---- | ---------------------------------- |
| str_end | -    | 指向指向字符指针的指针             |

**返回值**

​	成功时为对应 `str` 内容的浮点数。若转换出的值落在对应返回类型的范围外，则发生值域错误（将 [errno](https://zh.cppreference.com/w/c/error/errno) 设为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、[HUGE_VALF](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL) 或 [HUGE_VALL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)。若无法进行转换，则返回 `0` 并将 `*str_end` 设为 `str`。

**示例**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 带错误处理的解析
    const char* p = "111.11 -2.22 Nan nan(2) inF 0X1.BC70A3D70A3D7P+6  1.18973e+4932zzz";
    printf("Parsing '%s':\n", p);
    char* end = NULL;
    for (double f = strtod(p, &end); p != end; f = strtod(p, &end))
    {
        printf("'%.*s' -> ", (int)(end - p), p);
        p = end;
        if (errno == ERANGE)
        {
            printf("range error, got ");
            errno = 0;
        }
        printf("%f\n", f);
    }
 
    // 无错误处理的解析
    printf("\"  -0.0000000123junk\"  -->  %g\n", strtod("  -0.0000000123junk", NULL));
    printf("\"junk\"                 -->  %g\n", strtod("junk", NULL));
}
```

​	可能的输出：

```txt
Parsing '111.11 -2.22 Nan inF 0X1.BC70A3D70A3D7P+6  1.18973e+4932zzz':
'111.11' -> 111.110000
' -2.22' -> -2.220000
' Nan' -> nan
' nan(2)' -> nan
' inF' -> inf
' 0X1.BC70A3D70A3D7P+6' -> 111.110000
'  1.18973e+4932' -> range error, got inf
"  -0.0000000123junk"  -->  -1.23e-08
"junk"                 -->  0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 249-251 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 342-344 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.3 The strtod, strtof, and strtold functions （第 308-310 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.4 The strtod function

**参阅**

| [atof<br />](https://zh.cppreference.com/w/c/string/byte/atof) | 将字节字符串转换成浮点数 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| [wcstof (C99)<br />wcstod (C99)<br />wcstold (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstof) | 转换宽字符串为浮点数 (函数)     |
| **strtof, strtod, strtold** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtof)** |                                 |





### strtofN

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtofNx

原址：

作用：

备注：仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 stdlib.h 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：






### strtol

原址：[http://zh.cppreference.com/w/c/string/byte/strtol](http://zh.cppreference.com/w/c/string/byte/strtol)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
long      strtol( const char*          str, char**          str_end, int base );// (C99 前)
long      strtol( const char* restrict str, char** restrict str_end, int base );// (C99 起)
long long strtoll( const char* restrict str, char** restrict str_end, int base );// (C99 起)
```

​	转换 `str` 所指的字节字符串中的整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的整数表示，并将它们转换成一个整数。合法的整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)。

​	函数设置 `str_end` 所指向的指针指向最后被转换字符的后一字符。若 `str_end` 为空指针，则忽略它。

​	若 `str` 为空或无期待的形式，则不进行转换，并（若 `str_end` 不是空指针）将 `str` 的值存储于 `str_end` 所指的对象。

**参数**

| str     | -    | 指向要被转换的空终止字符串的指针 |
| ------- | ---- | -------------------------------- |
| str_end | -    | 指向指向字符指针的指针           |
| base    | -    | 被转换整数的*底*                 |

**返回值**

- 若成功，则返回对应 `str` 内容的整数。
- 若被转换值落在对应返回类型的范围外，则发生值域错误（设 [errno](https://zh.cppreference.com/w/c/error/errno) 为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [LONG_MAX](https://zh.cppreference.com/w/c/types/limits)、[LONG_MIN](https://zh.cppreference.com/w/c/types/limits)、[LLONG_MAX](https://zh.cppreference.com/w/c/types/limits) 或 [LLONG_MIN](https://zh.cppreference.com/w/c/types/limits)。
- 若无法进行转换，则返回 `0`。

**示例**

```c
#include <errno.h>
#include <limits.h>
#include <stdbool.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 带错误处理的剖析
    const char* p = "10 200000000000000000000000000000 30 -40 junk";
    printf("分析 '%s':\n", p);
 
    for (;;)
    {
        // 库函数调用能设置 errno 为任何非零值，无关乎是否有错误，
        // 故为检查 strtol 设置的错误，需要清除它
        errno = 0;
        char* end;
        const long i = strtol(p, &end, 10);
        if (p == end)
            break;
 
        const bool range_error = errno == ERANGE;
        printf("提取到 '%.*s', strtol 返回 %ld.", (int)(end-p), p, i);
        p = end;
 
        if (range_error)
            printf("\n --> 发生值域错误。");
 
        putchar('\n');
    }
 
    printf("剩余未提取：'%s'\n\n", p);
 
    // 不带错误处理的剖析
    printf("\"1010\" 按二进制    --> %ld\n", strtol("1010", NULL, 2));
    printf("\"12\"   按八进制    --> %ld\n", strtol("12",   NULL, 8));
    printf("\"A\"    按十六进制  --> %ld\n", strtol("A",    NULL, 16));
    printf("\"junk\" 按 36 进制  --> %ld\n", strtol("junk", NULL, 36));
    printf("\"012\"  自动检测基数 --> %ld\n", strtol("012",  NULL, 0));
    printf("\"0xA\"  自动检测基数 --> %ld\n", strtol("0xA",  NULL, 0));
    printf("\"junk\" 自动检测基数 --> %ld\n", strtol("junk", NULL, 0));
}
```

​	可能的输出：

```txt
分析 '10 200000000000000000000000000000 30 -40 junk':
提取到 '10', strtol 返回 10.
提取到 ' 200000000000000000000000000000', strtol 返回 9223372036854775807.
 --> 发生值域错误。
提取到 ' 30', strtol 返回 30.
提取到 ' -40', strtol 返回 -40.
剩余未提取：' junk'
 
"1010" 按二进制    --> 10
"12"   按八进制    --> 10
"A"    按十六进制  --> 10
"junk" 按 36 进制  --> 926192
"012"  自动检测基数 --> 10
"0xA"  自动检测基数 --> 10
"junk" 自动检测基数 --> 0
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 251-252 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 344-345 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 310-311 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.5 The strtol function

**参阅**

| [atoi <br />atol <br />atoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/atoi) | 将字节字符串转换成整数 (函数)       |
| ------------------------------------------------------------ | ----------------------------------- |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数) |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)           |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)     |
| **strtol, strtoll** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtol)** |                                     |





### strtold

原址：[http://zh.cppreference.com/w/c/string/byte/strtof](http://zh.cppreference.com/w/c/string/byte/strtof)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
float       strtof ( const char* restrict str, char** restrict str_end );// (1)(C99 起)
// (2)
double      strtod ( const char*          str, char**          str_end );// (C99 前)
double      strtod ( const char* restrict str, char** restrict str_end );// (C99 起)
long double strtold( const char* restrict str, char** restrict str_end );// (3)(C99 起)
```

​	转译 `str` 所指向的字节字符串中的浮点数。

​	函数会舍弃任何空白符（由 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定），直至找到首个非空白符。然后它会取用尽可能多的字符，以构成合法的浮点数表示，并将它们转换成浮点值。合法的浮点值可以为下列之一：

- 十进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - 非空的十进制数字序列，可选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `e` 或 `E`，并跟随可选的正或负号，以及非空十进制数字序列（以 *10* 为底定义指数）



- 十六进制浮点数表达式。它由下列部分组成：

  - (可选) 正或负号
  - `0x` 或 `0X`
  - 非空的十六进制数字序列，选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `p` 或 `P`，并跟随可选的正或负号，以及非空十进制数字序列（以 *2* 为底定义指数）

- 无穷大表达式。它由下列部分组成：

  - (可选) 正或负号
  - `INF` 或 `INFINITY`，忽略大小写

- 非数（NaN）表达式。它由下列部分组成：

  - (可选) 正或负号
  - `NAN` 或 `**NAN(**`*char_sequence* ﻿`**)**`，忽略 `NAN` 部分的大小写。 *char_sequence* 只能由数字、拉丁字母和下划线构成。结果是一个静态的 NaN 浮点值。

(C99 起)



- 任何其他可由当前 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)接受的表达式。

​	函数设置 `str_end` 所指向的指针指向最后被转译字符的后一字符，若 `str_end` 为空指针，则忽略它。

**参数**

| str     | -    | 指向要转译的空终止字节字符串的指针 |
| ------- | ---- | ---------------------------------- |
| str_end | -    | 指向指向字符指针的指针             |

**返回值**

​	成功时为对应 `str` 内容的浮点数。若转换出的值落在对应返回类型的范围外，则发生值域错误（将 [errno](https://zh.cppreference.com/w/c/error/errno) 设为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、[HUGE_VALF](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL) 或 [HUGE_VALL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)。若无法进行转换，则返回 `0` 并将 `*str_end` 设为 `str`。

**示例**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 带错误处理的解析
    const char* p = "111.11 -2.22 Nan nan(2) inF 0X1.BC70A3D70A3D7P+6  1.18973e+4932zzz";
    printf("Parsing '%s':\n", p);
    char* end = NULL;
    for (double f = strtod(p, &end); p != end; f = strtod(p, &end))
    {
        printf("'%.*s' -> ", (int)(end - p), p);
        p = end;
        if (errno == ERANGE)
        {
            printf("range error, got ");
            errno = 0;
        }
        printf("%f\n", f);
    }
 
    // 无错误处理的解析
    printf("\"  -0.0000000123junk\"  -->  %g\n", strtod("  -0.0000000123junk", NULL));
    printf("\"junk\"                 -->  %g\n", strtod("junk", NULL));
}
```

​	可能的输出：

```txt
Parsing '111.11 -2.22 Nan inF 0X1.BC70A3D70A3D7P+6  1.18973e+4932zzz':
'111.11' -> 111.110000
' -2.22' -> -2.220000
' Nan' -> nan
' nan(2)' -> nan
' inF' -> inf
' 0X1.BC70A3D70A3D7P+6' -> 111.110000
'  1.18973e+4932' -> range error, got inf
"  -0.0000000123junk"  -->  -1.23e-08
"junk"                 -->  0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 249-251 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.3 The strtod, strtof, and strtold functions （第 342-344 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.3 The strtod, strtof, and strtold functions （第 308-310 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.4 The strtod function

**参阅**

| [atof<br />](https://zh.cppreference.com/w/c/string/byte/atof) | 将字节字符串转换成浮点数 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| [wcstof (C99)<br />wcstod (C99)<br />wcstold (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstof) | 转换宽字符串为浮点数 (函数)     |
| **strtof, strtod, strtold** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtof)** |                                 |





### strtoll

原址：[http://zh.cppreference.com/w/c/string/byte/strtol](http://zh.cppreference.com/w/c/string/byte/strtol)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
long      strtol( const char*          str, char**          str_end, int base );// (C99 前)
long      strtol( const char* restrict str, char** restrict str_end, int base );// (C99 起)
long long strtoll( const char* restrict str, char** restrict str_end, int base );// (C99 起)
```

​	转换 `str` 所指的字节字符串中的整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的整数表示，并将它们转换成一个整数。合法的整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)。

​	函数设置 `str_end` 所指向的指针指向最后被转换字符的后一字符。若 `str_end` 为空指针，则忽略它。

​	若 `str` 为空或无期待的形式，则不进行转换，并（若 `str_end` 不是空指针）将 `str` 的值存储于 `str_end` 所指的对象。

**参数**

| str     | -    | 指向要被转换的空终止字符串的指针 |
| ------- | ---- | -------------------------------- |
| str_end | -    | 指向指向字符指针的指针           |
| base    | -    | 被转换整数的*底*                 |

**返回值**

- 若成功，则返回对应 `str` 内容的整数。
- 若被转换值落在对应返回类型的范围外，则发生值域错误（设 [errno](https://zh.cppreference.com/w/c/error/errno) 为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [LONG_MAX](https://zh.cppreference.com/w/c/types/limits)、[LONG_MIN](https://zh.cppreference.com/w/c/types/limits)、[LLONG_MAX](https://zh.cppreference.com/w/c/types/limits) 或 [LLONG_MIN](https://zh.cppreference.com/w/c/types/limits)。
- 若无法进行转换，则返回 `0`。

**示例**

```c
#include <errno.h>
#include <limits.h>
#include <stdbool.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 带错误处理的剖析
    const char* p = "10 200000000000000000000000000000 30 -40 junk";
    printf("分析 '%s':\n", p);
 
    for (;;)
    {
        // 库函数调用能设置 errno 为任何非零值，无关乎是否有错误，
        // 故为检查 strtol 设置的错误，需要清除它
        errno = 0;
        char* end;
        const long i = strtol(p, &end, 10);
        if (p == end)
            break;
 
        const bool range_error = errno == ERANGE;
        printf("提取到 '%.*s', strtol 返回 %ld.", (int)(end-p), p, i);
        p = end;
 
        if (range_error)
            printf("\n --> 发生值域错误。");
 
        putchar('\n');
    }
 
    printf("剩余未提取：'%s'\n\n", p);
 
    // 不带错误处理的剖析
    printf("\"1010\" 按二进制    --> %ld\n", strtol("1010", NULL, 2));
    printf("\"12\"   按八进制    --> %ld\n", strtol("12",   NULL, 8));
    printf("\"A\"    按十六进制  --> %ld\n", strtol("A",    NULL, 16));
    printf("\"junk\" 按 36 进制  --> %ld\n", strtol("junk", NULL, 36));
    printf("\"012\"  自动检测基数 --> %ld\n", strtol("012",  NULL, 0));
    printf("\"0xA\"  自动检测基数 --> %ld\n", strtol("0xA",  NULL, 0));
    printf("\"junk\" 自动检测基数 --> %ld\n", strtol("junk", NULL, 0));
}
```

​	可能的输出：

```txt
分析 '10 200000000000000000000000000000 30 -40 junk':
提取到 '10', strtol 返回 10.
提取到 ' 200000000000000000000000000000', strtol 返回 9223372036854775807.
 --> 发生值域错误。
提取到 ' 30', strtol 返回 30.
提取到 ' -40', strtol 返回 -40.
剩余未提取：' junk'
 
"1010" 按二进制    --> 10
"12"   按八进制    --> 10
"A"    按十六进制  --> 10
"junk" 按 36 进制  --> 926192
"012"  自动检测基数 --> 10
"0xA"  自动检测基数 --> 10
"junk" 自动检测基数 --> 0
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 251-252 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 344-345 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 310-311 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.5 The strtol function

**参阅**

| [atoi <br />atol <br />atoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/atoi) | 将字节字符串转换成整数 (函数)       |
| ------------------------------------------------------------ | ----------------------------------- |
| [strtoul <br />strtoull (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtoul) | 将字节字符串转换成无符号整数 (函数) |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)           |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)     |
| **strtol, strtoll** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtol)** |                                     |





### strtoul

原址：[http://zh.cppreference.com/w/c/string/byte/strtoul](http://zh.cppreference.com/w/c/string/byte/strtoul)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
unsigned long      strtoul( const char*          str, char**          str_end,
                            int base );// (C99 前)
unsigned long      strtoul( const char* restrict str, char** restrict str_end,
                            int base );// (C99 起)
unsigned long long strtoull( const char* restrict str, char** restrict str_end,
                             int base );// (C99 起)
```

​	转换 `str` 所指的字符串中的无符号整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的无符号整数表示，并将它们转换成一个整数。合法的无符号整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)，它对无符号整数应用回绕规则。

​	函数设置 `str_end` 所指向的指针指向最后一个被转换字符的后一字符。若 `str_end` 为空指针，则忽略它。

**参数**

| str     | -    | 指向要被转换的空终止字符串的指针 |
| ------- | ---- | -------------------------------- |
| str_end | -    | 指向指向字符的指针的指针         |
| base    | -    | 被转换整数的*底*                 |

**返回值**

​	成功时为对应 `str` 内容的整数。若被转换值落在对应返回类型的范围外，则发生值域错误（[errno](https://zh.cppreference.com/w/c/error/errno) 被设为 `ERANGE`）并返回 [ULONG_MAX](https://zh.cppreference.com/w/c/types/limits) 或 [ULLONG_MAX](https://zh.cppreference.com/w/c/types/limits)。若无转换可进行，则返回 `0`。

**示例**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char* p = "10 200000000000000000000000000000 30 -40 - 42";
    printf("解析 '%s':\n", p);
    char* end = NULL;
    for (unsigned long i = strtoul(p, &end, 10);
         p != end;
         i = strtoul(p, &end, 10))
    {
        printf("'%.*s' -> ", (int)(end - p), p);
        p = end;
        if (errno == ERANGE)
        {
            errno = 0;
            printf("值域错误，得到 ");
        }
        printf("%lu\n", i);
    }
    printf("循环后 p 指向 '%s'\n", p);
}
```

​	输出：

```txt
解析 '10 200000000000000000000000000000 30 -40 - 42':
'10' -> 10
' 200000000000000000000000000000' -> 值域错误，得到 18446744073709551615
' 30' -> 30
' -40' -> 18446744073709551576
循环后 p 指向 ' - 42'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.1.7 The strtol, strtoll, strtoul, and strtoull functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 251-252 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 344-345 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 310-311 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.6 The strtoul function

**参阅**

| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| [atoi <br />atol <br />atoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/atoi) | 将字节字符串转换成整数 (函数)   |
| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)   |
| **strtoul** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtoul)** |                                 |





### strtoull

原址：[http://zh.cppreference.com/w/c/string/byte/strtoul](http://zh.cppreference.com/w/c/string/byte/strtoul)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
unsigned long      strtoul( const char*          str, char**          str_end,
                            int base );// (C99 前)
unsigned long      strtoul( const char* restrict str, char** restrict str_end,
                            int base );// (C99 起)
unsigned long long strtoull( const char* restrict str, char** restrict str_end,
                             int base );// (C99 起)
```

​	转换 `str` 所指的字符串中的无符号整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的无符号整数表示，并将它们转换成一个整数。合法的无符号整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 `8` 或 `0` 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 `16` 或 `0` 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 `0`，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)，它对无符号整数应用回绕规则。

​	函数设置 `str_end` 所指向的指针指向最后一个被转换字符的后一字符。若 `str_end` 为空指针，则忽略它。

**参数**

| str     | -    | 指向要被转换的空终止字符串的指针 |
| ------- | ---- | -------------------------------- |
| str_end | -    | 指向指向字符的指针的指针         |
| base    | -    | 被转换整数的*底*                 |

**返回值**

​	成功时为对应 `str` 内容的整数。若被转换值落在对应返回类型的范围外，则发生值域错误（[errno](https://zh.cppreference.com/w/c/error/errno) 被设为 `ERANGE`）并返回 [ULONG_MAX](https://zh.cppreference.com/w/c/types/limits) 或 [ULLONG_MAX](https://zh.cppreference.com/w/c/types/limits)。若无转换可进行，则返回 `0`。

**示例**

```c
#include <errno.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char* p = "10 200000000000000000000000000000 30 -40 - 42";
    printf("解析 '%s':\n", p);
    char* end = NULL;
    for (unsigned long i = strtoul(p, &end, 10);
         p != end;
         i = strtoul(p, &end, 10))
    {
        printf("'%.*s' -> ", (int)(end - p), p);
        p = end;
        if (errno == ERANGE)
        {
            errno = 0;
            printf("值域错误，得到 ");
        }
        printf("%lu\n", i);
    }
    printf("循环后 p 指向 '%s'\n", p);
}
```

​	输出：

```txt
解析 '10 200000000000000000000000000000 30 -40 - 42':
'10' -> 10
' 200000000000000000000000000000' -> 值域错误，得到 18446744073709551615
' 30' -> 30
' -40' -> 18446744073709551576
循环后 p 指向 ' - 42'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.1.7 The strtol, strtoll, strtoul, and strtoull functions （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 251-252 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 344-345 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.1.4 The strtol, strtoll, strtoul, and strtoull functions （第 310-311 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.1.6 The strtoul function

**参阅**

| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数) |
| ------------------------------------------------------------ | ------------------------------- |
| [atoi <br />atol <br />atoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/atoi) | 将字节字符串转换成整数 (函数)   |
| [strtol <br />strtoll (C99)<br />](https://zh.cppreference.com/w/c/string/byte/strtol) | 将字节字符串转换成整数 (函数)   |
| **strtoul** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtoul)** |                                 |





### system

原址：[http://zh.cppreference.com/w/c/program/system](http://zh.cppreference.com/w/c/program/system)

作用：

备注：
```c
// 在标头 <stdlib.h> 定义
int system( const char *command );
```

​	以参数 `command` 调用宿主环境的命令处理器。返回实现定义值（通常是被调用程序所返回的值）。

​	若 `command` 是空指针，则检查宿主环境是否有命令处理器，并若且仅若命令处理器存在才返回非零。

**参数**

| command | -    | 标识要运行于命令处理器的命令的字符串。若给出空指针，则检查其存在性 |
| ------- | ---- | ------------------------------------------------------------ |
|         |      |                                                              |

**返回值**

​	实现定义值。若 `command` 为空指针，则当且仅当命令处理器存在才返回非零值。

**注意**

​	POSIX 系统上，可用 [`WEXITSTATUS` 和 `WSTOPSIG`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/wait.html) 分解返回值。

​	相关的 POSIX 函数 [popen](http://pubs.opengroup.org/onlinepubs/9699919799/functions/popen.html) 令 `command` 生成的输出对调用方可用。

**示例**

​	此示例中有 unix 命令 **date +%A** 的系统调用，以及（可能安装的）**gcc** 编译器附带命令行参数（*--version*）的系统调用：

```c
#include <stdlib.h>
 
int main(void) {
    system("date +%A");
    system("gcc --version");
}
```

​	可能的输出：

```txt
Wednesday
gcc (GCC) 11.2.0
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.4.8 The system function （第 257 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.4.8 The system function （第 353-354 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.4.6 The system function （第 317 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.4.5 The system function

**参阅**

**system** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/utility/program/system)**





### wcstombs

原址：[http://zh.cppreference.com/w/c/string/multibyte/wcstombs](http://zh.cppreference.com/w/c/string/multibyte/wcstombs)

作用：

备注：

```c
// 在标头 <stdlib.h> 定义
// (1)
size_t wcstombs( char          *dst, const wchar_t          *src, size_t len );// (C99 前)
size_t wcstombs( char *restrict dst, const wchar_t *restrict src, size_t len );// (C99 起)
errno_t wcstombs_s( size_t *restrict retval, char *restrict dst, rsize_t dstsz,
                    const wchar_t *restrict src, rsize_t len );// (2)(C11 起)
```

1） 将来自首元素为 `src` 所指向的数组中的宽字符序列为其窄多字节表示，其始于初始迁移状态。转换出的各字符被存储于 `dst` 所指向的数组的相继元素。写入目标数组的字节数不多于 `len`。

 如同以调用 [wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb) 来转换每个字符，但 wctomb 的转换状态不受影响。若满足下列条件则转换停止：

 \* 转换并存储空字符 `L'\0'`。此情况下存储的各字节为无迁移序列（若需要）后随 `'\0'`，

 \* 找到当前 C 本地环境中不对应合法字符的 `wchar_t`。

 \* 下个要存储的多字节字符会超出 `len`。

 若 `src` 与 `dst` 重叠，则行为未指定。

2） 同 (1)，但

 \* 转换如同以 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb) 而非 [wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb) 进行

 \* 函数将其结果作为输出参数 `retval` 返回

 \* 若转换停止而不写入控制符，则函数将在 `dst` 中的下个字符，可以是 `dst[len]` 或 `dst[dstsz]` 的先到来者，存储 `'\0'`（表示可能写入总计至多 len+1/dsz+1 个字符）。该情况下，空终止前不写入无迁移序列。

 \* 若 `dst` 是空指针，则将本会产生的字节数存储于 `*retval`

 \* 函数从空终止起到 `dstsz` 前为止破坏目标数组

 \* 若 `src` 与 `dst` 重叠，则行为未指定。

 \* 在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `retval` 或 `src` 是空指针
  - `dstsz` 或 `len` 大于 RSIZE_MAX（除非 `dst` 为空）
  - `dstsz` 非零（除非 `dst` 为空）
  - `len` 大于 `dstsz` 且直到抵达 `dstsz` 时，转换未于 `src` 数组遇到空字符或编码错误（除非 `dst` 为空）

**注意**

​	大多数实现中，`wcstombs` 在处理过字符串时更新 [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的全局静态对象，因而不能被两个线程同时调用，这种情况下应使用 [wcsrtombs](https://zh.cppreference.com/w/c/string/multibyte/wcsrtombs) 或 `wcstombs_s`。

​	POSIX 指定一个常见扩展：若 `dst` 是空指针，则此函数返回假设转换则会写入 `dst` 的字节数。类似行为对于 [wcsrtombs](https://zh.cppreference.com/w/c/string/multibyte/wcsrtombs) 和 `wcstombs_s` 是标准。

**参数**

| dst    | -    | 指向窄字符数组的指针，其中将存储多字节字符 |
| ------ | ---- | ------------------------------------------ |
| src    | -    | 指向要转换的空终止宽字符串首字符的指针     |
| len    | -    | dst 所指向数组中的可用字节数               |
| dstsz  | -    | 将写入的最大字节数（`dst` 数组的大小）     |
| retval | -    | 指向 size_t 对象的指针，其中将存储结果     |

**返回值**

1） 成功时，返回写入首元素为 `dst` 所指向的字符数组的字节数（包含任何迁移序列，但不含终止的 `'\0'`）。转换错误时（若遇到非法宽字符），返回 `([size_t](http://zh.cppreference.com/w/c/types/size_t))-1`。

2） 成功时返回零（该情况下，将被或本应写入 `dst` 的字节数，排除终止零，存储于 `*retval`），错误时返回非零。运行时制约违规的情况下，存储 `([size_t](http://zh.cppreference.com/w/c/types/size_t))-1` 于 `*retval`（除非 `retval` 为空）并设置 `dst[0]` 为 `'\0'`（除非 `dst` 为空或 `dstmax` 为零或大于 RSIZE_MAX）。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
 
int main(void)
{
    // 4 个宽字符
    const wchar_t src[] = L"z\u00df\u6c34\U0001f34c";
    // 它们于 UTF-8 占用 10 个字节
    char dst[11];
 
    setlocale(LC_ALL, "en_US.utf8");
    printf("宽字符字符串：'%ls'\n",src);
    for (size_t ndx=0; ndx < sizeof src/sizeof src[0]; ++ndx)
        printf("   src[%2zu] = %#8x\n", ndx, src[ndx]);
 
    int rtn_val = wcstombs(dst, src, sizeof dst);
    printf("rtn_val = %d\n", rtn_val);
    if (rtn_val > 0)
        printf("多字节字符串：'%s'\n", dst);
    for (size_t ndx=0; ndx<sizeof dst; ++ndx)
        printf("   dst[%2zu] = %#2x\n", ndx, (unsigned char)dst[ndx]);
}
```

​	输出：

```txt
宽字符字符串：'zß水🍌'
   src[ 0] =     0x7a
   src[ 1] =     0xdf
   src[ 2] =   0x6c34
   src[ 3] =  0x1f34c
   src[ 4] =        0
rtn_val = 10
多字节字符串：'zß水🍌'
   dst[ 0] = 0x7a
   dst[ 1] = 0xc3
   dst[ 2] = 0x9f
   dst[ 3] = 0xe6
   dst[ 4] = 0xb0
   dst[ 5] = 0xb4
   dst[ 6] = 0xf0
   dst[ 7] = 0x9f
   dst[ 8] = 0x8d
   dst[ 9] = 0x8c
   dst[10] =  0
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.8.2 The wcstombs function （第 360 页）

  - K.3.6.5.2 The wcstombs_s function （第 612-614 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.8.2 The wcstombs function （第 324 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.8.2 The wcstombs function

**参阅**

| [wcsrtombs (C95)<br />wcsrtombs_s (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/wcsrtombs) | 给定状态，转换宽字符串为窄多字节字符串 (函数) |
| ------------------------------------------------------------ | --------------------------------------------- |
| [mbstowcs <br />mbstowcs_s (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbstowcs) | 转换窄多字节字符串为宽字符串 (函数)           |
| **wcstombs** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte/wcstombs)** |                                               |



### wcstombs_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






### wctomb

原址：[http://zh.cppreference.com/w/c/string/multibyte/wctomb](http://zh.cppreference.com/w/c/string/multibyte/wctomb)

作用：

备注：

```c
// 在标头 <stdlib.h> 定义
int wctomb( char *s, wchar_t wc );// (1)
errno_t wctomb_s(int *restrict status, char *restrict s, rsize_t ssz, wchar_t wc);// (2)(C11 起)
```

1） 转换宽字符 `wc` 为多字节编码，并将之（含迁移状态）存储于 `s` 指向其首元素的字符数组。存储字节数不多于 `MB_CUR_MAX`。转换受到当前安装的本地环境的 LC_CTYPE 类别的影响。

 若 `wc` 是空字符，则将空字符写入 `s`，之前可以有需要恢复初始迁移状态的任何迁移状态。

 若 `s` 是空指针，则此函数重设全局转换状态并确定是否使用迁移序列。

2） 同 (1)，除了结果被返回到输出参数 `status`，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `ssz` 小于会被写入的字节数（除非 `s` 为空）
  - `ssz` 大于 RSIZE_MAX（除非 `s` 为空）
  - `s` 为空指针但 `ssz` 非零

**注意**

​	每次对 `wctomb` 的调用会更新全局转换状态（[mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的静态对象，只为此函数所知）。若多字节编码使用迁移状态，则此函数不可重入。任何情况下，多个线程不应调用 `wctomb` 而不同步：可使用 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb) 或 `wctomb_s` 代替。

​	不同于大多数边界检查函数，`wctomb_s` 不以空字符终止其输出，因为它被设计以用于逐字节处理的循环。

**参数**

| s      | -    | 指向输出用字符数组的指针                                     |
| ------ | ---- | ------------------------------------------------------------ |
| wc     | -    | 要转换的宽字符                                               |
| ssz    | -    | 要写入 `s` 的最大字节数（数组 `s` 的大小）                   |
| status | -    | 指向结果（多字节序列长度或迁移序列状态）存储位置的输出参数的指针 |

**返回值**

1） 若 `s` 非空指针，则返回 `wc` 的多字节表示所含的字节数，或者若 `wc` 非合法字符则为 `-1`。

 若 `s` 是空指针，则重设内部转换状态以表示初始迁移状态，并若当前多字节编码非状态依赖（不使用迁移序列）则返回 `0`，或者若当前多字节编码为状态依赖（使用迁移序列）则返回非零值。

2） 成功时为零，此情况下存储 `wc` 的多字节表示于 `s`，并存储其长度于 `*status`，或若 `s` 为空，则存储迁移序列状态于 `*status`。编码错误或运行时制约错误发生时为非零，此情况下存储 `([size_t](http://zh.cppreference.com/w/c/types/size_t))-1` 于 `*status`。存储于 `*status` 的值决不超过 MB_CUR_MAX。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
#include <locale.h>
 
void demo(wchar_t wc)
{
    const char* dep = wctomb(NULL, wc) ? "是" : "否";
    printf("状态依赖编码？%s。\n", dep);
 
    char mb[MB_CUR_MAX];
    int len = wctomb(mb, wc);
    printf("宽字符 '%lc' -> 多字节字符 [", wc);
    for (int idx = 0; idx < len; ++idx)
        printf("%s%#2x", idx ? " " : "", (unsigned char)mb[idx]);
    printf("]\n");
}
 
int main(void)
{
    setlocale(LC_ALL, "en_US.utf8");
    printf("MB_CUR_MAX = %zu\n", MB_CUR_MAX);
    demo(L'A');
    demo(L'\u00df');
    demo(L'\U0001d10b');
}
```

​	可能的输出：

```txt
MB_CUR_MAX = 6
状态依赖编码？否。
宽字符 'A' -> 多字节字符 [0x41]
状态依赖编码？否。
宽字符 'ß' -> 多字节字符 [0xc3 0x9f]
状态依赖编码？否。
宽字符 '𝄋' -> 多字节字符 [0xf0 0x9d 0x84 0x8b]
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.22.7.3 The wctomb function （第 261 页）

  - K.3.6.4.1 The wctomb_s function （第 443 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.22.7.3 The wctomb function （第 358-359 页）

  - K.3.6.4.1 The wctomb_s function （第 610-611 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.20.7.3 The wctomb function （第 322-323 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.10.7.3 The wctomb function

**参阅**

| [mbtowc<br />](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) | 转换下一个多字节字符为宽字符 (函数)       |
| ------------------------------------------------------------ | ----------------------------------------- |
| [wcrtomb (C95)<br />wcrtomb_s (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb) | 给定状态，转换宽字符成其多字节表示 (函数) |
| **wctomb** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte/wctomb)** |                                           |



### wctomb_s

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 stdio.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：







