+++
title = "<stdlib.h>"
date = 2025-04-14T16:54:35+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false
math = true

+++

## 类型








### constraint_handler_t

原址：[https://zh.cppreference.com/w/c/error/set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)

```c
constraint_handler_t set_constraint_handler_s( constraint_handler_t handler ); // (1)	(C11 起)
typedef void (*constraint_handler_t)( const char *restrict msg,
                                      void *restrict ptr,
                                      errno_t error); // (2)	(C11 起)
```

​	参见：[set_constraint_handler_s 函数](#set_constraint_handler_s)








### size_t

原址：[https://zh.cppreference.com/w/c/types/size_t](https://zh.cppreference.com/w/c/types/size_t)

```c
typedef /* 由实现定义 */ size_t;
```

​	`size_t` 是 [offsetof](https://zh.cppreference.com/w/c/types/offsetof)、[`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 和 `_Alignof`(C23 前)`alignof`(C23 起) 的结果的无符号整数类型，定义取决于[数据模型](https://zh.cppreference.com/w/c/language/arithmetic_types#.E6.95.B0.E6.8D.AE.E6.A8.A1.E5.9E.8B)。

​	`size_t` 的位宽不小于 16。(C99 起)

**注解**

​	`size_t` 能存储理论上可行的任何类型（包括数组）对象的最大大小。

​	`size_t` 通常用于数组下标和循环计数。将如 unsigned int 的其他类型用作数组下标的的程序，可能譬如在 64 位系统上，当下标超过 [UINT_MAX](https://zh.cppreference.com/w/c/types/limits) 时，或若其依赖 32 位模算术时失败。

**可能的实现**

```c
typedef typeof(sizeof(0)) size_t; // C23 起合法
```

**示例**



```c
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    const size_t N = 101;
    int numbers[N];
    size_t sum = 0;
    for (size_t ndx = 0; ndx < N; ++ndx)
        sum += numbers[ndx] = ndx;
    size_t size = sizeof numbers;
    printf("sum = %zu\n", sum);
    printf("size = %zu\n", size);
    printf("SIZE_MAX = %zu\n", SIZE_MAX);
}
```

​	可能的输出：

```txt
sum = 5050
size = 400
SIZE_MAX = 18446744073709551615
```

## 宏








### EXIT_SUCCESS 

原址：[https://zh.cppreference.com/w/c/program/EXIT_status](https://zh.cppreference.com/w/c/program/EXIT_status)

```c
#define EXIT_SUCCESS /* 由实现定义 */
```




### EXIT_FAILURE 

原址：[https://zh.cppreference.com/w/c/program/EXIT_status](https://zh.cppreference.com/w/c/program/EXIT_status)

```c
#define EXIT_FAILURE /* 由实现定义 */
```

​	`EXIT_SUCCESS` 和 `EXIT_FAILURE` 宏展开成能用作 [exit](https://zh.cppreference.com/w/c/program/exit) 的实参的整数常量表达式（从而作为从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function) 返回的值），并指示程序执行状态。

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




### NULL

原址：[https://zh.cppreference.com/w/c/types/NULL](https://zh.cppreference.com/w/c/types/NULL)

```c
#define NULL /* 由实现定义 */
```

​	宏 `NULL` 是实现定义的空指针常量，可为

- 值为 0 的整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F)
- [转换为](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2) void* 的值为 0 的整数常量表达式

| 预定义常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr) | (C23 起) |
| ------------------------------------------------------------ | -------- |

​	空指针常量能[转换](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2)为任何指针类型；转换结果是该类型的空指针值。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/stddef.h.html) `NULL` 被定义为转换为 void* 的值为 0 的整数常量表达式。

**可能的实现**

```C
// 兼容 C++： #define NULL 0 // 不兼容 C++： #define NULL (10*2 - 20) #define NULL ((void*)0) // C23 起（与 C++11 及之后兼容） #define NULL nullptr
```

**示例**



```c
#include <inttypes.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    // 任何类型的指针均能设为 NULL
    int* p = NULL;
    struct S *s = NULL;
    void(*f)(int, double) = NULL;
    printf("%p %p %p\n", (void*)p, (void*)s, (void*)(long)f);
 
    // 多数返回指针的函数用空指针指示错误
    char *ptr = malloc(0xFULL);
    if (ptr == NULL)
        printf("Out of memory");
    else
        printf("ptr = %#" PRIxPTR"\n", (uintptr_t)ptr);
    free(ptr);
}
```

​	可能的输出：

```txt
(nil) (nil) (nil)
ptr = 0xc001cafe
```

## 函数








### _Exit

原址：[https://zh.cppreference.com/w/c/program/_Exit](https://zh.cppreference.com/w/c/program/_Exit)

```c
void _Exit( int exit_code ); // (C99 起)(C11 前)
_Noreturn void _Exit( int exit_code );// (C11 起)(C23 前)
[[noreturn]] void _Exit( int exit_code );// (C23 起)
```

​	导致发生程序正常终止，但不完全清理资源。

​	不调用传递给 [at_quick_exit()](https://zh.cppreference.com/w/c/program/at_quick_exit) 或 [atexit()](https://zh.cppreference.com/w/c/program/atexit) 的函数。是否将未写入数据冲入打开的流、关闭打开的流或移除临时文件是实现定义的。

​	若 `exit_code` 为 0 或 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status)，则将指示成功终止的状态返回给宿主环境。若 `exit_code` 为 [EXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示 *不成功* 终止的实现定义状态。其他情况下返回实现定义的状态值。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |

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

输出：

```txt
Enter main()
```




### abort 

原址：[https://zh.cppreference.com/w/c/program/abort](https://zh.cppreference.com/w/c/program/abort)

```c
void abort(void); // (C11 前)
_Noreturn void abort(void); // (C11 起) (C23 前)
[[noreturn]] void abort(void); // (C23 起)
```

​	导致程序异常终止，除非传递给 [signal](https://zh.cppreference.com/w/c/program/signal) 的信号处理函数正在捕捉 [SIGABRT](https://zh.cppreference.com/w/c/program/SIG_types) 且该处理函数不返回。

​	不调用传递给 [atexit()](https://zh.cppreference.com/w/c/program/atexit) 的函数。是否关闭打开的资源，例如文件，是实现定义的。向宿主环境返回指示不成功执行的实现定义状态。

**参数**

（无）

**返回值**

（无）

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




### abort_handler_s <- 11+

原址：[https://zh.cppreference.com/w/c/error/abort_handler_s](https://zh.cppreference.com/w/c/error/abort_handler_s)

```c
void abort_handler_s( const char * restrict msg,
                      void * restrict ptr,
                      errno_t error
                    ); // (C11 起)
```

​	向 [stderr](https://zh.cppreference.com/w/c/io) 写入实现定义的消息，其中必须包含 `msg` 所指向字符串，然后调用 [abort()](https://zh.cppreference.com/w/c/program/abort) 。

​	指向此函数的指针可以传递给 [set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s) 以建立运行时制约违规处理函数。

​	同所有边界检查函数， `abort_handler_s` 仅若实现定义了 `__STDC_LIB_EXT1__` ，且用户在包含 `<stdlib.h>` 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 `1` 才保证可用。

**参数**

| msg   | -    | 指向要写到标准错误输出的消息的指针                           |
| ----- | ---- | ------------------------------------------------------------ |
| ptr   | -    | 指向实现定义的对象的指针或空指针。实现定义对象的例子，是给出检测到违规的函数名和检测到违规时的行号的对象 |
| error | -    | `errno_t` 类型的正值                                         |

**返回值**

​	无；此函数不会返回到调用方

**注意**

​	若从未调用 `set_constraint_handler_s` ，则默认处理函数是实现定义的：可以为 abort_handler_s 、 ignore_handler_s 或另外的实现定义处理函数。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
#ifdef __STDC_LIB_EXT1__
    char dst[2];
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
    set_constraint_handler_s(abort_handler_s);
    r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

可能的输出：

```txt
dst = "", r = 22
abort_handler_s was called in response to a runtime-constraint violation.
 
The runtime-constraint violation was caused by the following expression in strcpy_s:
(s1max <= (s2_len=strnlen_s(s2, s1max)) ) (in string_s.c:62)
 
Note to end users: This program was terminated as a result
of a bug present in the software. Please reach out to your
software's vendor to get more help.
Aborted
```




### abs

原址：[https://zh.cppreference.com/w/c/numeric/math/abs](https://zh.cppreference.com/w/c/numeric/math/abs)

```c
int        abs( int n );
long       labs( long n );
long long llabs( long long n ); // (C99 起)
```

​	计算整数的绝对值。若返回类型无法表示结果，则行为未定义。

**参数**

| n    | -    | 整数值 |
| ---- | ---- | ------ |

**返回值**

​	n 的绝对值（即 `|n|`），若它能被表示。

**注解**

​	在补码系统中，最小负值的绝对值处于对应整数范围外，例如对于 32 位补码类型 int，[INT_MIN](https://zh.cppreference.com/w/c/types/limits) 为 -2147483648，但其绝对值应有的结果是 2147483648，大于 [INT_MAX](https://zh.cppreference.com/w/c/types/limits)（其值为 2147483647）。

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




### aligned_alloc <- 11+

原址：[https://zh.cppreference.com/w/c/memory/aligned_alloc](https://zh.cppreference.com/w/c/memory/aligned_alloc)

```c
void *aligned_alloc( size_t alignment, size_t size ); // (C11 起)
```

​	分配 `size` 个字节的未初始化存储空间，按照 `alignment` 指定对齐。`size` 形参必须是 `alignment` 的整数倍。

​	`aligned_alloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 `free_sized` 及 `free_aligned_sized`(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用 *同步于* 分配同一块或部分相同的内存区域的 `aligned_alloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `aligned_alloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。

**参数**

| alignment | -    | 指定对齐。必须是实现支持的合法对齐。 |
| --------- | ---- | ------------------------------------ |
| size      | -    | 分配的字节数。alignment 的整数倍。   |

**返回值**

​	成功时，返回指向新分配内存的指针。为避免内存泄漏，返回的指针必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 解分配。

​	失败时，返回空指针。

**注解**

​	传递不是 `alignment` 整数倍的 `size`，或传递实现不支持的 `alignment`，会令函数失败并返回空指针（出版时的 C11 指定此为未定义行为，这已经为 [DR460](https://open-std.org/JTC1/SC22/WG14/www/docs/summary.htm#dr_460) 所更正）。[N2072](https://open-std.org/JTC1/SC22/WG14/www/docs/n2072.htm) 提议移除大小限制，使之能在限制性的对齐边界分配小对象（类似 [`alignas`](https://zh.cppreference.com/w/c/language/_Alignas)）。

​	作为“实现支持”要求的例子，POSIX 函数 [`posix_memalign`](https://pubs.opengroup.org/onlinepubs/9699919799/functions/posix_memalign.html) 接受任何是二的幂且为 `sizeof(void*)` 倍数的 `alignment`，而基于 POSIX 的 `aligned_alloc` 实现继承了此项要求。

​	基础对齐始终得到支持。若 `alignment` 是二的幂且不大于 `_Alignof`([max_align_t](http://zh.cppreference.com/w/c/types/max_align_t))，则 `aligned_alloc` 可以简单地调用 [malloc](https://zh.cppreference.com/w/c/memory/malloc)。

​	常规的 [malloc](https://zh.cppreference.com/w/c/memory/malloc) 分配适用于具有任何基础对齐的对象类型的内存。`aligned_alloc` 适用于过对齐分配，例如对 [SSE](https://en.wikipedia.org/wiki/Streaming_SIMD_Extensions)、缓存线或 [VM 页](https://en.wikipedia.org/wiki/Page_(computer_memory)#Multiple_page_sizes)边界。

​	Microsoft C 运行时库不支持此函数，因为其 `std::free` 的实现 [无法处理任意种类的对齐分配](https://learn.microsoft.com/en-us/cpp/standard-library/cstdlib#remarks-6)。MS CRT 提供 [`_aligned_malloc`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/aligned-malloc) 作为替代（其结果应以 [`_aligned_free`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/aligned-free) 释放）。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    int *p1 = malloc(10*sizeof *p1);
    printf("default-aligned addr:   %p\n", (void*)p1);
    free(p1);
 
    int *p2 = aligned_alloc(1024, 1024*sizeof *p2);
    printf("1024-byte aligned addr: %p\n", (void*)p2);
    free(p2);
}
```

可能的输出：

```txt
default-aligned addr:   0x1e40c20
1024-byte aligned addr: 0x1e41000
```




### at_quick_exit <- 11+

原址：[https://zh.cppreference.com/w/c/program/at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit)

```c
int at_quick_exit( void (*func)(void) ); (C11 起)
```

​	注册 `func` 所指向的函数，使它在程序快速终止（通过 [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)）时得到调用。

​	`at_quick_exit` 是线程安全的：从多个线程调用此函数不会导入数据竞争。实现应当支持注册至少 32 个函数。确切的极限是由实现定义的。

​	所注册的函数在 [程序正常终止](https://zh.cppreference.com/w/c/program/exit) 时并不会被调用。如果需要函数在这种情况下被调用，必须使用 [atexit](https://zh.cppreference.com/w/c/program/atexit)。

**参数**

| func | -    | 指向要在程序快速终止调用的函数的指针 |
| ---- | ---- | ------------------------------------ |

**返回值**

若注册成功则为 0，否则为非零值。

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

输出：

```txt
pushed second
pushed first
```




### atexit

原址：[https://zh.cppreference.com/w/c/program/atexit](https://zh.cppreference.com/w/c/program/atexit)

```c
int atexit( void (*func)(void) );
```

​	注册 `func` 所指向的函数，使它在程序正常终止（通过 [exit()](https://zh.cppreference.com/w/c/program/exit) 或从 `main()` 返回）时得到调用。将以注册顺序的逆序调用这些函数，即首先执行最后调用的函数。

​	可以注册同一函数多于一次。

​	实现保证支持注册至少 32 个函数。确切的极限是由实现定义的。

**参数**

| func | -    | 指向要在程序正常终止时调用的函数的指针 |
| ---- | ---- | -------------------------------------- |

**返回值**

若注册成功则为 0，否则为非零值。

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

输出：

```txt
f2
f2
f1
```




### atof

原址：[https://zh.cppreference.com/w/c/string/byte/atof](https://zh.cppreference.com/w/c/string/byte/atof)

```c
double atof( const char* str );

```
​	转译 str 所指向的字节字符串中的浮点数。

​	函数会舍弃任何空白符（由 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定），直至找到首个非空白符。然后它会取用尽可能多的字符，以构成合法的浮点数表示，并将它们转换成浮点值。合法的浮点值可以为下列之一：

- 十进制浮点数表达式。它由下列部分组成：
- 十六进制浮点数表达式。它由下列部分组成：(C99 起)
  - (可选) 正或负号
  - `0x` 或 `0X`
  - 非空的十六进制数字序列，选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `p` 或 `P`，并跟随可选的正或负号，以及非空十进制数字序列（以 *2* 为底定义指数）
- 无穷大表达式。它由下列部分组成：(C99 起)
  - (可选) 正或负号
  - `INF` 或 `INFINITY`，忽略大小写
- 非数（NaN）表达式。它由下列部分组成：(C99 起)
  - (可选) 正或负号
  - `NAN` 或 `NAN(char_sequence)`，忽略 `NAN` 部分的大小写。 *char_sequence* 只能由数字、拉丁字母和下划线构成。结果是一个静态的 NaN 浮点值。



- 任何其他可由当前 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)接受的表达式。

**参数**

| str  | -    | 指向待转译的空终止字符串的指针 |
| ---- | ---- | ------------------------------ |

**返回值**

​	成功时返回对应于 str 内容的 double 的值。若转换的值在返回类型的范围外，则返回值未定义。若无可进行的转换，则返回 0.0。

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




### atoi

原址：[https://zh.cppreference.com/w/c/string/byte/atoi](https://zh.cppreference.com/w/c/string/byte/atoi)

```c
int       atoi ( const char* str );  // (1)	
long      atol ( const char* str ); // (2)	
long long atoll( const char* str ); // (3)	(C99 起)
```

​	转换 str 所指的字节字符串中的整数。隐含的基数总为 *10*。

​	舍弃任何空白符，直至找到首个非空白符，然后接收尽可能多的字符以组成合法的整数表示，并转换之为整数。合法的整数含下列部分：

- (可选) 正或负号
- 数位

​	如果结果的值无法被表示，即转换后的值落在对应返回类型之外，则其行为未定义。

**参数**

| str  | -    | 指向要转译的空终止字符串的指针 |
| ---- | ---- | ------------------------------ |

**返回值**

​	成功时为对应于 str 的内容的整数。若转换的值落在对应的返回类型范围外，则返回值未定义。

​	若无法进行转换，则返回 0。

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




### atol

原址：[https://zh.cppreference.com/w/c/string/byte/atoi](https://zh.cppreference.com/w/c/string/byte/atoi)

```c
int       atoi ( const char* str );  // (1)	
long      atol ( const char* str ); // (2)	
long long atoll( const char* str ); // (3)	(C99 起)
```

参见：[atoi](#atoi)










### atoll

原址：[https://zh.cppreference.com/w/c/string/byte/atoi](https://zh.cppreference.com/w/c/string/byte/atoi)

```c
int       atoi ( const char* str );  // (1)	
long      atol ( const char* str ); // (2)	
long long atoll( const char* str ); // (3)	(C99 起)
```

参见：[atoi](#atoi)












### bsearch

原址：[https://zh.cppreference.com/w/c/algorithm/bsearch](https://zh.cppreference.com/w/c/algorithm/bsearch)

```c
void* bsearch( const void *key, const void *ptr, size_t count, size_t size,
               int (*comp)(const void*, const void*) ); // (1)	
void* bsearch_s( const void *key, const void *ptr, rsize_t count, rsize_t size,
                 int (*comp)(const void *, const void *, void *),
                 void *context ); // (2)	(C11 起)
/*QVoid*/* bsearch( const void *key, /*QVoid*/ *ptr, size_t count, size_t size,
                    int (*comp)(const void*, const void*) ); // (3)	(C23 起)
/*QVoid*/* bsearch_s( const void *key, /*QVoid*/ *ptr, rsize_t count, rsize_t size,
                      int (*comp)(const void *, const void *, void *),
                      void *context );
```

1）在 `ptr` 所指向的数组中寻找等于 `key` 所指向的元素。该数组含 `count` 个大小为 `size` 字节的元素，并且已相对于 `key` 划分，也就是说，所有比较小于关键目标的元素必须出现于所有比较等于的元素之前，而且所有比较等于关键目标的元素要出现于所有比较大于关键目标的元素之前。完全排序的数组满足这些要求。用 `comp` 所指向的函数比较元素。若数组未依照与 `comp` 标准相同的相对于 `*key` 的升序划分，则行为未定义。

2）同 (1) ，除了传递给 `comp` 额外状态参数 `context` ，并在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

- `count` 或 `size` 大于 RSIZE_MAX

- `key` 、 `ptr` 或 `comp` 是空指针（除非 `count` 为零）

  同所有边界检查函数，`bsearch_s`（及对应的泛型宏）(C23 起)，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



3,4）分别等价于 (1) 与 (2) 的泛型宏。令 `T` 为一个无限定的对象类型（包括 void）。

- 若 `ptr` 类型为 `const T*` ，则返回类型为 `const void*` 。
- 否则，若 `ptr` 类型为 `T*` ，则返回类型为 `void*` 。
- 否则行为未定义。

​	若抑制这些泛型函数之一的宏定义以访问实际函数（例如使用 (bsearch)、 (bsearch_s) 或函数指针），则实际函数声明 (1) 或 (2) 变为可见。

​	若数组包含多个 `comp` 指示为与欲查找元素相等的元素，则结果返回的具体元素是未指定的。

​	直接使用实际函数 (1) 与 (2) 是被弃用的。(C23 起)

**参数**

| key     | -    | 指向要查找的元素的指针                                       |
| ------- | ---- | ------------------------------------------------------------ |
| ptr     | -    | 指向要检验的数组的指针                                       |
| count   | -    | 数组的元素数目                                               |
| size    | -    | 数组每个元素的字节数                                         |
| comp    | -    | 比较函数。如果首个参数*小于* ﻿第二个，那么返回负整数值，如果首个参数*大于* ﻿第二个，那么返回正整数值，如果两个参数等价，那么返回零。 将 `key` 传给首个参数，数组中的元素传给第二个。 <br />​	比较函数的签名应等价于如下形式：<br />​	`int cmp(const void *a, const void *b);`<br />​	该函数必须不修改传递给它的对象，而且在调用比较相同对象时必须返回一致的结果，与它们在数组中的位置无关。 |
| context | -    | 比较器的状态（例如，对照序列），作为第三个参数传递给 `comp`  |

**返回值**

1）指向与 `*key` 比较相等的指针，在找不到元素时返回空指针。

2）同 (1) ，除了在运行时约束违规时也返回空指针。

3,4） 分别同 (1) 与 (2) ，除了 cv 限定得到调整。

**注解**

​	与名称无关， C 和 POSIX 标准都未要求此函数用二分查找实现，也未保证任何复杂度。

​	与其他检查边界的函数不同， `bsearch_s` 不将零大小数组视作运行时约束违规，而是指出找不到元素（另一个接受零大小数组的函数是 `qsort_s` ）。

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




### bsearch_s

原址：[https://zh.cppreference.com/w/c/algorithm/bsearch](https://zh.cppreference.com/w/c/algorithm/bsearch)

```c
void* bsearch( const void *key, const void *ptr, size_t count, size_t size,
               int (*comp)(const void*, const void*) ); // (1)	
void* bsearch_s( const void *key, const void *ptr, rsize_t count, rsize_t size,
                 int (*comp)(const void *, const void *, void *),
                 void *context ); // (2)	(C11 起)
/*QVoid*/* bsearch( const void *key, /*QVoid*/ *ptr, size_t count, size_t size,
                    int (*comp)(const void*, const void*) ); // (3)	(C23 起)
/*QVoid*/* bsearch_s( const void *key, /*QVoid*/ *ptr, rsize_t count, rsize_t size,
                      int (*comp)(const void *, const void *, void *),
                      void *context );
```

参见：[bsearch](#bsearch)










### call_once

原址：

```c
```




### calloc

原址：[https://zh.cppreference.com/w/c/memory/calloc](https://zh.cppreference.com/w/c/memory/calloc)

```c
void* calloc( size_t num, size_t size );
```

​	为 `num` 个 `size` 大小的对象的数组分配内存，并将分配存储中的所有字节初始化为零。

​	若分配成功，会返回指向分配内存块最低位（首位）字节的指针，它为任何具有 [基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90) 的对象类型适当地对齐。

​	若 `size` 为零，则行为是实现定义的（可返回空指针，或返回不可用于访问存储的非空指针）。

​	`calloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 `free_sized` 及 `free_aligned_sized`(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用 *同步于* 分配同一块或部分相同的内存区域的 `calloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `calloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)



**参数**

| num  | -    | 对象数目       |
| ---- | ---- | -------------- |
| size | -    | 每个对象的大小 |

**返回值**

​	成功时，返回指向新分配内存开头的指针。为避免内存泄漏，必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 解分配返回的指针。

​	失败时，返回空指针。

**注解**

​	因为对齐需求的缘故，分配的字节数不必等于 `num * size` 。

​	初始化所有位为零不保证浮点数或指针分别被初始化为 0.0 或空指针值（尽管这在所有常见平台上都为真）。

​	本来（C89 中），已经为了接纳这种代码增加对零大小的支持：

```c
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

输出：

```txt
p2[0] == 0
p2[1] == 0
p2[2] == 0
p2[3] == 0
```




### div

原址：[https://zh.cppreference.com/w/c/numeric/math/div](https://zh.cppreference.com/w/c/numeric/math/div)

```c
div_t     div( int x, int y ); // (1)	
ldiv_t    ldiv( long x, long y ); // (2)	
lldiv_t   lldiv( long long x, long long y ); // (3)	(C99 起)
```

​	计算分子 `x` 除以分母 `y` 的商和余数。

| ​	同时计算商和余数。商为舍弃小数部分（向零取整）的代数商。余数满足 quot * y + rem == x。 | (C99 前) |
| ------------------------------------------------------------ | -------- |
| ​	同时计算商（表达式 x / y 的结果）和余数（表达式 x % y 的结果）。 | (C99 起) |

**参数**

| x, y | -    | 整数值 |
| ---- | ---- | ------ |
|      |      |        |

**返回值**

​	若余数和商都能表示成对应类型的对象（分别为 int、long、long long、[intmax_t](http://zh.cppreference.com/w/c/types/integer)），则将两者作为返回作为定义如下的 `div_t`、`ldiv_t`、`lldiv_t`、`imaxdiv_t` 类型对象返回：

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




### exit

原址：[https://zh.cppreference.com/w/c/program/exit](https://zh.cppreference.com/w/c/program/exit)

```c
void exit( int exit_code ); // (C11 前)
_Noreturn void exit( int exit_code ); // (C11 起) (C23 前)
[[noreturn]] void exit( int exit_code ); // (C23 起)
```

​	导致发生正常程序终止。

​	进行几个清理步骤：

- 以注册的逆序调用传递给 [atexit](https://zh.cppreference.com/w/c/program/atexit) 的函数
- 冲入并关闭所有 C 流
- 移除 [tmpfile](https://zh.cppreference.com/w/c/io/tmpfile) 创建的文件
- 将控制返回给宿主环境。若 `exit_code` 为零或 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示成功终止的实现定义状态。若 `exit_code` 为 [EXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status)，则返回指示不成功终止的实现定义状态。其他情况下返回实现定义的状态值。

**注解**

​	不调用由 [at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit) 注册的函数。

​	若程序调用 `exit` 多于一次，或它调用 `exit` 和 [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)，则行为未定义。

​	若在调用由 [atexit](https://zh.cppreference.com/w/c/program/atexit) 注册的函数期间，以 [longjmp](https://zh.cppreference.com/w/c/program/longjmp) 退出该函数，则行为未定义。

​	从 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function) 返回时，无论是通过 `return` 语句还是抵达函数尾，都会将 return 语句的实参（或若使用隐式返回，则为 0）作为 `exit_code` 传递并执行 `exit()`。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |

**返回值**

（无）

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
       exit( EXIT_FAILURE );
    }
    fclose(fp);
    printf("Normal Return\n");
    return EXIT_SUCCESS ;
}
```

可能的输出：

```txt
error opening file data.txt in function main()
```




### free

原址：[https://zh.cppreference.com/w/c/memory/free](https://zh.cppreference.com/w/c/memory/free)

```c
void free( void* ptr );
```

​	解分配之前由 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、`aligned_alloc()`(C11 起) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc) 分配的空间。

​	若 `ptr` 为空指针，则函数不进行操作。

​	若 `ptr` 的值不等于之前从 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、[realloc()](https://zh.cppreference.com/w/c/memory/realloc) 或 aligned_alloc()(C11 起) 返回的值，则行为未定义。

​	若 `ptr` 所指代的内存区域已经被解分配，则行为未定义，即是说已经以 `ptr` 为实参调用过 `free()`、`free_sized()`、`free_aligned_sized()`(C23 起) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc)，而且没有后继的 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc)、[realloc()](https://zh.cppreference.com/w/c/memory/realloc) 或 aligned_alloc()(C11 起) 调用以 `ptr` 为结果。

​	若在 `free()` 返回后通过指针 `ptr` 访问内存，则行为未定义（除非另一个分配函数恰好返回等于 `ptr` 的值）。

​	`free` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。解分配一块内存区域的 `free` 调用 *同步于* 分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)

**参数**

| ptr  | -    | 指向要解分配的内存的指针 |
| ---- | ---- | ------------------------ |

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




### free_aligned_sized <- 23+

原址：[https://zh.cppreference.com/w/c/memory/free_aligned_sized](https://zh.cppreference.com/w/c/memory/free_aligned_sized)

```c
void free_aligned_sized( void* ptr, size_t alignment, size_t size ); // (C23 起)
```

​	若 ptr 为空指针或为对 aligned_alloc 的调用结果，其中 alignment 等于所请求的对齐而 size 等于所请求的分配大小，则本函数等价于 [free](http://zh.cppreference.com/w/c/memory/free)(ptr)。否则，其行为未定义。

​	[malloc](https://zh.cppreference.com/w/c/memory/malloc)、[calloc](https://zh.cppreference.com/w/c/memory/calloc) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 的调用结果不能传递给 `free_aligned_sized`。

​	`free_aligned_sized` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的 `free_aligned_sized` 调用 *同步于* 分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。

**参数**

| ptr       | -    | 指向欲接分配内存的指针 |
| --------- | ---- | ---------------------- |
| alignment | -    | 欲解分配内存的对齐     |
| size      | -    | 欲解分配内存的大小     |

**返回值**

​	（无）

**示例**

> 本节未完成 
>
> 原因：暂无示例








### free_sized <- 23+

原址：[https://zh.cppreference.com/w/c/memory/free_sized](https://zh.cppreference.com/w/c/memory/free_sized)

```c
void free_sized( void* ptr, size_t size ); // (C23 起)
```

​	解分配之前由 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc) 或 [realloc()](https://zh.cppreference.com/w/c/memory/realloc)（但非 aligned_alloc()）分配的存储空间。

> 本节未完成
>
> 原因：share wording among `free_*` family

​	`free_sized` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的 `free_sized` 调用 *同步于* 分配同一块或部分相同的内存区域的后续任何分配函数的调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何分配函数所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。

**参数**

| ptr  | -    | 指向欲解分配内存的指针       |
| ---- | ---- | ---------------------------- |
| size | -    | 之前传递给分配函数的内存大小 |

**返回值**

​	（无）

**注解**

​	本节未完成

**可能的实现**

```c
void free_sized(void* ptr, size_t /*size*/)
{
    free(ptr);
}
```

**示例**

```c
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>
 
typedef struct
{
    size_t size;     // 当前的元素数
    size_t capacity; // 保留的元素数
    void** data;
} PtrVector;
 
PtrVector vector_create(size_t initial_capacity)
{
    PtrVector ret =
    {
        .capacity = initial_capacity,
        .data = (void**) malloc(initial_capacity * sizeof(void*))
    };
    return ret;
}
 
void vector_delete(PtrVector* self)
{
    free_sized(self->data, self->capacity * sizeof(void*));
}
 
void vector_push_back(PtrVector* self, void* value)
{
    if (self->size == self->capacity)
    {
        self->capacity *= 2;
        self->data = (void**) realloc(self->data, self->capacity * sizeof(void*));
    }
    self->data[self->size++] = value;
}
 
int main()
{
    int data = 42;
    float pi = 3.141592f;
    PtrVector v = vector_create(8);
    vector_push_back(&v, &data);
    vector_push_back(&v, &pi);
    printf("data[0] = %i\n", *(int*)v.data[0]);
    printf("data[1] = %f\n", *(float*)v.data[1]);
    vector_delete(&v);
}
```

输出：

```txt
data[0] = 42
data[1] = 3.141592
```




### getenv

原址：[https://zh.cppreference.com/w/c/program/getenv](https://zh.cppreference.com/w/c/program/getenv)

```c
char *getenv( const char *name ); // 1
```




### getenv_s <- 11+

原址：[https://zh.cppreference.com/w/c/program/getenv](https://zh.cppreference.com/w/c/program/getenv)

```c
errno_t getenv_s( size_t *restrict len, char *restrict value,
                  rsize_t valuesz, const char *restrict name ); // 2
```

1）在宿主指定的环境列表中，查找名为 `name` 的环境变量，并返回关联到匹配环境变量的字符串。环境变量的集合及修改它的方法是实现定义的。

​	此函数不保证是线程安全的。另一个对 `getenv` 的调用，和对 POSIX 函数 [setenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/setenv.html)、[unsetenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/unsetenv.html) 及 [putenv()](http://pubs.opengroup.org/onlinepubs/9699919799/functions/putenv.html) 的调用，可能会使先前的调用返回的指针失效，或者修改先前调用所得的字符串。

​	 修改 `getenv` 返回的字符串会引起未定义行为。

2）同 (1)，但将环境变量的值写入用户提供的缓冲区 `value`（除非它为 `NULL`），而且将写入的字节数存储于用户提供的位置 `*len`（除非它为 `NULL`）。若环境变量未设置于环境中，则 `*len` 会被写入零（除非是 `NULL`），且 `'\0'` 会被写入 `value[0]`（除非是 `NULL`）。另外，在运行时检测下列错误并调用当前安装的 [制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s) 函数

- `name` 是空指针
- `valuesz` 大于 RSIZE_MAX
- `value` 是空指针且 `valuesz` 非零

​	同所有边界检查函数，`getenv_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 `1` 才保证可用。

**参数**

| name    | -    | 标识要查找的环境变量名称的空终止字符串                       |
| ------- | ---- | ------------------------------------------------------------ |
| len     | -    | 指向用户提供的位置，`getenv_s` 将会在其中存储环境变量的长度  |
| value   | -    | 指向用户提供的字符数组，`getenv_s` 将会在其中存储环境变量内容 |
| valuesz | -    | 允许 `getenv_s` 对目标写入的最大字节数（缓冲区大小）         |

**返回值**

1) 标识环境变量的值的字符串，若找不到该环境变量则为空指针。
2) 若找到环境变量则为零，若找不到该环境变量或发生运行时强制违规，则为非零。错误的情况下，将 `*len` 写入零（除非 `len` 为空指针）。

**注解**

​	POSIX 系统上，亦可通过全局变量 `environ` 访问 [环境变量](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap08.html#tag_08)，它于 `<unistd.h>` 中声明为 `extern char **environ;`，并可通过可选的 [`main` 函数](https://zh.cppreference.com/w/c/language/main_function) 第三参数 `envp` 访问。

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




### ignore_handler_s <- 11+

原址：[https://zh.cppreference.com/w/c/error/ignore_handler_s](https://zh.cppreference.com/w/c/error/ignore_handler_s)

```c
void ignore_handler_s( const char * restrict msg,
                       void * restrict ptr,
                       errno_t error
                     ); // (C11 起)
```

​	该函数只是返回到调用方，而不进行任何动作。

​	可以将指向此函数的指针传递给 [set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s) 以建立无任何动作的运行时制约违规处理函数。

​	同所有边界检查函数， `ignore_handler_s` 仅若实现定义了 `__STDC_LIB_EXT1__` ，且用户在包含 `<stdlib.h>` 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 `1` 才保证可用。



**参数**

| msg   | -    | 指向描述错误的字符串的指针                                   |
| ----- | ---- | ------------------------------------------------------------ |
| ptr   | -    | 指向实现定义的对象的指针或空指针。实现定义对象的例子有，给出检测到违规的函数的称和检测到违规时的行号的对象 |
| error | -    | 要由调用方函数返回的错误号，若它正好是返回 `errno_t` 的函数之一 |

**返回值**

​	（无）

**注意**

​	若以 `ignore_handler_s` 为运行时制约违规处理函数，则可通过检验带边界检查函数的调用结果检测违规，这对于不同函数可能不同（非零 `errno_t` ，在输出字符串的第一个字节写入了空字符，等等）。

​	若从不调用 `set_constraint_handler_s` ，则默认处理是实现定义的：它可以是 `abort_handler_s` 、 `ignore_handler_s` 或另外的实现定义处理函数。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
#ifdef __STDC_LIB_EXT1__
    char dst[2];
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
    set_constraint_handler_s(abort_handler_s);
    r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

可能的输出：

```txt
dst = "", r = 22
abort_handler_s was called in response to a runtime-constraint violation.
 
The runtime-constraint violation was caused by the following expression in strcpy_s:
(s1max <= (s2_len=strnlen_s(s2, s1max)) ) (in string_s.c:62)
 
Note to end users: This program was terminated as a result
of a bug present in the software. Please reach out to your
software's vendor to get more help.
Aborted
```




### labs

原址：[https://zh.cppreference.com/w/c/numeric/math/abs](https://zh.cppreference.com/w/c/numeric/math/abs)

```c
int        abs( int n );
long       labs( long n );
long long llabs( long long n ); // (C99 起)
```

参见：[abs](#abs)












### ldiv

原址：[https://zh.cppreference.com/w/c/numeric/math/div](https://zh.cppreference.com/w/c/numeric/math/div)

```c
div_t     div( int x, int y ); // (1)	
ldiv_t    ldiv( long x, long y ); // (2)	
lldiv_t   lldiv( long long x, long long y ); // (3)	(C99 起)
```

参见：[div](#div)












### llabs

原址：[https://zh.cppreference.com/w/c/numeric/math/abs](https://zh.cppreference.com/w/c/numeric/math/abs)

```c
int        abs( int n );
long       labs( long n );
long long llabs( long long n ); // (C99 起)
```

参见：[abs](#abs)










### lldiv

原址：[https://zh.cppreference.com/w/c/numeric/math/div](https://zh.cppreference.com/w/c/numeric/math/div)

```c
div_t     div( int x, int y ); // (1)	
ldiv_t    ldiv( long x, long y ); // (2)	
lldiv_t   lldiv( long long x, long long y ); // (3)	(C99 起)
```

参见：[div](#div)










### malloc

原址：[https://zh.cppreference.com/w/c/memory/malloc](https://zh.cppreference.com/w/c/memory/malloc)

```c
void* malloc( size_t size );
```

​	分配 `size` 字节的未初始化内存。

​	若分配成功，则返回为任何拥有[基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90)的对象类型对齐的指针。

​	若 `size` 为零，则 `malloc` 的行为实现是其实现（生成）时定义的。例如可返回空指针。亦可返回非空指针；但不应当[解引用](https://zh.cppreference.com/w/c/language/operator_member_access)这种指针，而且应将它传递给 [free](https://zh.cppreference.com/w/c/memory/free) 以避免内存泄漏。

​	`malloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。

​	解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 free_sized 及 free_aligned_sized(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用*同步于*分配同一块或部分相同的内存区域的 `malloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `malloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)

**参数**

| size | -    | 要分配的字节数 |
| ---- | ---- | -------------- |

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




### mblen

原址：[https://zh.cppreference.com/w/c/string/multibyte/mblen](https://zh.cppreference.com/w/c/string/multibyte/mblen)

```c
int mblen( const char* s, size_t n );
```

​	确定 `s` 指向其首字节的多字节字符的字节大小。

​	若 `s` 是空指针，则重置全局转换状态并(C23 前)确定是否使用迁移序列。

​	此函数等价于调用 [mbtowc](http://zh.cppreference.com/w/c/string/multibyte/mbtowc)`((wchar_t*)0, s, n)`，除了 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 的转换状态不受影响。

**参数**

| s    | -    | 指向多字节字符的指针       |
| ---- | ---- | -------------------------- |
| n    | -    | `s` 中能被检验的字节数限制 |

**返回值**

​	若 `s` 不是空指针，则返回多字节字符所含的字节数，或若 `s` 所指的首字节不组成合法多字节字符则返回 -1，或若 `s` 指向空字符 `'\0'` 则返回 0。

​	若 `s` 是空指针，则重置内部转换状态为初始迁移状态，(C23 前)若当前多字节编码非状态依赖（不使用迁移序列）则返回 0，或者若当前多字节编码为状态依赖（使用迁移序列）则返回非零。

**注解**

​	每次对 `mblen` 的调用更新内部全局转换状态（ [mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的静态对象，只为此函数所知）。若多字节编码使用迁移状态，则必须留意以避免回撤或多次扫描。任何情况下，多线程不应无同步地调用 `mblen`：可用 [mbrlen](https://zh.cppreference.com/w/c/string/multibyte/mbrlen) 代替。(C23 前)

​	不允许 `mblen` 拥有内部状态。(C23 起)

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




### mbstowcs

原址：[https://zh.cppreference.com/w/c/string/multibyte/mbstowcs](https://zh.cppreference.com/w/c/string/multibyte/mbstowcs)

```c
size_t mbstowcs( wchar_t          *dst, const char          *src, size_t len) // (C99 前)
size_t mbstowcs( wchar_t *restrict dst, const char *restrict src, size_t len) // (C99 起)
errno_t mbstowcs_s(size_t *restrict retval, wchar_t *restrict dst,
                  rsize_t dstsz, const char *restrict src, rsize_t len); // (2)	(C11 起)
```

1）将从首元素为 `src` 所指的数组中的多字节字符串转换为其宽字符表示。被转换的字符存储于 `dst` 所指向数组的相继元素。写入目标数组的宽字符数不多于 `len`。

 	如同以调用 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 来转换每个字符，除了 mbtowc 转换状态不受影响。若满足任一条件则转换停止：

-  转换并存储了多字节空字符。
- 遇到（当前 C 本地环境中的）非法多字节字符。
- 将要存储的下个宽字符会超出 `len`。

 若 `src` 与 `dst` 重叠，则行为未定义

2）同 (1)，但

-  如同以 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)，而非 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 进行转换
- 函数用输出参数 `retval` 返回结果
- 若在写入 `len` 个宽字符后未写入空字符到 `dst`，则存储 `L'\0'` 于 `dst[len]`，这表示总计写入 len+1 个宽字符
- 若 `dst` 是空指针，则存储本会产生的宽字符数于 *retval
- 函数破坏目标数组从空终止到 `dstsz` 为止的内容
- 若 `src` 与 `dst` 重叠，则行为未指定。
- 在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：
  - `retval` 或 `src` 是空指针
  - `dstsz` 或 `len` 大于 RSIZE_MAX/sizeof(wchar_t)（除非 `dst` 为空）
  - `dstsz` 非零（除非 `dst` 为空）
  - `src` 数组中的前 `dstsz` 个多字节中无空字符且 `len` 大于 `dstsz`（除非 `dst` 为空）

​	同所有边界检查函数，`mbstowcs_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



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

1) 成功时，返回目标数组的宽字符数，不含终止符 L'\0'。转换错误时（若遇到非法多字节字符），返回 ([size_t](http://zh.cppreference.com/w/c/types/size_t))-1。
2) 成功时为零（该情况下写入或本该写入到 `dst` 的不含终止零的宽字符存储于 `*retval`），错误时为非零，在运行时制约违规的情况，存储 ([size_t](http://zh.cppreference.com/w/c/types/size_t))-1 于 `*retval`（除非 `retval` 为空）并设置 dst[0] 为 `L'\0'`（除非 `dst` 为空或 `dstmax` 为零或大于 RSIZE_MAX）

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




### mbstowcs_s

原址：[https://zh.cppreference.com/w/c/string/multibyte/mbstowcs](https://zh.cppreference.com/w/c/string/multibyte/mbstowcs)

```c
size_t mbstowcs( wchar_t          *dst, const char          *src, size_t len) // (C99 前)
size_t mbstowcs( wchar_t *restrict dst, const char *restrict src, size_t len) // (C99 起)
errno_t mbstowcs_s(size_t *restrict retval, wchar_t *restrict dst,
                  rsize_t dstsz, const char *restrict src, rsize_t len); // (2)	(C11 起)
```

参见：[mbstowcs](#mbstowcs)










### mbtowc

原址：[https://zh.cppreference.com/w/c/string/multibyte/mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc)

```c
int mbtowc( wchar_t*          pwc, const char*          s, size_t n ) // (C99 前)
int mbtowc( wchar_t* restrict pwc, const char* restrict s, size_t n ) // (C99 起)
```

​	将 s 指向其首字节的多字节字符转换成宽字符，若 pwc 非空则写入 *pwc。

​	若 s 为空指针，则重置全局转换状态并确定是否使用迁移序列。

**注解**

​	每次对 `mbtowc` 的调用更新内部全局转换状态（[mbstate_t](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) 类型的静态对象，只为此函数所知）。若多字节编码使用迁移状态，则必须留意以避免回撤或多次扫描。任何情况下，多线程不应调用 `mbtowc` 而不同步：可用 [mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc) 代替。

**参数**

| pwc  | -    | 指向输出用宽字符的指针     |
| ---- | ---- | -------------------------- |
| s    | -    | 指向多字节字符的指针       |
| n    | -    | s 中能被检验的字节数的限制 |

**返回值**

​	若 s 不是空指针，则返回多字节字符所含的字节数，或若 s 所指的首字节不组成合法多字节字符则返回 -1，或若 s 指向空字符 '\0' 则返回 0。

​	若 s 是空指针，则重置内部转换状态为初始迁移状态，并若当前多字节编码非状态依赖（不使用迁移序列）则返回 0，或若当前多字节编码为状态依赖（使用迁移序列）则返回非零值。

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




### memalignment <- 23+

原址：[https://zh.cppreference.com/w/c/program/memalignment](https://zh.cppreference.com/w/c/program/memalignment)

```c
size_t memalignment( const void *p ); // (C23 起)
```

​	返回提供的地址所满足的最大对齐。返回值能大于任何实现所支持的对齐值。如果 `p` 为空指针值，则返回 0 指示该指针不能用于访问任何类型的对象。

​	如果返回值大于或等于 alignof(T)，则类型 `T` 的对齐要求为该指针所满足。

​	[独立实现](https://zh.cppreference.com/w/c/language/conformance) 需要提供 `memalignment`。

**参数**

| p    | -    | 要查询对齐的指针 |
| ---- | ---- | ---------------- |

**返回值**

`p` 的对齐值，或如果 `p` 为空指针值则为 0。

**注解**

​	在

- 空指针转型为整数 0，
- 指针值直接转型为虚拟地址的数值，且
- [size_t](https://zh.cppreference.com/w/c/types/size_t) 与 [uintptr_t](https://zh.cppreference.com/w/c/types/integer) 相同

的常见平台上，此函数能被实现为 return ([size_t](http://zh.cppreference.com/w/c/types/size_t))p & -([size_t](http://zh.cppreference.com/w/c/types/size_t))p;。

**示例**

```c
#include <stdio.h>
#include <stdlib.h>
 
int main()
{
    alignas(128) int i = 0;
    printf("%zu\n%zu\n", memalignment(nullptr), memalignment(&i));
}
```

可能的输出：

```txt
0
128
```




### malloc

原址：[https://zh.cppreference.com/w/c/memory/malloc](https://zh.cppreference.com/w/c/memory/malloc)

```c
void* malloc( size_t size );
```

​	分配 `size` 字节的未初始化内存。

​	若分配成功，则返回为任何拥有 [基础对齐](https://zh.cppreference.com/w/c/language/object#.E5.AF.B9.E9.BD.90) 的对象类型对齐的指针。

​	若 `size` 为零，则 `malloc` 的行为实现是其实现（生成）时定义的。例如可返回空指针。亦可返回非空指针；但不应当 [解引用](https://zh.cppreference.com/w/c/language/operator_member_access) 这种指针，而且应将它传递给 [free](https://zh.cppreference.com/w/c/memory/free) 以避免内存泄漏。

​	`malloc` 是线程安全的：它表现得如同只访问通过其参数可见的内存区域，而非任何静态存储。解分配一块内存区域的先前 [free](https://zh.cppreference.com/w/c/memory/free)、 `free_sized` 及 `free_aligned_sized`(C23 起) 或 [realloc](https://zh.cppreference.com/w/c/memory/realloc) 调用 *同步于* 分配同一块或部分相同的内存区域的 `malloc` 调用。此同步出现于任何通过解分配函数所作的内存访问之后，和任何 `malloc` 所作出的内存访问之前。所有操作每块特定内存区域的分配和解分配函数拥有单独全序。(C11 起)

**参数**

| size | -    | 要分配的字节数 |
| ---- | ---- | -------------- |

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

输出：

```txt
p1[0] == 0
p1[1] == 1
p1[2] == 4
p1[3] == 9
```




### qsort

原址：[https://zh.cppreference.com/w/c/algorithm/qsort](https://zh.cppreference.com/w/c/algorithm/qsort)

```c
void qsort( void* ptr, size_t count, size_t size,
            int (*comp)(const void*, const void*) ); // (1)	
errno_t qsort_s( void* ptr, rsize_t count, rsize_t size,
                 int (*comp)(const void*, const void*, void*),
                 void* context ); // (2)	(C11 起)
```

1）对 ptr 所指向的数组以升序排序。数组包含 count 个长度为 size 字节的元素。用 comp 所指向的函数比较对象。

2）同 (1)，除了传递给 comp 附加环境参数 context，还会在运行时检测下列错误，并调用当前安装的[约束处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：



​	若 comp 指示两元素相等，则它们排序后的结果是未指定的。

**参数**

| ptr     | -    | 指向待排序的数组的指针                                       |
| ------- | ---- | ------------------------------------------------------------ |
| count   | -    | 数组的元素数目                                               |
| size    | -    | 数组每个元素的字节大小                                       |
| comp    | -    | 比较函数。如果首个参数*小于* ﻿第二个，那么返回负整数值，如果首个参数*大于* ﻿第二个，那么返回正整数值，如果两个参数等价，那么返回零。 <br />​	比较函数的签名应等价于如下形式：<br />​	`int cmp(const void *a, const void *b);`<br />​	该函数必须不修改传递给它的对象，而且在调用比较相同对象时必须返回一致的结果，与它们在数组中的位置无关。 |
| context | -    | 附加信息（例如，校排序列），作为第三个参数传递给 comp        |

**返回值**

1）（无）

2）成功时为零，若检测到运行时制约违规，则为非零

**注意**

​	不管其名字如何，C 和 POSIX 标准都未要求此函数用[快速排序](https://en.wikipedia.org/wiki/Quicksort)实现，也未保证任何复杂度或稳定性。

​	与其他边界检查函数不同，`qsort_s` 不将零大小数组视作运行时强制违规，而是不修改数组并成功返回（另一个接受零大小数组的函数是 `bsearch_s`）。

​	[Windows CRT](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/qsort-s) 中的 `qsort_s` 实现与 C 标准不兼容。微软的版本被声明为： `void qsort_s(void *base, size_t num, size_t width, int (*compare )(void *, const void *, const void *), void * context);`。 它不返回值，而比较函数具有与标准相反的形参顺序：首先传递的是 context。[size_t](http://zh.cppreference.com/w/c/types/size_t)

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




### qsort_s

原址：[https://zh.cppreference.com/w/c/algorithm/qsort](https://zh.cppreference.com/w/c/algorithm/qsort)

```c
void qsort( void* ptr, size_t count, size_t size,
            int (*comp)(const void*, const void*) ); // (1)	
errno_t qsort_s( void* ptr, rsize_t count, rsize_t size,
                 int (*comp)(const void*, const void*, void*),
                 void* context ); // (2)	(C11 起)
```

参见：[qsort](#qsort)










### quick_exit <- 11+

原址：[https://zh.cppreference.com/w/c/program/quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)

```c
_Noreturn void quick_exit( int exit_code ); // (C11 起) (C23 前)
[[noreturn]] void quick_exit( int exit_code );// (C23 起)
```

​	导致程序正常终止，而不完全清理资源。

​	以注册顺序的逆序调用传递给 [at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit) 的函数。调用完注册的函数后，调用 [_Exit](http://zh.cppreference.com/w/c/program/_Exit)(exit_code)。

**参数**

| exit_code | -    | 程序的退出状态 |
| --------- | ---- | -------------- |

**返回值**

（无）

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
 
void f3(void)
{
    puts("won't be called");
}
 
int main(void)
{
    at_quick_exit(f1);
    at_quick_exit(f2);
    atexit(f3);
    quick_exit(0);
}
```

输出：

```txt
pushed second
pushed first
```




### rand

原址：[https://zh.cppreference.com/w/c/numeric/random/rand](https://zh.cppreference.com/w/c/numeric/random/rand)

```c
int rand();
```

​	返回 0 与 [RAND_MAX](https://zh.cppreference.com/w/c/numeric/random/RAND_MAX) 间的随机整数值（包含 0 与 `RAND_MAX`）。

​	[srand()](https://zh.cppreference.com/w/c/numeric/random/srand) 播种 `rand()` 所用的伪随机数生成器。若在任何对 `srand()` 的调用前使用 `rand()`，则 `rand()` 表现如同它以 `srand(1)` 播种。每次以 `srand()` 播种 `rand()` 时，它必须产生相同的值数列。

​	不保证 `rand()` 为线程安全。

**参数**

​	（无）

**返回值**

​	0 与 [RAND_MAX](https://zh.cppreference.com/w/c/numeric/random/RAND_MAX) 间包含边界的随机整数值。

**注意**

​	无对产生的随机数质量的保证。过去，某些 `rand()` 的实现在随机性、分布和产生的数列周期中有严重缺陷（在一个广为人知的例子中，最低位在调用间简单地于 `1` 和 `0` 间改变）。不推荐将 `rand()` 用于严肃的随机数生成需求，如加密。

​	POSIX 要求 `rand` 所用的伪随机数生成器的周期至少为 \\(2^{32}\\)。

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




### realloc

原址：[https://zh.cppreference.com/w/c/memory/realloc](https://zh.cppreference.com/w/c/memory/realloc)

```c
void *realloc( void *ptr, size_t new_size );
```

​	重新分配给定的内存区域。若 `ptr` 非 NULL，则它必须是之前为 [malloc()](https://zh.cppreference.com/w/c/memory/malloc)、[calloc()](https://zh.cppreference.com/w/c/memory/calloc) 或 `realloc()` 所分配，并且仍未被 [free](https://zh.cppreference.com/w/c/memory/free) 或 `realloc` 的调用所释放。否则，结果未定义。

​	重新分配按以下二者之一执行：

a) 可能的话，扩张或收缩 ptr 所指向的现有内存区域。新旧大小中的较小者范围内的区域的内容保持不变。若扩张范围，则数组新增部分的内容是未定义的。

b) 分配一个大小为 `new_size` 字节的新内存块，并复制大小等于新旧大小中较小者的内存区域，然后释放旧内存块。

​	若无足够内存，则不释放旧内存块，并返回空指针。

​	若 ptr 为 [NULL](https://zh.cppreference.com/w/c/types/NULL)，则行为与调用 [malloc](http://zh.cppreference.com/w/c/memory/malloc)(new_size) 相同。

​	否则，

​	若 new_size 为零，则行为是实现定义的（可能返回空指针，该情况下可能或可能不释放旧内存，或可能返回某个不能用于访问存储的非空指针）。这种用法被弃用（经由 [C DR 400](https://open-std.org/JTC1/SC22/WG14/www/docs/n2396.htm#dr_400)）。(C17 起) (C23 前)

​	若 `new_size` 为零，则行为未定义。(C23 起)

​	`realloc` 是线程安全的：它表现得如同只访问通过其实参可见的内存区域，而非任何静态存储。先前令 [free](https://zh.cppreference.com/w/c/memory/free) 或 `realloc` 归还一块内存区域的调用，*同步于* 任何分配函数的调用，包括分配相同或部分相同内存区域的 `realloc` 。这种同步出现于任何解分配函数所做的内存访问后，和任何 `realloc` 所做内存访问前。所有操作一块特定内存区域的分配及解分配函数拥有单独全序。(C11 起)

**参数**

| ptr      | -    | 指向需要重新分配的内存区域的指针 |
| -------- | ---- | -------------------------------- |
| new_size | -    | 数组的新大小（字节数）           |

**返回值**

​	成功时，返回指向新分配内存的指针。返回的指针必须用 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 归还。原指针 ptr 失效，而且任何通过它的访问是未定义行为（即使重分配是就地的）。

​	失败时，返回空指针。原指针 `ptr` 保持有效，并需要通过 [free()](https://zh.cppreference.com/w/c/memory/free) 或 `realloc()` 归还。

**注解**

​	本来（C89 中），增加对零大小的支持是为了容纳这种代码：

```c
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

可能的输出：

```txt
New location: 0x144c010. Size: 8 ints (32 bytes).
Old location: 0x144c010. Size: 10 ints (40 bytes).
New location: 0x144c450. Size: 12 ints (48 bytes).
Old location: 0x144c450. Size: 512 ints (2048 bytes).
Old location: 0x144c450. Size: 32768 ints (131072 bytes).
New location: 0x7f490c5bd010. Size: 65536 ints (262144 bytes).
Old location: 0x7f490c5bd010. Size: 32768 ints (131072 bytes).
```




### set_constraint_handler_s

原址：[https://zh.cppreference.com/w/c/error/set_constraint_handler_s](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)

```c
constraint_handler_t set_constraint_handler_s( constraint_handler_t handler ); // (1)	(C11 起)
typedef void (*constraint_handler_t)( const char *restrict msg,
                                      void *restrict ptr,
                                      errno_t error); // (2)	(C11 起)
```

1) 配置所有 [带边界检查函数](https://zh.cppreference.com/w/c/error#.E8.BE.B9.E7.95.8C.E6.A3.80.E6.9F.A5) 在发生运行时制约违规时所调用的处理函数，或恢复成默认处理函数（若 `handler` 是空指针）。
2) 指向将在运行时制约违规时调用的处理函数的指针。

​	若从不调用 `set_constraint_handler_s`，则默认处理是实现定义的：它可以是 abort_handler_s、ignore_handler_s 或另外的实现定义处理函数。

​	同所有边界检查函数， `set_constraint_handler_s, constraint_handler_t` 仅若实现定义了 `__STDC_LIB_EXT1__` ，且用户在包含 `<stdlib.h>` 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

​	与所有带边界检查的函数一样，仅当实现定义了 `__STDC_LIB_EXT1__` 并且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 之前将 `__STDC_WANT_LIB_EXT1__` 定义为整数常量 1 时，`set_constraint_handler_s` 和 `constraint_handler_t` 才保证可用。

**参数**

| handler | -    | `constraint_handler_t` 类型的函数指针或空指针                |
| ------- | ---- | ------------------------------------------------------------ |
| msg     | -    | 指向描述错误的字符串的指针                                   |
| ptr     | -    | 指向由实现定义的对象的指针或为空指针。由实现定义的对象的例子可以给出检测到违规的函数的名字和检测到违规的行号 |
| error   | -    | 如果所调用的函数刚好是返回 `errno_t` 的函数，则是将由此函数返回的错误 |

**返回值**

​	指向先前安装的运行时制约处理函数的指针（注意：此指针决不会是空指针，因为调用 set_constraint_handler_s([NULL](http://zh.cppreference.com/w/c/types/NULL)) 会设置系统默认处理函数）。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
#ifdef __STDC_LIB_EXT1__
    char dst[2];
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
    set_constraint_handler_s(abort_handler_s);
    r = strcpy_s(dst, sizeof dst, "Too long!");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

可能的输出：

```txt
dst = "", r = 22
abort_handler_s was called in response to a runtime-constraint violation.
 
The runtime-constraint violation was caused by the following expression in strcpy_s:
(s1max <= (s2_len=strnlen_s(s2, s1max)) ) (in string_s.c:62)
 
Note to end users: This program was terminated as a result
of a bug present in the software. Please reach out to your
software's vendor to get more help.
Aborted
```




### srand

原址：[https://zh.cppreference.com/w/c/numeric/random/srand](https://zh.cppreference.com/w/c/numeric/random/srand)

```c
void srand( unsigned seed );
```

​	以值 `seed` 播种 [rand()](https://zh.cppreference.com/w/c/numeric/random/rand) 所用的随机数生成器。

​	若在任何到 `srand()` 的调用前使用 `rand()`，则 `rand()` 表现为如同它被以 `srand(1)` 播种。

​	每次以同一 `seed` 播种 `rand()` 时，它必须产生相同的值数列。

​	`srand()` 不保证为线程安全。

**参数**

| seed 种子值 | -    |      |
| ----------- | ---- | ---- |

**返回值**

​	（无）

**注意**

​	通常来说，应该只播种一次随机数生成器，在程序开始处，任何到 `rand()` 的调用前。不应重复播种，或每次冀愿生成新一批随机数时重播种。

​	标准实践是使用以 [time](http://zh.cppreference.com/w/c/chrono/time)(0) 为种子调用的结果。然而 `time()` 返回 [time_t](http://zh.cppreference.com/w/c/chrono/time_t) 值，而不保证 `time_t` 是整数类型。 尽管实践中，主流实现都定义 `time_t` 为整数类型，且此亦为 POSIX 所要求。

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




### strfromd

原址：

```c
```




### strfromd128

原址：

```c
```




### strfromd32

原址：

```c
```




### strfromd64

原址：

```c
```




### strfromdN

原址：

```c
```




### strfromdNx

原址：

```c
```




### strfromencbindN

原址：

```c
```




### strfromencdecdN

原址：

```c
```




### strfromencfN

原址：

```c
```




### strfromf

原址：

```c
```




### strfromfN

原址：

```c
```




### strfromfNx

原址：

```c
```




### strfroml

原址：

```c
```




### strtod

原址：[https://zh.cppreference.com/w/c/string/byte/strtof](https://zh.cppreference.com/w/c/string/byte/strtof)

```c
float       strtof ( const char* restrict str, char** restrict str_end ); // (1)	(C99 起)
double      strtod ( const char*          str, char**          str_end ); // (2)	 (C99 前)
double      strtod ( const char* restrict str, char** restrict str_end ); // (2)	 (C99 前)
long double strtold( const char* restrict str, char** restrict str_end ); // (3)	(C99 起)
```

参见：[strtof](#strtof)










### strtod128

原址：

```c
```




### strtod32

原址：

```c
```




### strtod64

原址：

```c
```




### strtodN

原址：

```c
```




### strtodNx

原址：

```c
```




### strtoencbindN

原址：

```c
```




### strtoencdecdN

原址：

```c
```




### strtoencfN

原址：

```c
```




### strtof

原址：[https://zh.cppreference.com/w/c/string/byte/strtof](https://zh.cppreference.com/w/c/string/byte/strtof)

```c
float       strtof ( const char* restrict str, char** restrict str_end ); // (1)	(C99 起)
double      strtod ( const char*          str, char**          str_end ); // (2)	 (C99 前)
double      strtod ( const char* restrict str, char** restrict str_end ); // (2)	 (C99 前)
long double strtold( const char* restrict str, char** restrict str_end ); // (3)	(C99 起)
```

​	转译 str 所指向的字节字符串中的浮点数。

​	函数会舍弃任何空白符（由 [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) 确定），直至找到首个非空白符。然后它会取用尽可能多的字符，以构成合法的浮点数表示，并将它们转换成浮点值。合法的浮点值可以为下列之一：

- 十进制浮点数表达式。它由下列部分组成：
- 十六进制浮点数表达式。它由下列部分组成：(C99 起)
  - (可选) 正或负号
  - `0x` 或 `0X`非空的十六进制数字序列，选地包含一个小数点字符（由当前的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)确定）（定义有效数字）
  - (可选) `p` 或 `P`，并跟随可选的正或负号，以及非空十进制数字序列（以 *2* 为底定义指数）
- 无穷大表达式。它由下列部分组成：(C99 起)
  - (可选) 正或负号
  - `INF` 或 `INFINITY`，忽略大小
- 写非数（NaN）表达式。它由下列部分组成：
  - (可选) 正或负号
  - `NAN` 或 `NAN(char_sequence)`，忽略 `NAN` 部分的大小写。 *char_sequence* 只能由数字、拉丁字母和下划线构成。结果是一个静态的 NaN 浮点值。

- 任何其他可由当前 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)接受的表达式。

​	函数设置 str_end 所指向的指针指向最后被转译字符的后一字符，若 str_end 为空指针，则忽略它。

**参数**

| str     | -    | 指向要转译的空终止字节字符串的指针 |
| ------- | ---- | ---------------------------------- |
| str_end | -    | 指向指向字符指针的指针             |

**返回值**

​	成功时为对应 str 内容的浮点数。若转换出的值落在对应返回类型的范围外，则发生值域错误（将 [errno](https://zh.cppreference.com/w/c/error/errno) 设为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [HUGE_VAL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)、[HUGE_VALF](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL) 或 [HUGE_VALL](https://zh.cppreference.com/w/c/numeric/math/HUGE_VAL)。若无法进行转换，则返回 0 并将 *str_end 设为 `str`。

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




### strtofN

原址：

```c
```




### strtofNx

原址：

```c
```




### strtol

原址：[https://zh.cppreference.com/w/c/string/byte/strtol](https://zh.cppreference.com/w/c/string/byte/strtol)

```c
long      strtol( const char*          str, char**          str_end, int base ); // (C99 前)
long      strtol( const char* restrict str, char** restrict str_end, int base ); // (C99 起)
long long strtoll( const char* restrict str, char** restrict str_end, int base ); // (C99 起)
```

​	转换 str 所指的字节字符串中的整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的整数表示，并将它们转换成一个整数。合法的整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 8 或 0 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 16 或 0 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 0，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)。

​	函数设置 str_end 所指向的指针指向最后被转换字符的后一字符。若 str_end 为空指针，则忽略它。

​	若 str 为空或无期待的形式，则不进行转换，并（若 str_end 不是空指针）将 str 的值存储于 str_end 所指的对象。

**参数**

| str     | -    | 指向要被转换的空终止字符串的指针 |
| ------- | ---- | -------------------------------- |
| str_end | -    | 指向指向字符指针的指针           |
| base    | -    | 被转换整数的*底*                 |

**返回值**

- 若成功，则返回对应 str 内容的整数。
- 若被转换值落在对应返回类型的范围外，则发生值域错误（设 [errno](https://zh.cppreference.com/w/c/error/errno) 为 [ERANGE](https://zh.cppreference.com/w/c/error/errno_macros)）并返回 [LONG_MAX](https://zh.cppreference.com/w/c/types/limits)、[LONG_MIN](https://zh.cppreference.com/w/c/types/limits)、[LLONG_MAX](https://zh.cppreference.com/w/c/types/limits) 或 [LLONG_MIN](https://zh.cppreference.com/w/c/types/limits)。
- 若无法进行转换，则返回 0。

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




### strtold

原址：[https://zh.cppreference.com/w/c/string/byte/strtof](https://zh.cppreference.com/w/c/string/byte/strtof)

```c
float       strtof ( const char* restrict str, char** restrict str_end ); // (1)	(C99 起)
double      strtod ( const char*          str, char**          str_end ); // (2)	 (C99 前)
double      strtod ( const char* restrict str, char** restrict str_end ); // (2)	 (C99 前)
long double strtold( const char* restrict str, char** restrict str_end ); // (3)	(C99 起)
```

参见：[strtof](#strtof)










### strtoll

原址：[https://zh.cppreference.com/w/c/string/byte/strtol](https://zh.cppreference.com/w/c/string/byte/strtol)

```c
long      strtol( const char*          str, char**          str_end, int base ); // (C99 前)
long      strtol( const char* restrict str, char** restrict str_end, int base ); // (C99 起)
long long strtoll( const char* restrict str, char** restrict str_end, int base ); // (C99 起)
```

参见：[strtol](#strtol)










### strtoul

原址：[https://zh.cppreference.com/w/c/string/byte/strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul)

```c
unsigned long      strtoul( const char*          str, char**          str_end,
                            int base ); // (C99 前)
unsigned long      strtoul( const char* restrict str, char** restrict str_end,
                            int base ); // (C99 起)
unsigned long long strtoull( const char* restrict str, char** restrict str_end,
                             int base ); // (C99 起)
```

​	转换 str 所指的字符串中的无符号整数。

​	舍弃所有空白符（以调用 [`<sspac>`](https://zh.cppreference.com/w/c/string/byte/isspace) 鉴别），直到找到首个非空白符，然后取尽可能多的字符组成合法的*底 n* （其中 n=`base`）的无符号整数表示，并将它们转换成一个整数。合法的无符号整数由下列部分组成：

- (可选)正或负号
- (可选)指示八进制底的前缀（`0`）（仅当底为 8 或 0 时应用）
- (可选)指示十六进制底的前缀（`0x` 或 `0X`）（仅当底为 16 或 0 时应用）
- 数字序列

​	底的合法集是 `{0, 2, 3, ..., 36}`。合法数字集对于底 2 整数是 `{0, 1}`，对于底 3 整数是 `{0, 1, 2}`，以此类推。对于大于 `10` 的底，合法数字包含字母字符，从对于底 `11` 整数的 `Aa` 到对于底 `36` 整数的 `Zz`。忽略字符大小写。

​	当前安装的 C [本地环境](https://zh.cppreference.com/w/c/locale/setlocale)可能接受另外的数字格式。

​	如果 `base` 是 0，那么自动检测数值进制：如果前缀是 `0`，那么底是八进制，如果前缀是 `0x` 或 `0X`，那么底是十六进制，否则底是十进制。

​	如果符号是输入序列的一部分，那么对从数字序列计算得来的数字值取反，如同用结果类型的[一元减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E4.B8.80.E5.85.83.E7.AE.97.E6.9C.AF)，它对无符号整数应用回绕规则。

​	函数设置 str_end 所指向的指针指向最后一个被转换字符的后一字符。若 str_end 为空指针，则忽略它。

**参数**

| str     | -    | 指向要被转换的空终止字符串的指针 |
| ------- | ---- | -------------------------------- |
| str_end | -    | 指向指向字符的指针的指针         |
| base    | -    | 被转换整数的*底*                 |

**返回值**

​	成功时为对应 str 内容的整数。若被转换值落在对应返回类型的范围外，则发生值域错误（[errno](https://zh.cppreference.com/w/c/error/errno) 被设为 `ERANGE`）并返回 [ULONG_MAX](https://zh.cppreference.com/w/c/types/limits) 或 [ULLONG_MAX](https://zh.cppreference.com/w/c/types/limits)。若无转换可进行，则返回 0。

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




### strtoull

原址：[https://zh.cppreference.com/w/c/string/byte/strtoul](https://zh.cppreference.com/w/c/string/byte/strtoul)

```c
unsigned long      strtoul( const char*          str, char**          str_end,
                            int base ); // (C99 前)
unsigned long      strtoul( const char* restrict str, char** restrict str_end,
                            int base ); // (C99 起)
unsigned long long strtoull( const char* restrict str, char** restrict str_end,
                             int base ); // (C99 起)
```

参见：[strtoul](#strtoul)










### system

原址：[https://zh.cppreference.com/w/c/program/system](https://zh.cppreference.com/w/c/program/system)

```c
int system( const char *command );
```

​	以参数 `command` 调用宿主环境的命令处理器。返回实现定义值（通常是被调用程序所返回的值）。

​	若 `command` 是空指针，则检查宿主环境是否有命令处理器，并若且仅若命令处理器存在才返回非零。

**参数**

| command | -    | 标识要运行于命令处理器的命令的字符串。若给出空指针，则检查其存在性 |
| ------- | ---- | ------------------------------------------------------------ |

**返回值**

​	实现定义值。若 `command` 为空指针，则当且仅当命令处理器存在才返回非零值。

**注意**

​	POSIX 系统上，可用 [`WEXITSTATUS` 和 `WSTOPSIG`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/wait.html) 分解返回值。

​	相关的 POSIX 函数 [popen](http://pubs.opengroup.org/onlinepubs/9699919799/functions/popen.html) 令 `command` 生成的输出对调用方可用。

**示例**

​	此示例中有 unix 命令 **date +%A** 的系统调用，以及（可能安装的）**gcc** 编译器附带命令行参数（*`--version`*）的系统调用：

```c
#include <stdlib.h>
 
int main(void) {
    system("date +%A");
    system("gcc --version");
}
```

可能的输出：

```txt
Wednesday
gcc (GCC) 11.2.0
```




### wcstombs

原址：[https://zh.cppreference.com/w/c/string/multibyte/wcstombs](https://zh.cppreference.com/w/c/string/multibyte/wcstombs)

```c
size_t wcstombs( char          *dst, const wchar_t          *src, size_t len ); // (C99 前)
size_t wcstombs( char *restrict dst, const wchar_t *restrict src, size_t len ); // (C99 起)
errno_t wcstombs_s( size_t *restrict retval, char *restrict dst, rsize_t dstsz,
                    const wchar_t *restrict src, rsize_t len ); // (2)	(C11 起)
```

1）将来自首元素为 `src` 所指向的数组中的宽字符序列为其窄多字节表示，其始于初始迁移状态。转换出的各字符被存储于 `dst` 所指向的数组的相继元素。写入目标数组的字节数不多于 `len`。

 如同以调用 [wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb) 来转换每个字符，但 wctomb 的转换状态不受影响。若满足下列条件则转换停止：

- 转换并存储空字符 `L'\0'`。此情况下存储的各字节为无迁移序列（若需要）后随 `'\0'`，

- 找到当前 C 本地环境中不对应合法字符的 `wchar_t`。

- 下个要存储的多字节字符会超出 `len`。

 若 `src` 与 `dst` 重叠，则行为未指定。

2）同 (1)，但

- 转换如同以 [wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb) 而非 [wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb) 进行

- 函数将其结果作为输出参数 `retval` 返回

- 若转换停止而不写入控制符，则函数将在 `dst` 中的下个字符，可以是 `dst[len]` 或 `dst[dstsz]` 的先到来者，存储 `'\0'`（（表示可能写入总计至多 len+1/dsz+1 个字符）。该情况下，空终止前不写入无迁移序列。

- 若 `dst` 是空指针，则将本会产生的字节数存储于 `*retva`l

- 函数从空终止起到 `dstsz` 前为止破坏目标数组

- 若 `src` 与 `dst` 重叠，则行为未指定。

- 在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：
  - `retval` 或 `src` 是空指针
  - `dstsz` 或 `len` 大于 RSIZE_MAX（除非 `dst` 为空）
  - `dstsz` 非零（除非 `dst` 为空）
  - `len` 大于 `dstsz` 且直到抵达 `dstsz` 时，转换未于 `src` 数组遇到空字符或编码错误（除非 `dst` 为空）

​	同所有边界检查函数，`wcstombs_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。



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

1）成功时，返回写入首元素为 `dst` 所指向的字符数组的字节数（包含任何迁移序列，但不含终止的`'\0'`）。转换错误时（若遇到非法宽字符），返回 ([size_t](http://zh.cppreference.com/w/c/types/size_t))-1。

2）成功时返回零（该情况下，将被或本应写入 `dst` 的字节数，排除终止零，存储于 `*retval`），错误时返回非零。运行时制约违规的情况下，存储 ([size_t](http://zh.cppreference.com/w/c/types/size_t))-1 于 `*retval`（除非 `retval` 为空）并设置 `dst[0]` 为 `'\0'`（除非 `dst` 为空或 `dstmax` 为零或大于 RSIZE_MAX）。

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




### wcstombs_s

原址：[https://zh.cppreference.com/w/c/string/multibyte/wcstombs](https://zh.cppreference.com/w/c/string/multibyte/wcstombs)

```c
size_t wcstombs( char          *dst, const wchar_t          *src, size_t len ); // (C99 前)
size_t wcstombs( char *restrict dst, const wchar_t *restrict src, size_t len ); // (C99 起)
errno_t wcstombs_s( size_t *restrict retval, char *restrict dst, rsize_t dstsz,
                    const wchar_t *restrict src, rsize_t len ); // (2)	(C11 起)
```

参见：[wcstombs](#wcstombs)










### wctomb

原址：[https://zh.cppreference.com/w/c/string/multibyte/wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb)

```c
int wctomb( char *s, wchar_t wc ); // (1)	
errno_t wctomb_s(int *restrict status, char *restrict s, rsize_t ssz, wchar_t wc); // (2)	(C11 起)
```

1）转换宽字符 `wc` 为多字节编码，并将之（含迁移状态）存储于 `s` 指向其首元素的字符数组。存储字节数不多于 MB_CUR_MAX。转换受到当前安装的本地环境的 LC_CTYPE 类别的影响。

-  若 `wc` 是空字符，则将空字符写入 `s`，之前可以有需要恢复初始迁移状态的任何迁移状态。
- 若 `s` 是空指针，则此函数重设全局转换状态并确定是否使用迁移序列。

2）同 (1)，除了结果被返回到输出参数 `status`，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

- `ssz` 小于会被写入的字节数（除非 `s` 为空）
- `ssz` 大于 RSIZE_MAX（除非 `s` 为空）
- `s` 为空指针但 `ssz` 非零

​	同所有边界检查函数，`wctomb_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<stdlib.h>`](https://zh.cppreference.com/w/c/header/stdlib) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

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

1）若 `s` 非空指针，则返回 `wc` 的多字节表示所含的字节数，或者若 `wc` 非合法字符则为 -1。

 若 `s` 是空指针，则重设内部转换状态以表示初始迁移状态，并若当前多字节编码非状态依赖（不使用迁移序列）则返回 0，或者若当前多字节编码为状态依赖（使用迁移序列）则返回非零值。

2）成功时为零，此情况下存储 `wc` 的多字节表示于 `s`，并存储其长度于 `*status`，或若 `s` 为空，则存储迁移序列状态于 `*status`。编码错误或运行时制约错误发生时为非零，此情况下存储 ([size_t](http://zh.cppreference.com/w/c/types/size_t))-1 于 `*status`。存储于 `*status` 的值决不超过 MB_CUR_MAX。

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




### wctomb_s

原址：[https://zh.cppreference.com/w/c/string/multibyte/wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb)

```c
int wctomb( char *s, wchar_t wc ); // (1)	
errno_t wctomb_s(int *restrict status, char *restrict s, rsize_t ssz, wchar_t wc); // (2)	(C11 起)
```

参见：[wctomb](#wctomb)



