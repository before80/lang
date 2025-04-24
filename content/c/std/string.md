
+++
title = "<string.h>"
date = 2025-04-24T18:57:06+08:00
weight = 250
type = "docs"
description = "字符串处理"
isCJKLanguage = true
draft = false

+++

## 类型



### size_t

原址：[https://zh.cppreference.com/w/c/types/size_t](https://zh.cppreference.com/w/c/types/size_t)

作用：sizeof 运算符返回的无符号整数类型  (typedef)

备注：
```c
// 在标头 <stddef.h> 定义
// 在标头 <stdio.h> 定义
// 在标头 <stdlib.h> 定义
// 在标头 <string.h> 定义
// 在标头 <time.h> 定义
// 在标头 <uchar.h> 定义
// 在标头 <wchar.h> 定义
typedef /* 由实现定义 */ size_t;
```

​	`size_t` 是 [offsetof](https://zh.cppreference.com/w/c/types/offsetof)、[`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 和 `_Alignof`(C23 前)`alignof`(C23 起) 的结果的无符号整数类型，定义取决于[数据模型](https://zh.cppreference.com/w/c/language/arithmetic_types#.E6.95.B0.E6.8D.AE.E6.A8.A1.E5.9E.8B)。

​	`size_t` 的位宽不小于 16。 (C99 起)

**注解**

​	`size_t` 能存储理论上可行的任何类型（包括数组）对象的最大大小。

​	`size_t` 通常用于数组下标和循环计数。将如 `unsigned int` 的其他类型用作数组下标的的程序，可能譬如在 64 位系统上，当下标超过 [UINT_MAX](https://zh.cppreference.com/w/c/types/limits) 时，或若其依赖 32 位模算术时失败。

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

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.19 Common definitions <stddef.h> （第 TBD 页）

  - 7.20.3 Limits of other integer types （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.19 Common definitions <stddef.h> （第 211 页）

  - 7.20.3 Limits of other integer types （第 215 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.19 Common definitions <stddef.h> （第 288 页）

  - 7.20.3 Limits of other integer types （第 293 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.17 Common definitions <stddef.h> （第 253 页）

  - 7.18.3 Limits of other integer types （第 258 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.1.6 Common definitions <stddef.h>

**参阅**

| [ptrdiff_t<br />](https://zh.cppreference.com/w/c/types/ptrdiff_t) | 两个指针相减返回的有符号整数类型 (typedef)      |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [offsetof<br />](https://zh.cppreference.com/w/c/types/offsetof) | 从结构体类型的起始到指定成员的字节偏移 (宏函数) |
| **size_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/size_t)** |                                                 |






## 枚举




## 宏



### NULL

原址：[https://zh.cppreference.com/w/c/types/NULL](https://zh.cppreference.com/w/c/types/NULL)

作用：实现定义的空指针常量  (宏常量)

备注：
```c
// 在标头 <locale.h> 定义
// 在标头 <stddef.h> 定义
// 在标头 <stdio.h> 定义
// 在标头 <stdlib.h> 定义
// 在标头 <string.h> 定义
// 在标头 <time.h> 定义
// 在标头 <wchar.h> 定义
#define NULL /* 由实现定义 */
```

​	宏 `NULL` 是实现定义的空指针常量，可为

- 值为 `0` 的整数[常量表达式](https://zh.cppreference.com/w/c/language/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F)
- [转换为](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2) `void*` 的值为 `0` 的整数常量表达式



- 预定义常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr)

(C23 起)



​	空指针常量能[转换](https://zh.cppreference.com/w/c/language/conversion#.E6.8C.87.E9.92.88.E8.BD.AC.E6.8D.A2)为任何指针类型；转换结果是该类型的空指针值。

**注解**

​	[POSIX 要求](https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/stddef.h.html) `NULL` 被定义为转换为 `void*` 的值为 `0` 的整数常量表达式。

**可能的实现**

```c
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

**参阅**

| [nullptr_t (C23)<br />](https://zh.cppreference.com/w/c/types/nullptr_t) | 预定义空指针常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr) 的类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **NULL** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/NULL)** |                                                              |





### __STDC_VERSION_STRING_H__

原址：

作用：

备注：






## 函数



### memccpy

原址：[https://zh.cppreference.com/w/c/string/byte/memccpy](https://zh.cppreference.com/w/c/string/byte/memccpy)

作用：复制缓冲区到另一个，在指定的分隔符后停止   (函数)

备注：
```c
// 在标头 <string.h> 定义
void* memccpy( void* restrict dest, const void* restrict src, int c, size_t count );// (C23 起)
```

​	从 `src` 所指向的对象复制字节到 `dest` 所指向的对象，在满足以下两个条件*任何一个* ﻿后停止：

  - 复制了 `count` 个字节
  - 找到（并复制）了字节 `(unsigned char)c`。

​	转译 `src` 与 `dest` 对象为 `unsigned char` 的数组。

​	若符合以下条件*任何一个* ﻿则行为未定义：

  - 出现越过数组 `dest` 结尾的访问
  - 对象重叠（这违反 [`<estric>`](https://zh.cppreference.com/w/c/language/restrict) 契约）
  - `dest` 或 `src` 为非法或空指针值

**参数**

| dest  | -    | 指向要复制的对象的指针               |
| ----- | ---- | ------------------------------------ |
| src   | -    | 指向复制来源对象的指针               |
| c     | -    | 终止字节，首先转换成 `unsigned char` |
| count | -    | 要复制的字节数                       |

**返回值**

​	若找到字节 `(unsigned char)c` 则 `memccpy` 返回 `dest` 中 `(unsigned char)c` 后一字节的指针，否则返回空指针。

**注解**

​	函数等同于 [POSIX memccpy](https://pubs.opengroup.org/onlinepubs/9699919799/functions/memccpy.html)。

​	`memccpy(dest, src, 0, count)` 行为类似于 `[strncpy](http://zh.cppreference.com/w/c/string/byte/strncpy)(dest, src, count)`，但前者返回指向被写入缓冲区的*末尾* ﻿的指针，并且不会以零填充目标数组。因而 `memccpy` 对高效连接多个字符串有用。

```c
char bigString[1000];
char* end = bigString + sizeof bigString;
 
char* p = memccpy(bigString, "John, ", '\0', sizeof bigString - 1);
if (p)
    p = memccpy(p - 1, "Paul, ", '\0', end - p);
if (p)
    p = memccpy(p - 1, "George, ", '\0', end - p);
if (p)
    p = memccpy(p - 1, "Joel ", '\0', end - p);
if (!p)
    end[-1] = '\0';
 
puts(bigString); // John, Paul, George, Joel
```

**示例**

```c
#include <ctype.h>
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char src[] = "Stars: Altair, Sun, Vega.";
    const char terminal[] = {':', ' ', ',', '.', '!'};
    char dest[sizeof src];
    const char alt = '@';
 
    for (size_t i = 0; i != sizeof terminal; ++i) {
 
        void *to = memccpy(dest, src, terminal[i], sizeof dest);
 
        printf("Terminal '%c' (%s):\t\"", terminal[i], to ? "found" : "absent");
 
        // 若找不到 `terminal` 字符 - 打印整个 `dest`
        to = to ? to : dest + sizeof dest;
 
        for (char *from = dest; from != to; ++from)
            putchar(isprint(*from) ? *from : alt);
 
        puts("\"");
    }
 
 
    puts("\n" "Separate star names from distances (ly):");
    const char *star_distance[] = {
        "Arcturus : 37", "Vega : 25", "Capella : 43", "Rigel : 860", "Procyon : 11"
    };
    char names_only[64];
    char *first = names_only;
    char *last = names_only + sizeof names_only;
 
    for (size_t t = 0; t != (sizeof star_distance) / (sizeof star_distance[0]); ++t)
    {
        if (first)
            first = memccpy(first, star_distance[t], ' ', last - first);
        else
            break;
    }
 
    if (first)
    {
        *first = '\0';
        puts(names_only);
    }
    else
        puts("Buffer is too small.");
}
```

​	输出：

```txt
Terminal ':' (found):   "Stars:"
Terminal ' ' (found):   "Stars: "
Terminal ',' (found):   "Stars: Altair,"
Terminal '.' (found):   "Stars: Altair, Sun, Vega."
Terminal '!' (absent):  "Stars: Altair, Sun, Vega.@"
 
Separate star names from distances (ly):
Arcturus Vega Capella Rigel Procyon
```

**参阅**

| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                       |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [wmemcpy (C95)<br />wmemcpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcpy) | 在两个不重叠的数组间复制一定数量的宽字符 (函数) |
| [memmove <br />memmove_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memmove) | 移动缓冲区到另一个 (函数)                       |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                       |
| [strcat <br />strcat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcat) | 连接两个字符串 (函数)                           |





### memchr

原址：[https://zh.cppreference.com/w/c/string/byte/memchr](https://zh.cppreference.com/w/c/string/byte/memchr)

作用：在数组中搜索字符的首次出现  (函数)

备注：
```c
// 在标头 <string.h> 定义
void* memchr( const void* ptr, int ch, size_t count );// (1)
/*QVoid*/ *memchr( /*QVoid*/ *ptr, int ch, size_t count );// (2)(C23 起)
```

1） 在 `ptr` 所指向对象的起始 `count` 个字节（均转译成 `unsigned char`）中寻找首次出现的 `(unsigned char)ch`。

2） 等价于 (1) 的泛型函数。令 `T` 为未限定的 对象类型（包括 `void`）。

  - 若 `ptr` 类型为 `const T*`，则返回类型为 `const void*`。
  - 否则，若 `ptr` 类型为 `T*`，返回类型为 `void*`。
  - 否则，行为未定义。

如果这些泛型函数中的某个宏定义被抑制无法访问实际函数（比如当使用了 `(memchr)` 或使用了函数指针时），则实际函数声明 (1) 即变得可见。

​	若在所搜索的数组结尾后发生访问，则行为未定义。若 `ptr` 为空指针则行为未定义。

​	此函数表现如同它按顺序读取字节，并于找到匹配的字节时立即停止：若 `ptr` 所指向的字节数组小于 `count`，但在数组中找到匹配，则行为良定义。 (C11 起)

**参数**

| ptr   | -    | 指向要检验的对象的指针 |
| ----- | ---- | ---------------------- |
| ch    | -    | 要搜索的字节           |
| count | -    | 要检验的最大字节数     |

**返回值**

​	指向字节位置的指针，或若找不到该字节则为空指针。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char str[] = "ABCDEFG";
    const int chars[] = {'D', 'd'};
    for (size_t i = 0; i < sizeof chars / (sizeof chars[0]); ++i)
    {
        const int c = chars[i];
        const char *ps = memchr(str, c, strlen(str));
        ps ? printf ("找到字符 '%c'(%i): %s\n", c, c, ps)
           : printf ("未找到字符 '%c'(%i)\n", c, c);
    }
    return 0;
}
```

​	可能的输出：

```txt
找到字符 'D'(68): DEFG
未找到字符 'd'(100)
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.1 The memchr function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.1 The memchr function （第 267-268 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.1 The memchr function （第 367 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.1 The memchr function （第 330 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.1 The memchr function

**参阅**

| [strchr<br />](https://zh.cppreference.com/w/c/string/byte/strchr) | 查找字符的首次出现 (函数) |
| ------------------------------------------------------------ | ------------------------- |
| **memchr** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memchr)** |                           |





### memcmp

原址：[https://zh.cppreference.com/w/c/string/byte/memcmp](https://zh.cppreference.com/w/c/string/byte/memcmp)

作用：比较两块缓冲区  (函数)

备注：
```c
// 在标头 <string.h> 定义
int memcmp( const void* lhs, const void* rhs, size_t count );
```

​	比较 `lhs` 和 `rhs` 所指向对象的开头 `count` 个字节。按字典序进行比较。

​	结果的符号是在被比较对象中相异的首对字节的值（都转译成 `unsigned char`）之差的符号。

​	若在 `lhs` 和 `rhs` 所指向的任一对象结尾后发生访问，则行为未定义。若 `lhs` 或 `rhs` 为空指针则行为未定义。

**参数**

| lhs, rhs | -    | 指向要比较的对象的指针 |
| -------- | ---- | ---------------------- |
| count    | -    | 要检验的字节数         |

**返回值**

​	若 `lhs` 按字典序先于 `rhs` 出现，则为负值。

​	若 `lhs` 与 `rhs` 比较相等，或 `count` 为零则为零。

​	若 `lhs` 按字典序晚于 `rhs` 出现，则为正值。

**注解**

​	此函数读取[对象表示](https://zh.cppreference.com/w/c/language/object)，而非对象值，而且典型地只对字节数组有意义：结构体可以含有填充字节而其值不确定，存储于联合体最近存储成员后的任何字节的值是不确定的，且一个类型可以对相同值拥有二种或多种表示（对于 `+0` 和 `-0` 或 `+0.0` 和 `–0.0` 的相异编码、类型中不确定填充位）。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
void demo(const char* lhs, const char* rhs, size_t sz)
{
    for (size_t n = 0; n < sz; ++n)
        putchar(lhs[n]);
 
    int rc = memcmp(lhs, rhs, sz);
    const char *rel = rc < 0 ? " precedes " : rc > 0 ? " follows " : " compares equal ";
    fputs(rel, stdout);
 
    for (size_t n = 0; n < sz; ++n)
        putchar(rhs[n]);
    puts(" in lexicographical order");
}
 
int main(void)
{
    char a1[] = {'a','b','c'};
    char a2[sizeof a1] = {'a','b','d'};
 
    demo(a1, a2, sizeof a1);
    demo(a2, a1, sizeof a1);
    demo(a1, a1, sizeof a1);
}
```

​	输出：

```txt
abc precedes abd in lexicographical order
abd follows abc in lexicographical order
abc compares equal to abc in lexicographical order
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.4.1 The memcmp function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.4.1 The memcmp function （第 266 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.4.1 The memcmp function （第 365 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.4.1 The memcmp function （第 328 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.4.1 The memcmp function

**参阅**

| [strcmp<br />](https://zh.cppreference.com/w/c/string/byte/strcmp) | 比较两个字符串 (函数)               |
| ------------------------------------------------------------ | ----------------------------------- |
| [strncmp<br />](https://zh.cppreference.com/w/c/string/byte/strncmp) | 比较两个字符串的一定数量字符 (函数) |
| **memcmp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memcmp)** |                                     |





### memcpy

原址：[https://zh.cppreference.com/w/c/string/byte/memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy)

作用：复制缓冲区到另一个  (函数)

备注：
```c
// 在标头 <string.h> 定义
// (1)
void* memcpy( void *dest, const void *src, size_t count );// (C99 前)
void* memcpy( void *restrict dest, const void *restrict src, size_t count );// (C99 起)
errno_t memcpy_s( void *restrict dest, rsize_t destsz,
                  const void *restrict src, rsize_t count );// (2)(C11 起)
```

1） 从 `src` 所指向的对象复制 `count` 个字符到 `dest` 所指向的对象。两个对象都被转译成 `unsigned char` 的数组。

 若在 `dest` 数组结尾后发生访问，则行为未定义。若对象重叠（这违背 [`<estric>`](https://zh.cppreference.com/w/c/language/restrict) 契约）(C99 起)，则行为未定义。若 `dest` 或 `src` 为非法或空指针则行为未定义。

2） 同 (1)，除了错误时导致清零整个目标范围 `[dest, dest+destsz)`（若 `dest` 与 `destsz` 均合法），它在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 或 `src` 为空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会发生缓冲区溢出）
  - 源和目标对象重叠

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz` 则行为未定义；换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向复制目标对象的指针                             |
| ------ | ---- | -------------------------------------------------- |
| destsz | -    | 目标中要修改的最大字节数（典型地为目标对象的大小） |
| src    | -    | 指向复制来源对象的指针                             |
| count  | -    | 复制的字节数                                       |

**返回值**

1） 返回 `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是 `dest` 本身。

2） 成功时返回零，错误时返回非零。在错误时，若 `dest` 不是空指针且 `destsz` 合法，则还会写入 `destsz` 个零字节到目标数组。

**注解**

​	`memcpy` 可用于设置分配函数所获得对象的[有效类型](https://zh.cppreference.com/w/c/language/object#.E6.9C.89.E6.95.88.E7.B1.BB.E5.9E.8B)。

​	`memcpy` 是最快的内存到内存复制子程序。它通常比必须扫描其所复制数据的 [strcpy](https://zh.cppreference.com/w/c/string/byte/strcpy)，或必须预防以处理重叠输入的 [memmove](https://zh.cppreference.com/w/c/string/byte/memmove) 更高效。

​	许多 C 编译器将适合的内存复制循环变换为 `memcpy` 调用。

​	在[严格别名使用](https://zh.cppreference.com/w/c/language/object#.E4.B8.A5.E6.A0.BC.E5.88.AB.E5.90.8D.E4.BD.BF.E7.94.A8)禁止检验同一内存为二个不同类型的值处，可用 `memcpy` 转换值。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <stdint.h>
#include <inttypes.h>
#include <string.h>
#include <stdlib.h>
 
int main(void)
{
    // 简单用法
    char source[] = "once upon a midnight dreary...", dest[4];
    memcpy(dest, source, sizeof dest);
    for(size_t n = 0; n < sizeof dest; ++n)
        putchar(dest[n]);
 
    // 设置分配的内存的有效类型为 int
    int *p = malloc(3*sizeof(int));   // 分配的内存无有效类型
    int arr[3] = {1,2,3};
    memcpy(p,arr,3*sizeof(int));      // 分配的内存现在拥有有效类型
 
    // reinterpreting data
    double d = 0.1;
//    int64_t n = *(int64_t*)(&d); // 严格别名使用违规
    int64_t n;
    memcpy(&n, &d, sizeof d); // OK
    printf("\n%a is %" PRIx64 " as an int64_t\n", d, n);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char src[] = "aaaaaaaaaa";
    char dst[] = "xyxyxyxyxy";
    int r = memcpy_s(dst,sizeof dst,src,5);
    printf("dst = \"%s\", r = %d\n", dst,r);
    r = memcpy_s(dst,5,src,10);            // count 大于 destsz  
    printf("dst = \"");
    for(size_t ndx=0; ndx<sizeof dst; ++ndx) {
        char c = dst[ndx];
        c ? printf("%c", c) : printf("\\0");
    }
    printf("\", r = %d\n", r);
#endif
}
```

​	可能的输出：

```txt
once
0x1.999999999999ap-4 is 3fb999999999999a as an int64_t
dst = "aaaaayxyxy", r = 0
dst = "\0\0\0\0\0yxyxy", r = 22
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.1 The memcpy function （第 362 页）

  - K.3.7.1.1 The memcpy_s function （第 614 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.1 The memcpy function （第 325 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.1 The memcpy function

**参阅**

| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [memmove <br />memmove_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memmove) | 移动缓冲区到另一个 (函数)                       |
| [wmemcpy (C95)<br />wmemcpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcpy) | 在两个不重叠的数组间复制一定数量的宽字符 (函数) |
| **memcpy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memcpy)** |                                                 |





### memcpy_s

原址：[https://zh.cppreference.com/w/c/string/byte/memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy)

作用：复制缓冲区到另一个  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
// (1)
void* memcpy( void *dest, const void *src, size_t count );// (C99 前)
void* memcpy( void *restrict dest, const void *restrict src, size_t count );// (C99 起)
errno_t memcpy_s( void *restrict dest, rsize_t destsz,
                  const void *restrict src, rsize_t count );// (2)(C11 起)
```

1） 从 `src` 所指向的对象复制 `count` 个字符到 `dest` 所指向的对象。两个对象都被转译成 `unsigned char` 的数组。

 若在 `dest` 数组结尾后发生访问，则行为未定义。若对象重叠（这违背 [`<estric>`](https://zh.cppreference.com/w/c/language/restrict) 契约）(C99 起)，则行为未定义。若 `dest` 或 `src` 为非法或空指针则行为未定义。

2） 同 (1)，除了错误时导致清零整个目标范围 `[dest, dest+destsz)`（若 `dest` 与 `destsz` 均合法），它在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 或 `src` 为空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会发生缓冲区溢出）
  - 源和目标对象重叠

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz` 则行为未定义；换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向复制目标对象的指针                             |
| ------ | ---- | -------------------------------------------------- |
| destsz | -    | 目标中要修改的最大字节数（典型地为目标对象的大小） |
| src    | -    | 指向复制来源对象的指针                             |
| count  | -    | 复制的字节数                                       |

**返回值**

1） 返回 `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是 `dest` 本身。

2） 成功时返回零，错误时返回非零。在错误时，若 `dest` 不是空指针且 `destsz` 合法，则还会写入 `destsz` 个零字节到目标数组。

**注解**

​	`memcpy` 可用于设置分配函数所获得对象的[有效类型](https://zh.cppreference.com/w/c/language/object#.E6.9C.89.E6.95.88.E7.B1.BB.E5.9E.8B)。

​	`memcpy` 是最快的内存到内存复制子程序。它通常比必须扫描其所复制数据的 [strcpy](https://zh.cppreference.com/w/c/string/byte/strcpy)，或必须预防以处理重叠输入的 [memmove](https://zh.cppreference.com/w/c/string/byte/memmove) 更高效。

​	许多 C 编译器将适合的内存复制循环变换为 `memcpy` 调用。

​	在[严格别名使用](https://zh.cppreference.com/w/c/language/object#.E4.B8.A5.E6.A0.BC.E5.88.AB.E5.90.8D.E4.BD.BF.E7.94.A8)禁止检验同一内存为二个不同类型的值处，可用 `memcpy` 转换值。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <stdint.h>
#include <inttypes.h>
#include <string.h>
#include <stdlib.h>
 
int main(void)
{
    // 简单用法
    char source[] = "once upon a midnight dreary...", dest[4];
    memcpy(dest, source, sizeof dest);
    for(size_t n = 0; n < sizeof dest; ++n)
        putchar(dest[n]);
 
    // 设置分配的内存的有效类型为 int
    int *p = malloc(3*sizeof(int));   // 分配的内存无有效类型
    int arr[3] = {1,2,3};
    memcpy(p,arr,3*sizeof(int));      // 分配的内存现在拥有有效类型
 
    // reinterpreting data
    double d = 0.1;
//    int64_t n = *(int64_t*)(&d); // 严格别名使用违规
    int64_t n;
    memcpy(&n, &d, sizeof d); // OK
    printf("\n%a is %" PRIx64 " as an int64_t\n", d, n);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char src[] = "aaaaaaaaaa";
    char dst[] = "xyxyxyxyxy";
    int r = memcpy_s(dst,sizeof dst,src,5);
    printf("dst = \"%s\", r = %d\n", dst,r);
    r = memcpy_s(dst,5,src,10);            // count 大于 destsz  
    printf("dst = \"");
    for(size_t ndx=0; ndx<sizeof dst; ++ndx) {
        char c = dst[ndx];
        c ? printf("%c", c) : printf("\\0");
    }
    printf("\", r = %d\n", r);
#endif
}
```

​	可能的输出：

```txt
once
0x1.999999999999ap-4 is 3fb999999999999a as an int64_t
dst = "aaaaayxyxy", r = 0
dst = "\0\0\0\0\0yxyxy", r = 22
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.1 The memcpy function （第 362 页）

  - K.3.7.1.1 The memcpy_s function （第 614 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.1 The memcpy function （第 325 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.1 The memcpy function

**参阅**

| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [memmove <br />memmove_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memmove) | 移动缓冲区到另一个 (函数)                       |
| [wmemcpy (C95)<br />wmemcpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcpy) | 在两个不重叠的数组间复制一定数量的宽字符 (函数) |
| **memcpy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memcpy)** |                                                 |
`__STDC_WANT_LIB_EXT1__`：






### memmove

原址：[https://zh.cppreference.com/w/c/string/byte/memmove](https://zh.cppreference.com/w/c/string/byte/memmove)

作用：移动缓冲区到另一个  (函数)

备注：
```c
// 在标头 <string.h> 定义
void* memmove( void* dest, const void* src, size_t count );// (1)
errno_t memmove_s(void* dest, rsize_t destsz, const void* src, rsize_t count);// (2)(C11 起)
```

1） 从 `src` 所指向的对象复制 `count` 个字节到 `dest` 所指向的对象。两个对象都被转译成 `unsigned char` 的数组。对象可以重叠：如同复制字符到临时数组，再从该数组到 `dest` 一般进行复制。

 若在 dest 数组末尾之后发生访问则行为未定义。若 `dest` 或 `src` 为非法或空指针则行为未定义。

2） 同 (1)，但错误时清零整个范围 `[dest, dest+destsz)`（若 `dest` 和 `destsz` 均合法）。它在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 或 `src` 为空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会出现溢出）

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz` 则行为未定义；换言之，`destsz` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向复制目标对象的指针                             |
| ------ | ---- | -------------------------------------------------- |
| destsz | -    | 要于目标修改的最大字节数（典型地为目标对象的大小） |
| src    | -    | 指向复制来源对象的指针                             |
| count  | -    | 要复制的字节数                                     |

**返回值**

1） 返回 `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是dest本身。

2） 成功时返回零，失败时返回非零值。在失败时，若 `dest` 不是空指针且 `destsz` 合法，则亦会写入 `destsz` 个零字节到目标数组。

**注解**

​	`memmove` 可用于设置由分配函数获得的对象的[有效类型](https://zh.cppreference.com/w/c/language/object#.E6.9C.89.E6.95.88.E7.B1.BB.E5.9E.8B)。

​	尽管说明了“如同”使用临时缓冲区，此函数的实际实现不会带来二次复制或额外内存的开销。常用方法（glibc 和 bsd libc）是若目标在源之前开始，则从缓冲区开始正向复制，否则从末尾反向复制，完全无重叠时回落到更高效的 [memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy)。

​	在[严格别名使用](https://zh.cppreference.com/w/c/language/object#.E4.B8.A5.E6.A0.BC.E5.88.AB.E5.90.8D.E4.BD.BF.E7.94.A8)禁止检验同一内存为二个不同类型的值时，可使用 `memmove` 转换值。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <inttypes.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
int main(void)
{
    char str[] = "1234567890";
    puts(str);
    memmove(str + 4, str + 3, 3); // 从 [4,5,6] 复制到 [5,6,7]
    puts(str);
 
    // 设置分配的内存的有效类型为 int
    int *p = malloc(3*sizeof(int)); // 分配的内存无有效类型
    int arr[3] = {1, 2, 3};
    memmove(p,arr,3*sizeof(int)); // 分配的内存现在拥有有效类型
 
    // 转译数据
    double d = 0.1;
    // int64_t n = *(int64_t*)(&d); // 严格别名使用违规
    int64_t n;
    memmove(&n, &d, sizeof d); // OK
    printf("%a 作为 int64_t 为 %" PRIx64 "\n", d, n);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char src[] = "aaaaaaaaaa";
    char dst[] = "xyxyxyxyxy";
    int r = memmove_s(dst, sizeof dst, src, 5);
    printf("dst = \"%s\", r = %d\n", dst, r);
    r = memmove_s(dst, 5, src, 10); // count 大于 destsz  
    printf("dst = \"");
    for (size_t ndx = 0; ndx < sizeof dst; ++ndx)
    {
        char c = dst[ndx];
        c ? printf("%c", c) : printf("\\0");
    }
    printf("\", r = %d\n", r);
#endif
}
```

​	可能的输出：

```txt
1234567890
1234456890
0x1.999999999999ap-4 作为 int64_t 为 3fb999999999999a
dst = "aaaaayxyxy", r = 0
dst = "\0\0\0\0\0yxyxy", r = 22
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.2 The memmove function （第 TBD 页）

  - K.3.7.1.2 The memmove_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.2 The memmove function （第 264 页）

  - K.3.7.1.2 The memmove_s function （第 446 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.2 The memmove function （第 363 页）

  - K.3.7.1.2 The memmove_s function （第 615 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.2 The memmove function （第 326 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.2 The memmove function

**参阅**

| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                         |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [wmemmove (C95)<br />wmemmove_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemmove) | 在两个可能重叠的数组间复制一定数量的宽字符 (函数) |
| **memmove** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memmove)** |                                                   |





### memmove_s

原址：[https://zh.cppreference.com/w/c/string/byte/memmove](https://zh.cppreference.com/w/c/string/byte/memmove)

作用：移动缓冲区到另一个  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
void* memmove( void* dest, const void* src, size_t count );// (1)
errno_t memmove_s(void* dest, rsize_t destsz, const void* src, rsize_t count);// (2)(C11 起)
```

1） 从 `src` 所指向的对象复制 `count` 个字节到 `dest` 所指向的对象。两个对象都被转译成 `unsigned char` 的数组。对象可以重叠：如同复制字符到临时数组，再从该数组到 `dest` 一般进行复制。

 若在 dest 数组末尾之后发生访问则行为未定义。若 `dest` 或 `src` 为非法或空指针则行为未定义。

2） 同 (1)，但错误时清零整个范围 `[dest, dest+destsz)`（若 `dest` 和 `destsz` 均合法）。它在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 或 `src` 为空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会出现溢出）

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz` 则行为未定义；换言之，`destsz` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向复制目标对象的指针                             |
| ------ | ---- | -------------------------------------------------- |
| destsz | -    | 要于目标修改的最大字节数（典型地为目标对象的大小） |
| src    | -    | 指向复制来源对象的指针                             |
| count  | -    | 要复制的字节数                                     |

**返回值**

1） 返回 `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是dest本身。

2） 成功时返回零，失败时返回非零值。在失败时，若 `dest` 不是空指针且 `destsz` 合法，则亦会写入 `destsz` 个零字节到目标数组。

**注解**

​	`memmove` 可用于设置由分配函数获得的对象的[有效类型](https://zh.cppreference.com/w/c/language/object#.E6.9C.89.E6.95.88.E7.B1.BB.E5.9E.8B)。

​	尽管说明了“如同”使用临时缓冲区，此函数的实际实现不会带来二次复制或额外内存的开销。常用方法（glibc 和 bsd libc）是若目标在源之前开始，则从缓冲区开始正向复制，否则从末尾反向复制，完全无重叠时回落到更高效的 [memcpy](https://zh.cppreference.com/w/c/string/byte/memcpy)。

​	在[严格别名使用](https://zh.cppreference.com/w/c/language/object#.E4.B8.A5.E6.A0.BC.E5.88.AB.E5.90.8D.E4.BD.BF.E7.94.A8)禁止检验同一内存为二个不同类型的值时，可使用 `memmove` 转换值。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <inttypes.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
int main(void)
{
    char str[] = "1234567890";
    puts(str);
    memmove(str + 4, str + 3, 3); // 从 [4,5,6] 复制到 [5,6,7]
    puts(str);
 
    // 设置分配的内存的有效类型为 int
    int *p = malloc(3*sizeof(int)); // 分配的内存无有效类型
    int arr[3] = {1, 2, 3};
    memmove(p,arr,3*sizeof(int)); // 分配的内存现在拥有有效类型
 
    // 转译数据
    double d = 0.1;
    // int64_t n = *(int64_t*)(&d); // 严格别名使用违规
    int64_t n;
    memmove(&n, &d, sizeof d); // OK
    printf("%a 作为 int64_t 为 %" PRIx64 "\n", d, n);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char src[] = "aaaaaaaaaa";
    char dst[] = "xyxyxyxyxy";
    int r = memmove_s(dst, sizeof dst, src, 5);
    printf("dst = \"%s\", r = %d\n", dst, r);
    r = memmove_s(dst, 5, src, 10); // count 大于 destsz  
    printf("dst = \"");
    for (size_t ndx = 0; ndx < sizeof dst; ++ndx)
    {
        char c = dst[ndx];
        c ? printf("%c", c) : printf("\\0");
    }
    printf("\", r = %d\n", r);
#endif
}
```

​	可能的输出：

```txt
1234567890
1234456890
0x1.999999999999ap-4 作为 int64_t 为 3fb999999999999a
dst = "aaaaayxyxy", r = 0
dst = "\0\0\0\0\0yxyxy", r = 22
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.2 The memmove function （第 TBD 页）

  - K.3.7.1.2 The memmove_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.2 The memmove function （第 264 页）

  - K.3.7.1.2 The memmove_s function （第 446 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.2 The memmove function （第 363 页）

  - K.3.7.1.2 The memmove_s function （第 615 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.2 The memmove function （第 326 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.2 The memmove function

**参阅**

| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                         |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [wmemmove (C95)<br />wmemmove_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemmove) | 在两个可能重叠的数组间复制一定数量的宽字符 (函数) |
| **memmove** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memmove)** |                                                   |
`__STDC_WANT_LIB_EXT1__`：






### memset

原址：[https://zh.cppreference.com/w/c/string/byte/memset](https://zh.cppreference.com/w/c/string/byte/memset)

作用：以字符填充缓冲区  (函数)

备注：
```c
// 在标头 <string.h> 定义
void *memset( void *dest, int ch, size_t count );// (1)
void *memset_explicit( void *dest, int ch, size_t count );// (2)(C23 起)
errno_t memset_s( void *dest, rsize_t destsz, int ch, rsize_t count );// (3)(C11 起)
```

1） 将值 `(unsigned char)ch` 复制到 `dest` 所指向对象的最前面 `count` 个字节中。

 若在 dest 数组结尾之后发生访问则行为未定义。若 `dest` 为空指针则行为未定义。

2） 同 (1)，但对敏感信息是安全的。

3） 同 (1)，但若 `dest` 与 `destsz` 自身有效，则存储 `ch` 于目标范围 `[dest, dest+destsz)` 的每个位置后，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 是空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会发生缓冲区溢出）

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz`; 则行为未定义，换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要填充的对象的指针 |
| ------ | ---- | ---------------------- |
| ch     | -    | 填充字节               |
| count  | -    | 要填充的字节数         |
| destsz | -    | 目标数组的大小         |

**返回值**

1,2) `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是dest本身。

3） 成功时为零，失败时为非零。在失败时，若 `dest` 不是空指针且 `destsz` 合法，则亦写入 `destsz` 个填充字节 `ch` 到目标数组。

**注解**

​	若 `memset` 所修改的对象在其生存期的剩余部分不再被访问，则此函数可以被优化掉（在[如同](https://zh.cppreference.com/w/c/language/as_if)规则下）（例如 [gcc 漏洞 8537](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=8537)）。为此，此函数不能用于擦洗内存（例如以零填充存储密码的数组）。

​	对 `memset_explicit` 和 `memset_s` 禁止此优化：保证进行内存写。

​	该问题的第三方解决方案包含 FreeBSD [explicit_bzero](https://www.freebsd.org/cgi/man.cgi?query=explicit_bzero) 或 Microsoft [SecureZeroMemory](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366877.aspx)。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
 
int main(void)
{
    char str[] = "ghghghghghghghghghghgh";
    puts(str);
    memset(str,'a',5);
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = memset_s(str, sizeof str, 'b', 5);
    printf("str = \"%s\", r = %d\n", str, r);
    r = memset_s(str, 5, 'c', 10);   // count 大于 destsz  
    printf("str = \"%s\", r = %d\n", str, r);
#endif
}
```

​	可能的输出：

```txt
ghghghghghghghghghghgh
aaaaahghghghghghghghgh
str = "bbbbbhghghghghghghghgh", r = 0
str = "ccccchghghghghghghghgh", r = 22
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.6.1 The memset function （第 270 页）

  - K.3.7.4.1 The memset_s function （第 451 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.1 The memset function （第 371 页）

  - K.3.7.4.1 The memset_s function （第 621-622 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.1 The memset function （第 333 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.1 The memset function

**参阅**

| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                     |
| ------------------------------------------------------------ | --------------------------------------------- |
| [wmemset (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemset) | 复制给定的宽字符到宽字符数组的所有位置 (函数) |
| **memset** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memset)** |                                               |





### memset_explicit

原址：[https://zh.cppreference.com/w/c/string/byte/memset](https://zh.cppreference.com/w/c/string/byte/memset)

作用：以字符填充缓冲区  (函数)

备注：
```c
// 在标头 <string.h> 定义
void *memset( void *dest, int ch, size_t count );// (1)
void *memset_explicit( void *dest, int ch, size_t count );// (2)(C23 起)
errno_t memset_s( void *dest, rsize_t destsz, int ch, rsize_t count );// (3)(C11 起)
```

1） 将值 `(unsigned char)ch` 复制到 `dest` 所指向对象的最前面 `count` 个字节中。

 若在 dest 数组结尾之后发生访问则行为未定义。若 `dest` 为空指针则行为未定义。

2） 同 (1)，但对敏感信息是安全的。

3） 同 (1)，但若 `dest` 与 `destsz` 自身有效，则存储 `ch` 于目标范围 `[dest, dest+destsz)` 的每个位置后，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 是空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会发生缓冲区溢出）

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz`; 则行为未定义，换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要填充的对象的指针 |
| ------ | ---- | ---------------------- |
| ch     | -    | 填充字节               |
| count  | -    | 要填充的字节数         |
| destsz | -    | 目标数组的大小         |

**返回值**

1,2) `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是dest本身。

3） 成功时为零，失败时为非零。在失败时，若 `dest` 不是空指针且 `destsz` 合法，则亦写入 `destsz` 个填充字节 `ch` 到目标数组。

**注解**

​	若 `memset` 所修改的对象在其生存期的剩余部分不再被访问，则此函数可以被优化掉（在[如同](https://zh.cppreference.com/w/c/language/as_if)规则下）（例如 [gcc 漏洞 8537](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=8537)）。为此，此函数不能用于擦洗内存（例如以零填充存储密码的数组）。

​	对 `memset_explicit` 和 `memset_s` 禁止此优化：保证进行内存写。

​	该问题的第三方解决方案包含 FreeBSD [explicit_bzero](https://www.freebsd.org/cgi/man.cgi?query=explicit_bzero) 或 Microsoft [SecureZeroMemory](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366877.aspx)。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
 
int main(void)
{
    char str[] = "ghghghghghghghghghghgh";
    puts(str);
    memset(str,'a',5);
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = memset_s(str, sizeof str, 'b', 5);
    printf("str = \"%s\", r = %d\n", str, r);
    r = memset_s(str, 5, 'c', 10);   // count 大于 destsz  
    printf("str = \"%s\", r = %d\n", str, r);
#endif
}
```

​	可能的输出：

```txt
ghghghghghghghghghghgh
aaaaahghghghghghghghgh
str = "bbbbbhghghghghghghghgh", r = 0
str = "ccccchghghghghghghghgh", r = 22
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.6.1 The memset function （第 270 页）

  - K.3.7.4.1 The memset_s function （第 451 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.1 The memset function （第 371 页）

  - K.3.7.4.1 The memset_s function （第 621-622 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.1 The memset function （第 333 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.1 The memset function

**参阅**

| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                     |
| ------------------------------------------------------------ | --------------------------------------------- |
| [wmemset (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemset) | 复制给定的宽字符到宽字符数组的所有位置 (函数) |
| **memset** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memset)** |                                               |





### memset_s

原址：[https://zh.cppreference.com/w/c/string/byte/memset](https://zh.cppreference.com/w/c/string/byte/memset)

作用：以字符填充缓冲区  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
void *memset( void *dest, int ch, size_t count );// (1)
void *memset_explicit( void *dest, int ch, size_t count );// (2)(C23 起)
errno_t memset_s( void *dest, rsize_t destsz, int ch, rsize_t count );// (3)(C11 起)
```

1） 将值 `(unsigned char)ch` 复制到 `dest` 所指向对象的最前面 `count` 个字节中。

 若在 dest 数组结尾之后发生访问则行为未定义。若 `dest` 为空指针则行为未定义。

2） 同 (1)，但对敏感信息是安全的。

3） 同 (1)，但若 `dest` 与 `destsz` 自身有效，则存储 `ch` 于目标范围 `[dest, dest+destsz)` 的每个位置后，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `dest` 是空指针
  - `destsz` 或 `count` 大于 RSIZE_MAX
  - `count` 大于 `destsz`（会发生缓冲区溢出）

 若 `dest` 所指向的字符数组大小 < `count` <= `destsz`; 则行为未定义，换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要填充的对象的指针 |
| ------ | ---- | ---------------------- |
| ch     | -    | 填充字节               |
| count  | -    | 要填充的字节数         |
| destsz | -    | 目标数组的大小         |

**返回值**

1,2) `dest` 的副本，本质为更底层操作的临时内存地址，在实际操作中不建议直接使用此地址，操作完成以后，真正有意义的地址是dest本身。

3） 成功时为零，失败时为非零。在失败时，若 `dest` 不是空指针且 `destsz` 合法，则亦写入 `destsz` 个填充字节 `ch` 到目标数组。

**注解**

​	若 `memset` 所修改的对象在其生存期的剩余部分不再被访问，则此函数可以被优化掉（在[如同](https://zh.cppreference.com/w/c/language/as_if)规则下）（例如 [gcc 漏洞 8537](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=8537)）。为此，此函数不能用于擦洗内存（例如以零填充存储密码的数组）。

​	对 `memset_explicit` 和 `memset_s` 禁止此优化：保证进行内存写。

​	该问题的第三方解决方案包含 FreeBSD [explicit_bzero](https://www.freebsd.org/cgi/man.cgi?query=explicit_bzero) 或 Microsoft [SecureZeroMemory](https://msdn.microsoft.com/en-us/library/windows/desktop/aa366877.aspx)。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
 
int main(void)
{
    char str[] = "ghghghghghghghghghghgh";
    puts(str);
    memset(str,'a',5);
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = memset_s(str, sizeof str, 'b', 5);
    printf("str = \"%s\", r = %d\n", str, r);
    r = memset_s(str, 5, 'c', 10);   // count 大于 destsz  
    printf("str = \"%s\", r = %d\n", str, r);
#endif
}
```

​	可能的输出：

```txt
ghghghghghghghghghghgh
aaaaahghghghghghghghgh
str = "bbbbbhghghghghghghghgh", r = 0
str = "ccccchghghghghghghghgh", r = 22
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.6.1 The memset function （第 270 页）

  - K.3.7.4.1 The memset_s function （第 451 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.1 The memset function （第 371 页）

  - K.3.7.4.1 The memset_s function （第 621-622 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.1 The memset function （第 333 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.1 The memset function

**参阅**

| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                     |
| ------------------------------------------------------------ | --------------------------------------------- |
| [wmemset (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemset) | 复制给定的宽字符到宽字符数组的所有位置 (函数) |
| **memset** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/memset)** |                                               |
`__STDC_WANT_LIB_EXT1__`：






### strcat

原址：[https://zh.cppreference.com/w/c/string/byte/strcat](https://zh.cppreference.com/w/c/string/byte/strcat)

作用：连接两个字符串  (函数)

备注：
```c
// 在标头 <string.h> 定义
// (1)
char *strcat( char *dest, const char *src );// (C99 前)
char *strcat( char *restrict dest, const char *restrict src );// (C99 起)
errno_t strcat_s(char *restrict dest, rsize_t destsz, const char *restrict src);// (2)(C11 起)
```

1） 将 `src` 所指向的空终止字节字符串的副本追加到 `dest` 所指向的空终止字节字符串的末尾。字符 `src[0]` 替换 `dest` 末尾的空终止符。产生的字节字符串是空终止的。

 若目标数组对于 `src` 和 `dest` 的内容以及空终止符不够大，则行为未定义。若字符串重叠，则行为未定义。若 `dest` 或 `src` 不是指向空终止字节字符串的指针，则行为未定义。

2） 同 (1)，但它可用未指定值破坏目标数组的剩余部分（从最后写入字符到 `destsz`），以及在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `src` 或 `dest` 为空指针
  - `destsz` 为零或大于 RSIZE_MAX
  - `dest` 的前 `destsz` 个字节中无空终止符
  - 会出现截断（`dest` 末尾的可用空间不能适应 `src` 的每个字符，包括空终止符）
  - 源与目标字符串间会出现重叠

 若 `dest` 所指向的字符数组大小 < `[strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(dest)+[strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(src)+1` <= `destsz` 则行为未定义；换言之，`destsz` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要后附到的空终止字节字符串的指针         |
| ------ | ---- | -------------------------------------------- |
| src    | -    | 指向作为复制来源的空终止字节字符串的指针     |
| destsz | -    | 要写入的最大字符数，典型地为目标缓冲区的大小 |

**返回值**

1） 返回 `dest` 的副本。

2） 成功时返回零。错误时返回非零。错误时，亦写入零到 `dest[0]`（除非 `dest` 为空指针，或 `destsz` 为零或大于 RSIZE_MAX）。

**注解**

​	因为 `strcat` 需要在每次调用时找到 `dest` 的结尾，故用 `strcat` 将多个字符串连接成一体是低效的。

​	为提升效率，允许 `strcat_s` 从最后被写入字符到 `destsz` 破坏目标数组：它可以用多字节块复制，然后检查空字节。

​	函数 `strcat_s` 类似 BSD 函数 `strlcat`，

- `strlcat` 截断源字符串以适合目标
- `strlcat` 不进行所有 `strcat_s` 进行的运行时检查
- 若调用失败，则 `strlcat` 不设置目标为空字符串或调用处理函数，而令失败显著。

​	尽管 `strcat_s` 由于潜在安全风险禁止截断，还可以用带边界检查的 [strncat_s](https://zh.cppreference.com/w/c/string/byte/strncat) 截断字符串。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h> 
#include <stdio.h>
#include <stdlib.h>
 
int main(void) 
{
    char str[50] = "Hello ";
    char str2[50] = "World!";
    strcat(str, str2);
    strcat(str, " ...");
    strcat(str, " Goodbye World!");
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = strcat_s(str, sizeof str, " ... ");
    printf("str = \"%s\", r = %d\n", str, r);
    r = strcat_s(str, sizeof str, " and this is too much");
    printf("str = \"%s\", r = %d\n", str, r);
#endif
}
```

​	可能的输出：

```txt
Hello World! ... Goodbye World!
str = "Hello World! ... Goodbye World! ... ", r = 0
str = "", r = 22
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.3.1 The strcat function （第 364 页）

  - K.3.7.2.1 The strcat_s function （第 617-618 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.3.1 The strcat function （第 327 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.3.1 The strcat function

**参阅**

| [strncat <br />strncat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncat) | 连接两个字符串的一定数量字符 (函数)             |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                       |
| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |
| **strcat** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcat)** |                                                 |





### strcat_s

原址：[https://zh.cppreference.com/w/c/string/byte/strcat](https://zh.cppreference.com/w/c/string/byte/strcat)

作用：连接两个字符串  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
// (1)
char *strcat( char *dest, const char *src );// (C99 前)
char *strcat( char *restrict dest, const char *restrict src );// (C99 起)
errno_t strcat_s(char *restrict dest, rsize_t destsz, const char *restrict src);// (2)(C11 起)
```

1） 将 `src` 所指向的空终止字节字符串的副本追加到 `dest` 所指向的空终止字节字符串的末尾。字符 `src[0]` 替换 `dest` 末尾的空终止符。产生的字节字符串是空终止的。

 若目标数组对于 `src` 和 `dest` 的内容以及空终止符不够大，则行为未定义。若字符串重叠，则行为未定义。若 `dest` 或 `src` 不是指向空终止字节字符串的指针，则行为未定义。

2） 同 (1)，但它可用未指定值破坏目标数组的剩余部分（从最后写入字符到 `destsz`），以及在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `src` 或 `dest` 为空指针
  - `destsz` 为零或大于 RSIZE_MAX
  - `dest` 的前 `destsz` 个字节中无空终止符
  - 会出现截断（`dest` 末尾的可用空间不能适应 `src` 的每个字符，包括空终止符）
  - 源与目标字符串间会出现重叠

 若 `dest` 所指向的字符数组大小 < `[strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(dest)+[strlen](http://zh.cppreference.com/w/c/string/byte/strlen)(src)+1` <= `destsz` 则行为未定义；换言之，`destsz` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要后附到的空终止字节字符串的指针         |
| ------ | ---- | -------------------------------------------- |
| src    | -    | 指向作为复制来源的空终止字节字符串的指针     |
| destsz | -    | 要写入的最大字符数，典型地为目标缓冲区的大小 |

**返回值**

1） 返回 `dest` 的副本。

2） 成功时返回零。错误时返回非零。错误时，亦写入零到 `dest[0]`（除非 `dest` 为空指针，或 `destsz` 为零或大于 RSIZE_MAX）。

**注解**

​	因为 `strcat` 需要在每次调用时找到 `dest` 的结尾，故用 `strcat` 将多个字符串连接成一体是低效的。

​	为提升效率，允许 `strcat_s` 从最后被写入字符到 `destsz` 破坏目标数组：它可以用多字节块复制，然后检查空字节。

​	函数 `strcat_s` 类似 BSD 函数 `strlcat`，

- `strlcat` 截断源字符串以适合目标
- `strlcat` 不进行所有 `strcat_s` 进行的运行时检查
- 若调用失败，则 `strlcat` 不设置目标为空字符串或调用处理函数，而令失败显著。

​	尽管 `strcat_s` 由于潜在安全风险禁止截断，还可以用带边界检查的 [strncat_s](https://zh.cppreference.com/w/c/string/byte/strncat) 截断字符串。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h> 
#include <stdio.h>
#include <stdlib.h>
 
int main(void) 
{
    char str[50] = "Hello ";
    char str2[50] = "World!";
    strcat(str, str2);
    strcat(str, " ...");
    strcat(str, " Goodbye World!");
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = strcat_s(str, sizeof str, " ... ");
    printf("str = \"%s\", r = %d\n", str, r);
    r = strcat_s(str, sizeof str, " and this is too much");
    printf("str = \"%s\", r = %d\n", str, r);
#endif
}
```

​	可能的输出：

```txt
Hello World! ... Goodbye World!
str = "Hello World! ... Goodbye World! ... ", r = 0
str = "", r = 22
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.3.1 The strcat function （第 364 页）

  - K.3.7.2.1 The strcat_s function （第 617-618 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.3.1 The strcat function （第 327 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.3.1 The strcat function

**参阅**

| [strncat <br />strncat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncat) | 连接两个字符串的一定数量字符 (函数)             |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                       |
| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |
| **strcat** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcat)** |                                                 |
`__STDC_WANT_LIB_EXT1__`：






### strchr

原址：[https://zh.cppreference.com/w/c/string/byte/strchr](https://zh.cppreference.com/w/c/string/byte/strchr)

作用：查找字符的首次出现  (函数)

备注：
```c
// 在标头 <string.h> 定义
char* strchr( const char* str, int ch );// (1)
/*QChar*/ *strchr( /*QChar*/ *str, int ch );// (2)(C23 起)
```

1） 寻找 `ch`（如同用 `(char)ch` 转换成 `char` 后）在 `str` 所指向的空终止字节字符串（转译每个字符为 `unsigned char`）中的首次出现位置。终止空字符被认为是字符串的一部分，并且能在寻找 `'\0'` 时找到。

2） 等价于 (1) 的泛型函数。令 `T` 为未限定的 字符对象类型。

  - 若 `str` 类型为 `const T*`，则返回类型为 `const char*`。
  - 否则，若 `str` 类型为 `T*`，返回类型为 `char*`。
  - 否则，行为未定义。

如果这些泛型函数中的某个宏定义被抑制无法访问实际函数（比如当使用了 `(strchr)` 或使用了函数指针时），则实际函数声明 (1) 即变得可见。

​	若 `str` 不是指向空终止字节字符串的指针，则行为未定义。

**参数**

| str  | -    | 指向待分析的空终止字节字符串的指针 |
| ---- | ---- | ---------------------------------- |
| ch   | -    | 要搜索的字符                       |

**返回值**

​	指向 `str` 找到的字符的指针，若未找到该字符则为空指针。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char *str = "Try not. Do, or do not. There is no try.";
    char target = 'T';
    const char *result = str;
 
    while ((result = strchr(result, target)) != NULL)
    {
        printf("找到 '%c' 起始于 '%s'\n", target, result);
        ++result; // result 自增，否则我们会找到相同位置的目标
    }
}
```

​	输出：

```txt
找到 'T' 起始于 'Try not. Do, or do not. There is no try.'
找到 'T' 起始于 'There is no try.'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.2 The strchr function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.2 The strchr function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.2 The strchr function （第 367-368 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.2 The strchr function （第 330 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.2 The strchr function

**参阅**

| [memchr<br />](https://zh.cppreference.com/w/c/string/byte/memchr) | 在数组中搜索字符的首次出现 (函数)                       |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| [strrchr<br />](https://zh.cppreference.com/w/c/string/byte/strrchr) | 查找字符的最后一次出现 (函数)                           |
| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数) |
| **strchr** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strchr)** |                                                         |





### strcmp

原址：[https://zh.cppreference.com/w/c/string/byte/strcmp](https://zh.cppreference.com/w/c/string/byte/strcmp)

作用：比较两个字符串  (函数)

备注：
```c
// 在标头 <string.h> 定义
int strcmp( const char* lhs, const char* rhs );
```

​	以字典序比较两个空终止字节字符串。

​	结果的符号是被比较的字符串中首对不同字符（都转译成 `unsigned char`）的值间的差的符号。

​	若 `lhs` 或 `rhs` 不是指向空终止字节字符串的指针，则行为未定义。

**参数**

| lhs, rhs | -    | 指向要比较的空终止字节字符串的指针 |
| -------- | ---- | ---------------------------------- |
|          |      |                                    |

**返回值**

​	若字典序中 `lhs` 先于 `rhs` 出现则为负值。

​	若 `lhs` 与 `rhs` 比较相等则为零。

​	若字典序中 `lhs` 后于 `rhs` 出现则为正值。

**注解**

​	不同于 [strcoll](https://zh.cppreference.com/w/c/string/byte/strcoll) 和 [strxfrm](https://zh.cppreference.com/w/c/string/byte/strxfrm)，此函数不考虑本地环境。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
void demo(const char* lhs, const char* rhs)
{
    const int rc = strcmp(lhs, rhs);
    const char* rel = rc < 0 ? "先于" : rc > 0 ? "后于" : "等于";
    printf("[%s] %s [%s]\n", lhs, rel, rhs);
}
 
int main(void)
{
    const char* string = "Hello World!";
    demo(string, "Hello!");
    demo(string, "Hello");
    demo(string, "Hello there");
    demo("Hello, everybody!" + 12, "Hello, somebody!" + 11);
}
```

​	输出：

```txt
[Hello World!] 先于 [Hello!]
[Hello World!] 后于 [Hello]
[Hello World!] 先于 [Hello there]
[body!] 等于 [body!]
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.4.2 The strcmp function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.4.2 The strcmp function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.4.2 The strcmp function （第 365-366 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.4.2 The strcmp function （第 328-329 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.4.2 The strcmp function

**参阅**

| [strncmp<br />](https://zh.cppreference.com/w/c/string/byte/strncmp) | 比较两个字符串的一定数量字符 (函数)     |
| ------------------------------------------------------------ | --------------------------------------- |
| [wcscmp (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscmp) | 比较两个宽字符串 (函数)                 |
| [memcmp<br />](https://zh.cppreference.com/w/c/string/byte/memcmp) | 比较两块缓冲区 (函数)                   |
| [strcoll<br />](https://zh.cppreference.com/w/c/string/byte/strcoll) | 比较两个字符串，根据当前本地环境 (函数) |
| **strcmp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcmp)** |                                         |





### strcoll

原址：[https://zh.cppreference.com/w/c/string/byte/strcoll](https://zh.cppreference.com/w/c/string/byte/strcoll)

作用：比较两个字符串，根据当前本地环境  (函数)

备注：
```c
// 在标头 <string.h> 定义
int strcoll( const char *lhs, const char *rhs );
```

​	按照 [LC_COLLATE](https://zh.cppreference.com/w/c/locale/LC_categories) 类别所定义的当前本地环境，比较两个空终止字节字符串。

**参数**

| lhs, rhs | -    | 指向要比较的空终止字节字符串的指针 |
| -------- | ---- | ---------------------------------- |
|          |      |                                    |

**返回值**

- 若 `lhs` *小于*（前趋）`rhs` 则为负值。
- 若 `lhs` *等于* `rhs` 则为 `0`。
- 若 `lhs` *大于*（后随）`rhs` 则为负值。

**注意**

​	校排顺序为字典顺序：国家字母表（其*等价类*）中字母的位置拥有高于其大小写或变体的优先级。在等价类内，小写字符先于其大写等价物校排，而且对有变音符的字符可能应用特定于本地环境的顺序。一些本地环境中，字符组作为单个*校排单元*参与比较。例如，`"ch"` 在捷克语中后随 `"h"` 而前趋 `"i"`，`"dzs"` 在匈牙利语中后随 `"dz"` 而前趋 `"g"`。

**示例**

```c
#include <stdio.h>
#include <string.h>
#include <locale.h>
 
int main(void)
{
    setlocale(LC_COLLATE, "cs_CZ.utf8");
    // 此外，某些 OS 上 ISO-8859-2（亦即 Latin-2）
    // 也能工作：
    // setlocale(LC_COLLATE, "cs_CZ.iso88592");
 
 
    const char* s1 = "hrnec";
    const char* s2 = "chrt";
 
    printf("In the Czech locale: ");
    if(strcoll(s1, s2) < 0)
         printf("%s before %s\n", s1, s2);
    else
         printf("%s before %s\n", s2, s1);
 
    printf("In lexicographical comparison: ");
    if(strcmp(s1, s2) < 0)
         printf("%s before %s\n", s1, s2);
    else
         printf("%s before %s\n", s2, s1);
}
```

​	输出：

```txt
In the Czech locale: hrnec before chrt
In lexicographical comparison: chrt before hrnec
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.4.3 The strcoll function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.4.3 The strcoll function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.4.3 The strcoll function （第 366 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.4.3 The strcoll function （第 329 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.4.3 The strcoll function

**参阅**

| [wcscoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscoll) | 根据当前本地环境比较两个宽字符串 (函数)                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [strxfrm<br />](https://zh.cppreference.com/w/c/string/byte/strxfrm) | 变换字符串，使得 strcmp 会产生同 strcoll 的结果 (函数)       |
| [wcsxfrm (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsxfrm) | 变换宽字符串，使得 [wcscmp](https://zh.cppreference.com/w/c/string/wide/wcscmp) 会产生与 [wcscoll](https://zh.cppreference.com/w/c/string/wide/wcscoll) 相同的结果 (函数) |
| [strcmp<br />](https://zh.cppreference.com/w/c/string/byte/strcmp) | 比较两个字符串 (函数)                                        |
| **strcoll** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcoll)** |                                                              |





### strcpy

原址：[https://zh.cppreference.com/w/c/string/byte/strcpy](https://zh.cppreference.com/w/c/string/byte/strcpy)

作用：复制字符串给另一个  (函数)

备注：
```c
// 在标头 <string.h> 定义
// (1)
char* strcpy( char* dest, const char* src );// (C99 前)
char* strcpy( char* restrict dest, const char* restrict src );// (C99 起)
errno_t strcpy_s( char* restrict dest, rsize_t destsz, const char* restrict src );// (2)(C11 起)
```

1） 复制 `src` 所指向的空终止字节字符串，包含空终止符，到首元素为 `dest` 所指的字符数组。

 若 `dest` 数组长度不足则行为未定义。若字符串重叠则行为未定义。若 `dest` 不是指向字符数组的指针或 `src` 不是指向空终止字节字符串的指针则行为未定义。

2） 同 (1)，但它可能以未指定值破坏目标数组的剩余部分，而且会会在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `src` 或 `dest` 为空指针
  - `destsz` 为零或大于 `RSIZE_MAX`
  - `destsz` 小于或等于 `strnlen_s(src, destsz)`；换言之，会发生截断
  - 源与目标字符串间会发生重叠

 若 `dest` 所指的字符数组大小 `<=` `strnlen_s(src, destsz)` `<` `destsz` 则行为未定义；换言之， `destsz` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要写入的字符数组的指针                 |
| ------ | ---- | ------------------------------------------ |
| src    | -    | 指向要复制的空终止字节字符串的指针         |
| destsz | -    | 写入的最大字符数，典型地为目标缓冲区的大小 |

**返回值**

1） 返回 `dest` 的副本

2） 成功时返回零，失败时返回非零。而且失败时向 `dest[0]` 写入零（除非 `dest` 是空指针或 `destsz` 为零或大于 `RSIZE_MAX`）。

**注解**

​	为提升效率，允许 `strcpy_s` 破坏至多 `destsz` 个目标数组上次写入的字符：它可能先复制多字节块再检查空字节。

​	函数 `strcpy_s` 类似 BSD 函数 `strlcpy`，但

- `strlcpy` 截断源字符串以适应目标（这有安全风险）
- `strlcpy` 不全部进行 `strcpy_s` 所进行的运行时检查
- `strlcpy` 不会通过设置目标为空字符串或调用处理函数，以令失败显著。

​	尽管 `strcpy_s` 因潜在的安全风险禁止截断，也还可以代之以用使用边界检查的 [strncpy_s](https://zh.cppreference.com/w/c/string/byte/strncpy) 并进行截断字符串。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
int main(void)
{
    char* src = "Take the test.";
//  src[0] = 'M' ; // 这会是未定义行为
    char dst[strlen(src) + 1]; // +1 以适应空终止符
    strcpy(dst, src);
    dst[0] = 'M'; // OK
    printf("src = %s\ndst = %s\n", src, dst);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, src);
    printf("dst = \"%s\", r = %d\n", dst, r);
    r = strcpy_s(dst, sizeof dst, "Take even more tests.");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

​	可能的输出：

```txt
src = Take the test.
dst = Make the test.
dst = "Take the test.", r = 0
dst = "", r = 22
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.2.3 The strcpy function （第 TBD 页）

  - K.3.7.1.3 The strcpy_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.3 The strcpy function （第 264-265 页）

  - K.3.7.1.3 The strcpy_s function （第 447 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.3 The strcpy function （第 363 页）

  - K.3.7.1.3 The strcpy_s function （第 615-616 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.3 The strcpy function （第 326 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.3 The strcpy function

**参阅**

| [strncpy <br />strncpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncpy) | 从字符串复制一定数量的字符到另一个 (函数) |
| ------------------------------------------------------------ | ----------------------------------------- |
| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                 |
| [wcscpy (C95)<br />wcscpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscpy) | 复制宽字符串给另一个 (函数)               |
| [strdup (动态内存 TR)<br />](https://zh.cppreference.com/w/c/experimental/dynamic/strdup) | 分配字符串的副本 (函数)                   |
| **strcpy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcpy)** |                                           |





### strcpy_s

原址：[https://zh.cppreference.com/w/c/string/byte/strcpy](https://zh.cppreference.com/w/c/string/byte/strcpy)

作用：复制字符串给另一个  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
// (1)
char* strcpy( char* dest, const char* src );// (C99 前)
char* strcpy( char* restrict dest, const char* restrict src );// (C99 起)
errno_t strcpy_s( char* restrict dest, rsize_t destsz, const char* restrict src );// (2)(C11 起)
```

1） 复制 `src` 所指向的空终止字节字符串，包含空终止符，到首元素为 `dest` 所指的字符数组。

 若 `dest` 数组长度不足则行为未定义。若字符串重叠则行为未定义。若 `dest` 不是指向字符数组的指针或 `src` 不是指向空终止字节字符串的指针则行为未定义。

2） 同 (1)，但它可能以未指定值破坏目标数组的剩余部分，而且会会在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `src` 或 `dest` 为空指针
  - `destsz` 为零或大于 `RSIZE_MAX`
  - `destsz` 小于或等于 `strnlen_s(src, destsz)`；换言之，会发生截断
  - 源与目标字符串间会发生重叠

 若 `dest` 所指的字符数组大小 `<=` `strnlen_s(src, destsz)` `<` `destsz` 则行为未定义；换言之， `destsz` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要写入的字符数组的指针                 |
| ------ | ---- | ------------------------------------------ |
| src    | -    | 指向要复制的空终止字节字符串的指针         |
| destsz | -    | 写入的最大字符数，典型地为目标缓冲区的大小 |

**返回值**

1） 返回 `dest` 的副本

2） 成功时返回零，失败时返回非零。而且失败时向 `dest[0]` 写入零（除非 `dest` 是空指针或 `destsz` 为零或大于 `RSIZE_MAX`）。

**注解**

​	为提升效率，允许 `strcpy_s` 破坏至多 `destsz` 个目标数组上次写入的字符：它可能先复制多字节块再检查空字节。

​	函数 `strcpy_s` 类似 BSD 函数 `strlcpy`，但

- `strlcpy` 截断源字符串以适应目标（这有安全风险）
- `strlcpy` 不全部进行 `strcpy_s` 所进行的运行时检查
- `strlcpy` 不会通过设置目标为空字符串或调用处理函数，以令失败显著。

​	尽管 `strcpy_s` 因潜在的安全风险禁止截断，也还可以代之以用使用边界检查的 [strncpy_s](https://zh.cppreference.com/w/c/string/byte/strncpy) 并进行截断字符串。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
 
int main(void)
{
    char* src = "Take the test.";
//  src[0] = 'M' ; // 这会是未定义行为
    char dst[strlen(src) + 1]; // +1 以适应空终止符
    strcpy(dst, src);
    dst[0] = 'M'; // OK
    printf("src = %s\ndst = %s\n", src, dst);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    int r = strcpy_s(dst, sizeof dst, src);
    printf("dst = \"%s\", r = %d\n", dst, r);
    r = strcpy_s(dst, sizeof dst, "Take even more tests.");
    printf("dst = \"%s\", r = %d\n", dst, r);
#endif
}
```

​	可能的输出：

```txt
src = Take the test.
dst = Make the test.
dst = "Take the test.", r = 0
dst = "", r = 22
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.2.3 The strcpy function （第 TBD 页）

  - K.3.7.1.3 The strcpy_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.3 The strcpy function （第 264-265 页）

  - K.3.7.1.3 The strcpy_s function （第 447 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.3 The strcpy function （第 363 页）

  - K.3.7.1.3 The strcpy_s function （第 615-616 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.3 The strcpy function （第 326 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.3 The strcpy function

**参阅**

| [strncpy <br />strncpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncpy) | 从字符串复制一定数量的字符到另一个 (函数) |
| ------------------------------------------------------------ | ----------------------------------------- |
| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                 |
| [wcscpy (C95)<br />wcscpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscpy) | 复制宽字符串给另一个 (函数)               |
| [strdup (动态内存 TR)<br />](https://zh.cppreference.com/w/c/experimental/dynamic/strdup) | 分配字符串的副本 (函数)                   |
| **strcpy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcpy)** |                                           |
`__STDC_WANT_LIB_EXT1__`：






### strcspn

原址：[https://zh.cppreference.com/w/c/string/byte/strcspn](https://zh.cppreference.com/w/c/string/byte/strcspn)

作用：返回另一个字符串所不具有的字符分割的最大起始段长度   (函数)

备注：
```c
// 在标头 <string.h> 定义
size_t strcspn( const char *dest, const char *src );
```

​	返回 `dest` 所指向的空终止字节字符串的最大起始段长度，该段只由 `src` 所指向的空终止字节字符串中找*不*到的字符组成。

​	若 `dest` 或 `src` 不是指向空终止字节字符串的指针，则行为未定义。

**参数**

| dest | -    | 指向要分析的空终止字节字符串的指针         |
| ---- | ---- | ------------------------------------------ |
| src  | -    | 指向含有要搜索字符的空终止字节字符串的指针 |

**返回值**

​	仅由 `src` 所指向的空终止字节字符串中找不到的字符组成的最大起始段长度。

**注意**

​	函数名代表“补集段 (complementary span)”，因为函数搜索 `src` 中找不到的字符，即 `src` 的补集。

**示例**

```c
#include <string.h>
#include <stdio.h>
 
int main(void)
{
    const char *string = "abcde312$#@";
    const char *invalid = "*$#";
 
    size_t valid_len = strcspn(string, invalid);
    if(valid_len != strlen(string))
       printf("'%s' contains invalid chars starting at position %zu\n",
               string, valid_len);
}
```

​	输出：

```txt
'abcde312$#@' contains invalid chars starting at position 8
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.3 The strcspn function （第 368 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.3 The strcspn function （第 331 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.3 The strcspn function

**参阅**

| [strspn<br />](https://zh.cppreference.com/w/c/string/byte/strspn) | 返回由另一个字符串中的字符分割的最大起始段长度 (函数)        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcscspn (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscspn) | 返回仅由*不* ﻿出现于另一个宽字符串中的宽字符分隔的最长首段长度 (函数) |
| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数)      |
| **strcspn** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strcspn)** |                                                              |





### strdup

原址：[https://zh.cppreference.com/w/c/string/byte/strdup](https://zh.cppreference.com/w/c/string/byte/strdup)

作用：分配字符串的副本   (函数)

备注：
```c
// 在标头 <string.h> 定义
char *strdup( const char *src );// (C23 起)
```

​	返回指向作为 `src` 所指向的字符串的副本的空终止字节字符串的指针。如同通过调用 [malloc](https://zh.cppreference.com/w/c/memory/malloc) 获得新字符串的空间。必须将返回的指针传递给 [free](https://zh.cppreference.com/w/c/memory/free) 以避免内存泄漏。

​	若出现错误，则返回空指针值并可能设置 [errno](https://zh.cppreference.com/w/c/error/errno)。

**参数**

| src  | -    | 指向要复制的空终止字节字符串的指针 |
| ---- | ---- | ---------------------------------- |
|      |      |                                    |

**返回值**

​	指向新分配的字符串的指针，或若出现错误则为空指针值。

**注解**

​	该函数等同于 [POSIX strdup](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strdup.html) 。

**示例**

```c
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const char *s1 = "Duplicate me!";
    char *s2 = strdup(s1);
    printf("s2 = \"%s\"\n", s2);
    free(s2);
}
```

​	输出：

```txt
s2 = "Duplicate me!"
```

**参阅**

| [strndup (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strndup) | 分配拥有指定大小的字符串副本 (函数) |
| ------------------------------------------------------------ | ----------------------------------- |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)           |
| [malloc<br />](https://zh.cppreference.com/w/c/memory/malloc) | 分配内存 (函数)                     |
| [free<br />](https://zh.cppreference.com/w/c/memory/free)  | 归还之前分配的内存 (函数)           |





### strerror

原址：[https://zh.cppreference.com/w/c/string/byte/strerror](https://zh.cppreference.com/w/c/string/byte/strerror)

作用：返回给定错误码的文本版本  (函数)

备注：
```c
// 在标头 <string.h> 定义
char* strerror( int errnum );// (1)
errno_t strerror_s( char *buf, rsize_t bufsz, errno_t errnum );// (2)(C11 起)
size_t strerrorlen_s( errno_t errnum );// (3)(C11 起)
```

1） 返回指向系统错误码 `errnum` 的文本表示的指针，它等同于 [perror()](https://zh.cppreference.com/w/c/io/perror) 会打印的描述。

 `errnum` 通常从 `errno` 变量获得，不过函数接受可任何 `int` 类型值。字符串的内容特定于本地环境。

 程序必须不修改返回的字符串，但对 `strerror` 函数的后继调用可能重写该字符串。不要求 `strerror` 为线程安全。实现可以返回指向静态只读字符串字面量的不同指针，或反复返回指向静态缓冲区的同一指针，`strerror` 放置字符串于该缓冲区中。

2） 同 (1)，但将消息复制到用户提供的存储 `buf` 中。不写入多于 `bufsz-1` 个字符，缓冲区始终为空终止的。若消息必须被截断，且 `bufsz` 大于 3，则只写入 `bufsz-4` 个字符，并在空终止符前前附字符 `"..."` 。另外，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `buf` 为空指针
  - `bufsz` 为零或大于 RSIZE_MAX

 若向 `buf` 的写入在数组末尾后发生则行为未定义，这在 `buf` 所指向的缓冲区大小写小于错误消息的字符数，且小于 `bufsz` 时会发生。

3） 计算当以 `errnum` 调用 `strerror_s` 则本会写入的，本地环境限定错误消息的不截断长度。长度不包含空终止符。

**参数**

| errnum | -    | 指代错误码的整数值         |
| ------ | ---- | -------------------------- |
| buf    | -    | 指向用户提供的缓冲区的指针 |
| bufsz  | -    | 用户提供的缓冲区的大小     |

**返回值**

1） 指向对应 [errno](https://zh.cppreference.com/w/c/error/errno) 错误码 `errnum` 的空终止字节串的指针。

2） 若整个消息完整存储于 `buf` 则为零，否则为非零。

3） `strerror_s` 会返回的消息长度（不包含空终止符）

**注意**

​	[POSIX](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strerror.html) 允许对 `strerror` 的后继调用非法化先前调用所返回的指针值。它亦指定控制这些消息的 [`<C_MESSAGE>`](https://zh.cppreference.com/w/c/locale/LC_categories) 本地环境平面。

​	`strerror_s` 是仅有的允许截断的带边界检查函数，因为提供尽可能多的关于失败的信息被视为更加令人满意。POSIX 亦为类似目的定义 [strerror_r](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strerror.html)。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <errno.h>
#include <string.h>
#include <locale.h>
 
int main(void)
{
    FILE *fp = fopen(tmpnam((char[L_tmpnam]){0}), "r");
    if(fp==NULL) {
        printf("File opening error: %s\n", strerror(errno));
        setlocale(LC_MESSAGES, "de_DE.utf8");
        printf("Now in German: %s\n", strerror(errno));
#ifdef __STDC_LIB_EXT1__
        setlocale(LC_ALL, "zh_CN.utf8"); // printf 需要多字节输出的 CTYPE
        size_t errmsglen = strerrorlen_s(errno) + 1;
        char errmsg[errmsglen]; 
        strerror_s(errmsg, errmsglen, errno);
        printf("Now in Chinese: %s\n", errmsg);
#endif
    }
}
```

​	可能的输出：

```txt
File opening error: No such file or directory
Now in German: Datei oder Verzeichnis nicht gefunden
Now in Chinese: 文件或目录不存在
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.2 The strerror function （第 371 页）

  - K.3.7.4.2 The strerror_s function （第 622 页）

  - K.3.7.4.3 The strerrorlen_s function （第 623 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.2 The strerror function （第 334 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.2 The strerror function

**参阅**

| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 [stderr](https://zh.cppreference.com/w/c/io) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [errno<br />](https://zh.cppreference.com/w/c/error/errno) | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量)             |
| **strerror** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strerror)** |                                                              |





### strerror_s

原址：[https://zh.cppreference.com/w/c/string/byte/strerror](https://zh.cppreference.com/w/c/string/byte/strerror)

作用：返回给定错误码的文本版本  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
char* strerror( int errnum );// (1)
errno_t strerror_s( char *buf, rsize_t bufsz, errno_t errnum );// (2)(C11 起)
size_t strerrorlen_s( errno_t errnum );// (3)(C11 起)
```

1） 返回指向系统错误码 `errnum` 的文本表示的指针，它等同于 [perror()](https://zh.cppreference.com/w/c/io/perror) 会打印的描述。

 `errnum` 通常从 `errno` 变量获得，不过函数接受可任何 `int` 类型值。字符串的内容特定于本地环境。

 程序必须不修改返回的字符串，但对 `strerror` 函数的后继调用可能重写该字符串。不要求 `strerror` 为线程安全。实现可以返回指向静态只读字符串字面量的不同指针，或反复返回指向静态缓冲区的同一指针，`strerror` 放置字符串于该缓冲区中。

2） 同 (1)，但将消息复制到用户提供的存储 `buf` 中。不写入多于 `bufsz-1` 个字符，缓冲区始终为空终止的。若消息必须被截断，且 `bufsz` 大于 3，则只写入 `bufsz-4` 个字符，并在空终止符前前附字符 `"..."` 。另外，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `buf` 为空指针
  - `bufsz` 为零或大于 RSIZE_MAX

 若向 `buf` 的写入在数组末尾后发生则行为未定义，这在 `buf` 所指向的缓冲区大小写小于错误消息的字符数，且小于 `bufsz` 时会发生。

3） 计算当以 `errnum` 调用 `strerror_s` 则本会写入的，本地环境限定错误消息的不截断长度。长度不包含空终止符。

**参数**

| errnum | -    | 指代错误码的整数值         |
| ------ | ---- | -------------------------- |
| buf    | -    | 指向用户提供的缓冲区的指针 |
| bufsz  | -    | 用户提供的缓冲区的大小     |

**返回值**

1） 指向对应 [errno](https://zh.cppreference.com/w/c/error/errno) 错误码 `errnum` 的空终止字节串的指针。

2） 若整个消息完整存储于 `buf` 则为零，否则为非零。

3） `strerror_s` 会返回的消息长度（不包含空终止符）

**注意**

​	[POSIX](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strerror.html) 允许对 `strerror` 的后继调用非法化先前调用所返回的指针值。它亦指定控制这些消息的 [`<C_MESSAGE>`](https://zh.cppreference.com/w/c/locale/LC_categories) 本地环境平面。

​	`strerror_s` 是仅有的允许截断的带边界检查函数，因为提供尽可能多的关于失败的信息被视为更加令人满意。POSIX 亦为类似目的定义 [strerror_r](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strerror.html)。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <errno.h>
#include <string.h>
#include <locale.h>
 
int main(void)
{
    FILE *fp = fopen(tmpnam((char[L_tmpnam]){0}), "r");
    if(fp==NULL) {
        printf("File opening error: %s\n", strerror(errno));
        setlocale(LC_MESSAGES, "de_DE.utf8");
        printf("Now in German: %s\n", strerror(errno));
#ifdef __STDC_LIB_EXT1__
        setlocale(LC_ALL, "zh_CN.utf8"); // printf 需要多字节输出的 CTYPE
        size_t errmsglen = strerrorlen_s(errno) + 1;
        char errmsg[errmsglen]; 
        strerror_s(errmsg, errmsglen, errno);
        printf("Now in Chinese: %s\n", errmsg);
#endif
    }
}
```

​	可能的输出：

```txt
File opening error: No such file or directory
Now in German: Datei oder Verzeichnis nicht gefunden
Now in Chinese: 文件或目录不存在
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.2 The strerror function （第 371 页）

  - K.3.7.4.2 The strerror_s function （第 622 页）

  - K.3.7.4.3 The strerrorlen_s function （第 623 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.2 The strerror function （第 334 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.2 The strerror function

**参阅**

| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 [stderr](https://zh.cppreference.com/w/c/io) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [errno<br />](https://zh.cppreference.com/w/c/error/errno) | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量)             |
| **strerror** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strerror)** |                                                              |
`__STDC_WANT_LIB_EXT1__`：






### strerrorlen_s

原址：[https://zh.cppreference.com/w/c/string/byte/strerror](https://zh.cppreference.com/w/c/string/byte/strerror)

作用：返回给定错误码的文本版本  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
char* strerror( int errnum );// (1)
errno_t strerror_s( char *buf, rsize_t bufsz, errno_t errnum );// (2)(C11 起)
size_t strerrorlen_s( errno_t errnum );// (3)(C11 起)
```

1） 返回指向系统错误码 `errnum` 的文本表示的指针，它等同于 [perror()](https://zh.cppreference.com/w/c/io/perror) 会打印的描述。

 `errnum` 通常从 `errno` 变量获得，不过函数接受可任何 `int` 类型值。字符串的内容特定于本地环境。

 程序必须不修改返回的字符串，但对 `strerror` 函数的后继调用可能重写该字符串。不要求 `strerror` 为线程安全。实现可以返回指向静态只读字符串字面量的不同指针，或反复返回指向静态缓冲区的同一指针，`strerror` 放置字符串于该缓冲区中。

2） 同 (1)，但将消息复制到用户提供的存储 `buf` 中。不写入多于 `bufsz-1` 个字符，缓冲区始终为空终止的。若消息必须被截断，且 `bufsz` 大于 3，则只写入 `bufsz-4` 个字符，并在空终止符前前附字符 `"..."` 。另外，在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `buf` 为空指针
  - `bufsz` 为零或大于 RSIZE_MAX

 若向 `buf` 的写入在数组末尾后发生则行为未定义，这在 `buf` 所指向的缓冲区大小写小于错误消息的字符数，且小于 `bufsz` 时会发生。

3） 计算当以 `errnum` 调用 `strerror_s` 则本会写入的，本地环境限定错误消息的不截断长度。长度不包含空终止符。

**参数**

| errnum | -    | 指代错误码的整数值         |
| ------ | ---- | -------------------------- |
| buf    | -    | 指向用户提供的缓冲区的指针 |
| bufsz  | -    | 用户提供的缓冲区的大小     |

**返回值**

1） 指向对应 [errno](https://zh.cppreference.com/w/c/error/errno) 错误码 `errnum` 的空终止字节串的指针。

2） 若整个消息完整存储于 `buf` 则为零，否则为非零。

3） `strerror_s` 会返回的消息长度（不包含空终止符）

**注意**

​	[POSIX](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strerror.html) 允许对 `strerror` 的后继调用非法化先前调用所返回的指针值。它亦指定控制这些消息的 [`<C_MESSAGE>`](https://zh.cppreference.com/w/c/locale/LC_categories) 本地环境平面。

​	`strerror_s` 是仅有的允许截断的带边界检查函数，因为提供尽可能多的关于失败的信息被视为更加令人满意。POSIX 亦为类似目的定义 [strerror_r](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strerror.html)。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <errno.h>
#include <string.h>
#include <locale.h>
 
int main(void)
{
    FILE *fp = fopen(tmpnam((char[L_tmpnam]){0}), "r");
    if(fp==NULL) {
        printf("File opening error: %s\n", strerror(errno));
        setlocale(LC_MESSAGES, "de_DE.utf8");
        printf("Now in German: %s\n", strerror(errno));
#ifdef __STDC_LIB_EXT1__
        setlocale(LC_ALL, "zh_CN.utf8"); // printf 需要多字节输出的 CTYPE
        size_t errmsglen = strerrorlen_s(errno) + 1;
        char errmsg[errmsglen]; 
        strerror_s(errmsg, errmsglen, errno);
        printf("Now in Chinese: %s\n", errmsg);
#endif
    }
}
```

​	可能的输出：

```txt
File opening error: No such file or directory
Now in German: Datei oder Verzeichnis nicht gefunden
Now in Chinese: 文件或目录不存在
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.2 The strerror function （第 371 页）

  - K.3.7.4.2 The strerror_s function （第 622 页）

  - K.3.7.4.3 The strerrorlen_s function （第 623 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.2 The strerror function （第 334 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.2 The strerror function

**参阅**

| [perror<br />](https://zh.cppreference.com/w/c/io/perror)  | 显示对应当前错误的字符串到 [stderr](https://zh.cppreference.com/w/c/io) (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [errno<br />](https://zh.cppreference.com/w/c/error/errno) | 展开成 POSIX 兼容的线程局域错误编号变量 (宏变量)             |
| **strerror** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strerror)** |                                                              |
`__STDC_WANT_LIB_EXT1__`：






### strlen

原址：[https://zh.cppreference.com/w/c/string/byte/strlen](https://zh.cppreference.com/w/c/string/byte/strlen)

作用：返回给定字符串的长度  (函数)

备注：
```c
// 在标头 <string.h> 定义
size_t strlen( const char* str );// (1)
size_t strnlen_s( const char* str, size_t strsz );// (2)(C11 起)
```

1） 返回给定空终止字符串的长度，即首元素为 `str` 所指的字符数组中，直至且不包含首个空字符的字符数。

 若 `str` 不是指向空终止字节字符串的指针则行为未定义。

2） 同 (1)，但若 `str` 为空指针则返回零，而若在 `str` 的首 `strsz` 个字节找不到空字符则返回 `strsz`。

 若 `str` 不是指向空终结的字节字符串且 `strsz` 大于该字符数组的大小，则行为未定义。

**参数**

| str   | -    | 指向要检查的空终止字符串的指针 |
| ----- | ---- | ------------------------------ |
| strsz | -    | 要检查的最大字符数量           |

**返回值**

1） 空终止字节字符串 `str` 的长度。

2） 成功时为空终止字节字符串 `str` 的长度，若 `str` 是空指针则为零，若找不到空字符则为 `strsz`。

**注解**

​	`strnlen_s` 与 `wcsnlen_s` 是仅有的不调用运行时制约处理函数的[带边界检查函数](https://zh.cppreference.com/w/c/error)。它们是用于提供空终止字符串受限制支持的纯功能函数。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char str[] = "How many characters does this string contain?";
 
    printf("不计入空字符: %zu\n", strlen(str));
    printf("计入空字符:   %zu\n", sizeof str);
 
#ifdef __STDC_LIB_EXT1__
    printf("不计入空字符: %zu\n", strnlen_s(str, sizeof str));
#endif
}
```

​	可能的输出：

```txt
不计入空字符: 45
计入空字符:   46
不计入空字符: 45
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.6.3 The strlen function （第 TBD 页）

  - K.3.7.4.4 The strnlen_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.6.3 The strlen function （第 TBD 页）

  - K.3.7.4.4 The strnlen_s function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.3 The strlen function （第 372 页）

  - K.3.7.4.4 The strnlen_s function （第 623 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.3 The strlen function （第 334 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.3 The strlen function

**参阅**

| [wcslen (C95)<br />wcsnlen_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcslen) | 返回宽字符串的长度 (函数)           |
| ------------------------------------------------------------ | ----------------------------------- |
| [mblen<br />](https://zh.cppreference.com/w/c/string/multibyte/mblen) | 返回下一个多字节字符的字节数 (函数) |
| **strlen** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strlen)** |                                     |





### strncat

原址：[https://zh.cppreference.com/w/c/string/byte/strncat](https://zh.cppreference.com/w/c/string/byte/strncat)

作用：连接两个字符串的一定数量字符  (函数)

备注：
```c
// 在标头 <string.h> 定义
// (1)
char *strncat( char *dest, const char *src, size_t count );// (C99 前)
char *strncat( char *restrict dest, const char *restrict src, size_t count );// (C99 起)
errno_t strncat_s(char *restrict dest, rsize_t destsz,
                  const char *restrict src, rsize_t count);// (2)(C11 起)
```

1） 将来自 `src` 所指向的字符数组的至多 `count` 个字符，追加到 `dest` 所指向的空终止字节字符串的末尾，若找到空字符则停止。字符 `src[0]` 替换位于 `dest` 末尾的空终止符。总会在末尾追加终止空字符（故函数可写入的最大字节数是 `count+1`）。

 若目标数组没有对于 `dest` 和 `src` 的前 `count` 个字符加上终止空字符的足够空间，则行为未定义。若源与目标对象重叠，则行为未定义。若 `dest` 不是指向空终止字节字符串的指针，或 `src` 不是指向字符数组的指针，则行为未定义。

2） 同 (1)，但函数可以可用未指定值破坏目标数组的剩余部分（从最后写入字符到 `destsz`），以及在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `src` 或 `dest` 为空指针
  - `destsz` 或 `count` 为零或大于 RSIZE_MAX
  - `dest` 的首 `destsz` 个字节中无空字符
  - 会出现截断：`count` 与 `src` 长度的较小者，会超出 `dest` 的空终止符和 `destsz` 之间的可用空间。
  - 源与目标字符串之间会出现重叠

 若 `dest` 所指向的字符数组大小 < `strnlen(dest,destsz)+strnlen(src,count)+1` < `destsz` 则行为未定义；换言之，`destsz` 的错误值不暴露行将发生的缓冲区溢出。若 `src` 所指向的字符数组大小 < `strnlen(src,count)` < `destsz`；换言之，`count` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要后附到的空终止字节字符串的指针 |
| ------ | ---- | ------------------------------------ |
| src    | -    | 指向作为复制来源的字符数组的指针     |
| count  | -    | 要复制的最大字符数                   |
| destsz | -    | 目标缓冲区的大小                     |

**返回值**

1） 返回 `dest` 的副本。

2） 成功时返回零。错误时返回非零。错误时，亦写入零到 `dest[0]`（除非 `dest` 为空指针，或 `destsz` 为零或大于 RSIZE_MAX）。

**注解**

​	因为 `strncat` 需要在每次调用时找到 `dest` 的结尾，故用 `strncat` 将多个字符串连接成一体是低效的。

​	尽管截断以适应目标缓冲区是安全风险，从而是 `strncat_s` 的运行时制约违规，还是可以通过指定 `count` 等于目标数组大小减一获取截断行为：这将一如往常地复制首 `count` 个字节并后附空终止符：`strncat_s(dst, sizeof dst, src, (sizeof dst)-strnlen_s(dst, sizeof dst)-1);`。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h> 
#include <stdio.h>
#include <stdlib.h>
 
int main(void) 
{
    char str[50] = "Hello ";
    char str2[50] = "World!";
    strcat(str, str2);
    strncat(str, " Goodbye World!", 3);
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char s1[100] = "good";
    char s5[1000] = "bye";
    int r1 = strncat_s(s1, 100, s5, 1000); // r1 为 0，s1 保有 "goodbye\0"
    printf("s1 = %s, r1 = %d\n", s1, r1);
    char s2[6] = "hello";
    int r2 = strncat_s(s2, 6, "", 1); // r2 为 0，s2 保有 "hello\0"
    printf("s2 = %s, r2 = %d\n", s2, r2);
    char s3[6] = "hello";
    int r3 = strncat_s(s3, 6, "X", 2); // r3 非零，s3 保有 "\0"
    printf("s3 = %s, r3 = %d\n", s3, r3);
    // strncat_s 截断惯用法：
    char s4[7] = "abc";
    int r4 = strncat_s(s4, 7, "defghijklmn", 3); // r4 为 0，s4 保有 "abcdef\0"
    printf("s4 = %s, r4 = %d\n", s4, r4);
#endif
}
```

​	可能的输出：

```txt
Hello World! Go
s1 = goodbye, r1 = 0
s2 = hello, r2 = 0
s3 = , r3 = 22
s4 = abcdef, r4 = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.26.3.2 The strncat function （第 379 页）

  - K.3.7.2.2 The strncat_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.3.2 The strncat function （第 265-266 页）

  - K.3.7.2.2 The strncat_s function （第 449-450 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.3.2 The strncat function （第 364-365 页）

  - K.3.7.2.2 The strncat_s function （第 618-620 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.3.2 The strncat function （第 327-328 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.3.2 The strncat function

**参阅**

| [strcat <br />strcat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcat) | 连接两个字符串 (函数)                           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                       |
| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |
| **strncat** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strncat)** |                                                 |





### strncat_s

原址：[https://zh.cppreference.com/w/c/string/byte/strncat](https://zh.cppreference.com/w/c/string/byte/strncat)

作用：连接两个字符串的一定数量字符  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
// (1)
char *strncat( char *dest, const char *src, size_t count );// (C99 前)
char *strncat( char *restrict dest, const char *restrict src, size_t count );// (C99 起)
errno_t strncat_s(char *restrict dest, rsize_t destsz,
                  const char *restrict src, rsize_t count);// (2)(C11 起)
```

1） 将来自 `src` 所指向的字符数组的至多 `count` 个字符，追加到 `dest` 所指向的空终止字节字符串的末尾，若找到空字符则停止。字符 `src[0]` 替换位于 `dest` 末尾的空终止符。总会在末尾追加终止空字符（故函数可写入的最大字节数是 `count+1`）。

 若目标数组没有对于 `dest` 和 `src` 的前 `count` 个字符加上终止空字符的足够空间，则行为未定义。若源与目标对象重叠，则行为未定义。若 `dest` 不是指向空终止字节字符串的指针，或 `src` 不是指向字符数组的指针，则行为未定义。

2） 同 (1)，但函数可以可用未指定值破坏目标数组的剩余部分（从最后写入字符到 `destsz`），以及在运行时检测下列错误，并调用当前安装的[约束处理函数](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)：

  - `src` 或 `dest` 为空指针
  - `destsz` 或 `count` 为零或大于 RSIZE_MAX
  - `dest` 的首 `destsz` 个字节中无空字符
  - 会出现截断：`count` 与 `src` 长度的较小者，会超出 `dest` 的空终止符和 `destsz` 之间的可用空间。
  - 源与目标字符串之间会出现重叠

 若 `dest` 所指向的字符数组大小 < `strnlen(dest,destsz)+strnlen(src,count)+1` < `destsz` 则行为未定义；换言之，`destsz` 的错误值不暴露行将发生的缓冲区溢出。若 `src` 所指向的字符数组大小 < `strnlen(src,count)` < `destsz`；换言之，`count` 的错误值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要后附到的空终止字节字符串的指针 |
| ------ | ---- | ------------------------------------ |
| src    | -    | 指向作为复制来源的字符数组的指针     |
| count  | -    | 要复制的最大字符数                   |
| destsz | -    | 目标缓冲区的大小                     |

**返回值**

1） 返回 `dest` 的副本。

2） 成功时返回零。错误时返回非零。错误时，亦写入零到 `dest[0]`（除非 `dest` 为空指针，或 `destsz` 为零或大于 RSIZE_MAX）。

**注解**

​	因为 `strncat` 需要在每次调用时找到 `dest` 的结尾，故用 `strncat` 将多个字符串连接成一体是低效的。

​	尽管截断以适应目标缓冲区是安全风险，从而是 `strncat_s` 的运行时制约违规，还是可以通过指定 `count` 等于目标数组大小减一获取截断行为：这将一如往常地复制首 `count` 个字节并后附空终止符：`strncat_s(dst, sizeof dst, src, (sizeof dst)-strnlen_s(dst, sizeof dst)-1);`。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h> 
#include <stdio.h>
#include <stdlib.h>
 
int main(void) 
{
    char str[50] = "Hello ";
    char str2[50] = "World!";
    strcat(str, str2);
    strncat(str, " Goodbye World!", 3);
    puts(str);
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char s1[100] = "good";
    char s5[1000] = "bye";
    int r1 = strncat_s(s1, 100, s5, 1000); // r1 为 0，s1 保有 "goodbye\0"
    printf("s1 = %s, r1 = %d\n", s1, r1);
    char s2[6] = "hello";
    int r2 = strncat_s(s2, 6, "", 1); // r2 为 0，s2 保有 "hello\0"
    printf("s2 = %s, r2 = %d\n", s2, r2);
    char s3[6] = "hello";
    int r3 = strncat_s(s3, 6, "X", 2); // r3 非零，s3 保有 "\0"
    printf("s3 = %s, r3 = %d\n", s3, r3);
    // strncat_s 截断惯用法：
    char s4[7] = "abc";
    int r4 = strncat_s(s4, 7, "defghijklmn", 3); // r4 为 0，s4 保有 "abcdef\0"
    printf("s4 = %s, r4 = %d\n", s4, r4);
#endif
}
```

​	可能的输出：

```txt
Hello World! Go
s1 = goodbye, r1 = 0
s2 = hello, r2 = 0
s3 = , r3 = 22
s4 = abcdef, r4 = 0
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.26.3.2 The strncat function （第 379 页）

  - K.3.7.2.2 The strncat_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.3.2 The strncat function （第 265-266 页）

  - K.3.7.2.2 The strncat_s function （第 449-450 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.3.2 The strncat function （第 364-365 页）

  - K.3.7.2.2 The strncat_s function （第 618-620 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.3.2 The strncat function （第 327-328 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.3.2 The strncat function

**参阅**

| [strcat <br />strcat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcat) | 连接两个字符串 (函数)                           |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                       |
| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |
| **strncat** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strncat)** |                                                 |
`__STDC_WANT_LIB_EXT1__`：






### strncmp

原址：[https://zh.cppreference.com/w/c/string/byte/strncmp](https://zh.cppreference.com/w/c/string/byte/strncmp)

作用：比较两个字符串的一定数量字符  (函数)

备注：
```c
// 在标头 <string.h> 定义
int strncmp( const char *lhs, const char *rhs, size_t count );
```

​	比较两个可能空终止的数组的至多 `count` 个字符。按字典序进行比较。不比较后随空字符的字符。

​	结果的符号是被比较的数组中首对字符（都转译成 `unsigned char`）的值间的差的符号。

​	若出现越过 `lhs` 或 `rhs` 结尾的访问，则行为未定义。若 `lhs` 或 `rhs` 为空指针，则行为未定义。

**参数**

| lhs, rhs | -    | 指向要比较的可能空终止的数组的指针 |
| -------- | ---- | ---------------------------------- |
| count    | -    | 要比较的最大字符数                 |

**返回值**

​	若字典序中 `lhs` 先于 `rhs` 出现则为负值。

​	若 `lhs` 与 `rhs` 比较相等，或若 count 为零，则为零。

​	若字典序中 `lhs` 后于 `rhs` 出现则为正值。

**注解**

​	不同于 [strcoll](https://zh.cppreference.com/w/c/string/byte/strcoll) 和 [strxfrm](https://zh.cppreference.com/w/c/string/byte/strxfrm)，此函数不考虑本地环境。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
void demo(const char* lhs, const char* rhs, int sz)
{
    const int rc = strncmp(lhs, rhs, sz);
    if (rc < 0)
        printf("First %d chars of [%s] precede [%s]\n", sz, lhs, rhs);
    else if (rc > 0)
        printf("First %d chars of [%s] follow [%s]\n", sz, lhs, rhs);
    else
        printf("First %d chars of [%s] equal [%s]\n", sz, lhs, rhs);
}
int main(void)
{
    const char* string = "Hello World!";
    demo(string, "Hello!", 5);
    demo(string, "Hello", 10);
    demo(string, "Hello there", 10);
    demo("Hello, everybody!" + 12, "Hello, somebody!" + 11, 5);
}
```

​	输出：

```txt
First 5 chars of [Hello World!] equal [Hello!]
First 10 chars of [Hello World!] follow [Hello]
First 10 chars of [Hello World!] precede [Hello there]
First 5 chars of [body!] equal [body!]
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.4.4 The strncmp function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.4.4 The strncmp function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.4.4 The strncmp function （第 366 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.4.4 The strncmp function （第 329 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.4.4 The strncmp function

**参阅**

| [strcmp<br />](https://zh.cppreference.com/w/c/string/byte/strcmp) | 比较两个字符串 (函数)                   |
| ------------------------------------------------------------ | --------------------------------------- |
| [wcsncmp (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsncmp) | 比较来自两个宽字符串的一定量字符 (函数) |
| [memcmp<br />](https://zh.cppreference.com/w/c/string/byte/memcmp) | 比较两块缓冲区 (函数)                   |
| [strcoll<br />](https://zh.cppreference.com/w/c/string/byte/strcoll) | 比较两个字符串，根据当前本地环境 (函数) |
| **strncmp** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strncmp)** |                                         |





### strncpy

原址：[https://zh.cppreference.com/w/c/string/byte/strncpy](https://zh.cppreference.com/w/c/string/byte/strncpy)

作用：从字符串复制一定数量的字符到另一个  (函数)

备注：
```c
// 在标头 <string.h> 定义
// (1)
char *strncpy( char *dest, const char *src, size_t count );// (C99 前)
char *strncpy( char *restrict dest, const char *restrict src, size_t count );// (C99 起)
errno_t strncpy_s(char *restrict dest, rsize_t destsz,
                  const char *restrict src, rsize_t count);// (2)(C11 起)
```

1） 复制 `src` 所指向的字符数组的至多 `count` 个字符（包含空终止字符，但不包含后随空字符的任何字符）到 `dest` 所指向的字符数组。

 若在完全复制整个 `src` 数组前抵达 `count`，则结果的字符数组不是空终止的。

 若在复制来自 `src` 的空终止字符后未抵达 `count`，则写入额外的空字符到 `dest`，直至写入总共 `count` 个字符。

 若字符数组重叠，若 `dest` 或 `src` 不是指向字符数组的指针（包含若 `dest` 或 `src` 为空指针），若 `dest` 所指向的数组大小小于 `count`，或若 `src` 所指向的数组大小小于 `count` 且它不含空字符，则行为未定义。

2） 同 (1)，但此函数不持续写入零到目标数组以填满 `count`，它在写入空终止字符后停止（若源中无空字符，则它于 `dest[count]` 写入一个然后停止）。并且在运行时检测下列错误并调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

  - `src` 或 `dest` 是空指针
  - `destsz` 零或大于 RSIZE_MAX
  - `count` 大于 RSIZE_MAX
  - `count` 大于或等于 `destsz`，但 `destsz` 小于或等于 `strnlen_s(src, count)`，换言之，会出现截断
  - 源和目标字符串间会出现重叠

 若 `dest` 所指的字符数组大小 < `strnlen_s(src, destsz)` <= `destsz` 则行为未定义；换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。若 `src` 所指的字符数组大小 < `strnlen_s(src, count)` < `destsz` 则行为未定义；换言之，错误的 `count` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要复制到的字符数组的指针 |
| ------ | ---- | ---------------------------- |
| src    | -    | 指向复制来源的字符数组的指针 |
| count  | -    | 要复制的最大字符数           |
| destsz | -    | 目标缓冲区的大小             |

**返回值**

1） 返回 `dest` 的副本

2） 成功时返回零，错误时返回非零。而且，在错误时写入零到 `dest[0]`（除非 `dest` 为空指针，或 `destsz` 为零或大于 RSIZE_MAX），而且可能以未指定值破坏目标数组的剩余部分。

**注解**

​	按 C11 后的 DR 468 更正，`strncpy_s` 不同于 [strcpy_s](https://zh.cppreference.com/w/c/string/byte/strcpy)，仅若错误发生才被允许破坏目标数组的剩余部分。

​	不同于 `strncpy`，`strncpy_s` 不以零填充目标数组。这是转换既存代码到边界检查版本的常见错误源。

​	尽管适合目标缓冲区的截断是安全风险，从而是 `strncpy_s` 的运行时制约违规，还是可通过指定 `count` 等于目标数组大小减一以获取截断行为：它会复制首 `count` 个字节，并照常添加空终止符：`strncpy_s(dst, sizeof dst, src, (sizeof dst)-1);`

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
 
int main(void)
{
    char src[] = "hi";
    char dest[6] = "abcdef"; // 无空字符
    strncpy(dest, src, 5); // 写入五个字符 'h', 'i', '\0', '\0', '\0' 到 dest
    printf("strncpy(dest, src, 5) to a 6-byte dest gives : ");
    for(size_t n = 0; n < sizeof dest; ++n) {
        char c = dest[n];
        c ? printf("'%c' ", c) : printf("'\\0' ");
    }
 
    printf("\nstrncpy(dest2, src, 2) to a 2-byte dst gives : ");
    char dest2[2];
    strncpy(dest2, src, 2); // 截断：写入二个字符 'h', 'i', 到 dest2
    for (size_t n = 0; n < sizeof dest2; ++n) {
        char c = dest2[n];
        c ? printf("'%c' ", c) : printf("'\\0' ");
    }
    printf("\n");
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char dst1[6], src1[100] = "hello";
    int r1 = strncpy_s(dst1, 6, src1, 100);      // 写入 0 到 r1，6 个字符到 dst1
    printf("dst1 = \"%s\", r1 = %d\n", dst1,r1); // 'h','e','l','l','o','\0' 到 dst1
 
    char dst2[5], src2[7] = {'g','o','o','d','b','y','e'};
    int r2 = strncpy_s(dst2, 5, src2, 7);        // 复制溢出目标数组
    printf("dst2 = \"%s\", r2 = %d\n", dst2,r2); // 写入非零到 r2，'\0' 到 dst2[0]
 
    char dst3[5];
    int r3 = strncpy_s(dst3, 5, src2, 4);        // 写入 0 到 r3，5 个字符到 dst3
    printf("dst3 = \"%s\", r3 = %d\n", dst3,r3); // 'g', 'o', 'o', 'd', '\0' 到 dst3 
#endif
}
```

​	可能的输出：

```txt
strncpy(dest, src, 5) to a 6-byte dst gives : 'h' 'i' '\0' '\0' '\0' 'f'
strncpy(dest2, src, 2) to a 2-byte dst gives : 'h' 'i'
dst1 = "hello", r1 = 0
dst2 = "", r2 = 22
dst3 = "good", r3 = 0
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.4 The strncpy function （第 265 页）

  - K.3.7.1.4 The strncpy_s function （第 447-448 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.4 The strncpy function （第 363-364 页）

  - K.3.7.1.4 The strncpy_s function （第 616-617 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.4 The strncpy function （第 326-327 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.4 The strncpy function

**参阅**

| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)               |
| [strndup (动态内存 TR)<br />](https://zh.cppreference.com/w/c/experimental/dynamic/strndup) | 分配字符串副本，至多到指定的大小 (函数) |
| **strncpy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strncpy)** |                                         |





### strncpy_s

原址：[https://zh.cppreference.com/w/c/string/byte/strncpy](https://zh.cppreference.com/w/c/string/byte/strncpy)

作用：从字符串复制一定数量的字符到另一个  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
// (1)
char *strncpy( char *dest, const char *src, size_t count );// (C99 前)
char *strncpy( char *restrict dest, const char *restrict src, size_t count );// (C99 起)
errno_t strncpy_s(char *restrict dest, rsize_t destsz,
                  const char *restrict src, rsize_t count);// (2)(C11 起)
```

1） 复制 `src` 所指向的字符数组的至多 `count` 个字符（包含空终止字符，但不包含后随空字符的任何字符）到 `dest` 所指向的字符数组。

 若在完全复制整个 `src` 数组前抵达 `count`，则结果的字符数组不是空终止的。

 若在复制来自 `src` 的空终止字符后未抵达 `count`，则写入额外的空字符到 `dest`，直至写入总共 `count` 个字符。

 若字符数组重叠，若 `dest` 或 `src` 不是指向字符数组的指针（包含若 `dest` 或 `src` 为空指针），若 `dest` 所指向的数组大小小于 `count`，或若 `src` 所指向的数组大小小于 `count` 且它不含空字符，则行为未定义。

2） 同 (1)，但此函数不持续写入零到目标数组以填满 `count`，它在写入空终止字符后停止（若源中无空字符，则它于 `dest[count]` 写入一个然后停止）。并且在运行时检测下列错误并调用当前安装的[制约处理](https://zh.cppreference.com/w/c/error/set_constraint_handler_s)函数：

  - `src` 或 `dest` 是空指针
  - `destsz` 零或大于 RSIZE_MAX
  - `count` 大于 RSIZE_MAX
  - `count` 大于或等于 `destsz`，但 `destsz` 小于或等于 `strnlen_s(src, count)`，换言之，会出现截断
  - 源和目标字符串间会出现重叠

 若 `dest` 所指的字符数组大小 < `strnlen_s(src, destsz)` <= `destsz` 则行为未定义；换言之，错误的 `destsz` 值不暴露行将发生的缓冲区溢出。若 `src` 所指的字符数组大小 < `strnlen_s(src, count)` < `destsz` 则行为未定义；换言之，错误的 `count` 值不暴露行将发生的缓冲区溢出。

**参数**

| dest   | -    | 指向要复制到的字符数组的指针 |
| ------ | ---- | ---------------------------- |
| src    | -    | 指向复制来源的字符数组的指针 |
| count  | -    | 要复制的最大字符数           |
| destsz | -    | 目标缓冲区的大小             |

**返回值**

1） 返回 `dest` 的副本

2） 成功时返回零，错误时返回非零。而且，在错误时写入零到 `dest[0]`（除非 `dest` 为空指针，或 `destsz` 为零或大于 RSIZE_MAX），而且可能以未指定值破坏目标数组的剩余部分。

**注解**

​	按 C11 后的 DR 468 更正，`strncpy_s` 不同于 [strcpy_s](https://zh.cppreference.com/w/c/string/byte/strcpy)，仅若错误发生才被允许破坏目标数组的剩余部分。

​	不同于 `strncpy`，`strncpy_s` 不以零填充目标数组。这是转换既存代码到边界检查版本的常见错误源。

​	尽管适合目标缓冲区的截断是安全风险，从而是 `strncpy_s` 的运行时制约违规，还是可通过指定 `count` 等于目标数组大小减一以获取截断行为：它会复制首 `count` 个字节，并照常添加空终止符：`strncpy_s(dst, sizeof dst, src, (sizeof dst)-1);`

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
 
int main(void)
{
    char src[] = "hi";
    char dest[6] = "abcdef"; // 无空字符
    strncpy(dest, src, 5); // 写入五个字符 'h', 'i', '\0', '\0', '\0' 到 dest
    printf("strncpy(dest, src, 5) to a 6-byte dest gives : ");
    for(size_t n = 0; n < sizeof dest; ++n) {
        char c = dest[n];
        c ? printf("'%c' ", c) : printf("'\\0' ");
    }
 
    printf("\nstrncpy(dest2, src, 2) to a 2-byte dst gives : ");
    char dest2[2];
    strncpy(dest2, src, 2); // 截断：写入二个字符 'h', 'i', 到 dest2
    for (size_t n = 0; n < sizeof dest2; ++n) {
        char c = dest2[n];
        c ? printf("'%c' ", c) : printf("'\\0' ");
    }
    printf("\n");
 
#ifdef __STDC_LIB_EXT1__
    set_constraint_handler_s(ignore_handler_s);
    char dst1[6], src1[100] = "hello";
    int r1 = strncpy_s(dst1, 6, src1, 100);      // 写入 0 到 r1，6 个字符到 dst1
    printf("dst1 = \"%s\", r1 = %d\n", dst1,r1); // 'h','e','l','l','o','\0' 到 dst1
 
    char dst2[5], src2[7] = {'g','o','o','d','b','y','e'};
    int r2 = strncpy_s(dst2, 5, src2, 7);        // 复制溢出目标数组
    printf("dst2 = \"%s\", r2 = %d\n", dst2,r2); // 写入非零到 r2，'\0' 到 dst2[0]
 
    char dst3[5];
    int r3 = strncpy_s(dst3, 5, src2, 4);        // 写入 0 到 r3，5 个字符到 dst3
    printf("dst3 = \"%s\", r3 = %d\n", dst3,r3); // 'g', 'o', 'o', 'd', '\0' 到 dst3 
#endif
}
```

​	可能的输出：

```txt
strncpy(dest, src, 5) to a 6-byte dst gives : 'h' 'i' '\0' '\0' '\0' 'f'
strncpy(dest2, src, 2) to a 2-byte dst gives : 'h' 'i'
dst1 = "hello", r1 = 0
dst2 = "", r2 = 22
dst3 = "good", r3 = 0
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.2.4 The strncpy function （第 265 页）

  - K.3.7.1.4 The strncpy_s function （第 447-448 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.2.4 The strncpy function （第 363-364 页）

  - K.3.7.1.4 The strncpy_s function （第 616-617 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.2.4 The strncpy function （第 326-327 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.2.4 The strncpy function

**参阅**

| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)               |
| ------------------------------------------------------------ | --------------------------------------- |
| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)               |
| [strndup (动态内存 TR)<br />](https://zh.cppreference.com/w/c/experimental/dynamic/strndup) | 分配字符串副本，至多到指定的大小 (函数) |
| **strncpy** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strncpy)** |                                         |
`__STDC_WANT_LIB_EXT1__`：






### strndup

原址：[https://zh.cppreference.com/w/c/string/byte/strndup](https://zh.cppreference.com/w/c/string/byte/strndup)

作用：分配拥有指定大小的字符串副本   (函数)

备注：
```c
// 在标头 <string.h> 定义
char *strndup( const char *src, size_t size );// (C23 起)
```

​	返回指向含有来自 `src` 所指向的字符串的至多 `size` 个字节的副本的空终止字节字符串的指针。如同通过调用 [malloc](https://zh.cppreference.com/w/c/memory/malloc) 获得新字符串的空间。若在首 `size` 个字节中未遇到空终止符，则将它后附到复制的字符串。

​	必须将返回的指针传递给 [free](https://zh.cppreference.com/w/c/memory/free) 以避免内存泄漏。

​	若出现错误，则返回空指针值并可能设置 [errno](https://zh.cppreference.com/w/c/error/errno)。

**参数**

| src  | -    | 指向要复制的空终止字节字符串的指针 |
| ---- | ---- | ---------------------------------- |
| size | -    | 要从 `src` 复制的最大字节数        |

**返回值**

​	指向新分配的字符串的指针，或若出现错误则为空指针值。

**注解**

​	函数等同于 [POSIX strndup](http://pubs.opengroup.org/onlinepubs/9699919799/functions/strdup.html)，除了允许但不要求它在错误时设置 [errno](https://zh.cppreference.com/w/c/error/errno)。

**示例**

```c
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    const size_t n = 3;
 
    const char *src = "Replica";
    char *dup = strndup(src, n);
    printf("strndup(\"%s\", %lu) == \"%s\"\n", src, n, dup);
    free(dup);
 
    src = "Hi";
    dup = strndup(src, n);
    printf("strndup(\"%s\", %lu) == \"%s\"\n", src, n, dup);
    free(dup);
 
    const char arr[] = {'A','B','C','D'}; // NB ：无尾随 '\0'
    dup = strndup(arr, n);
    printf("strndup({'A','B','C','D'}, %lu) == \"%s\"\n", n, dup);
    free(dup);
}
```

​	输出：

```txt
strndup("Replica", 3) == "Rep"
strndup("Hi", 3) == "Hi"
strndup({'A','B','C','D'}, 3) == "ABC"
```

**参阅**

| [strdup (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strdup) | 分配字符串的副本 (函数)   |
| ------------------------------------------------------------ | ------------------------- |
| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数) |
| [malloc<br />](https://zh.cppreference.com/w/c/memory/malloc) | 分配内存 (函数)           |
| [free<br />](https://zh.cppreference.com/w/c/memory/free)  | 归还之前分配的内存 (函数) |





### strnlen

原址：

作用：

备注：





### strnlen_s

原址：[https://zh.cppreference.com/w/c/string/byte/strlen](https://zh.cppreference.com/w/c/string/byte/strlen)

作用：返回给定字符串的长度  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
size_t strlen( const char* str );// (1)
size_t strnlen_s( const char* str, size_t strsz );// (2)(C11 起)
```

1） 返回给定空终止字符串的长度，即首元素为 `str` 所指的字符数组中，直至且不包含首个空字符的字符数。

 若 `str` 不是指向空终止字节字符串的指针则行为未定义。

2） 同 (1)，但若 `str` 为空指针则返回零，而若在 `str` 的首 `strsz` 个字节找不到空字符则返回 `strsz`。

 若 `str` 不是指向空终结的字节字符串且 `strsz` 大于该字符数组的大小，则行为未定义。

**参数**

| str   | -    | 指向要检查的空终止字符串的指针 |
| ----- | ---- | ------------------------------ |
| strsz | -    | 要检查的最大字符数量           |

**返回值**

1） 空终止字节字符串 `str` 的长度。

2） 成功时为空终止字节字符串 `str` 的长度，若 `str` 是空指针则为零，若找不到空字符则为 `strsz`。

**注解**

​	`strnlen_s` 与 `wcsnlen_s` 是仅有的不调用运行时制约处理函数的[带边界检查函数](https://zh.cppreference.com/w/c/error)。它们是用于提供空终止字符串受限制支持的纯功能函数。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char str[] = "How many characters does this string contain?";
 
    printf("不计入空字符: %zu\n", strlen(str));
    printf("计入空字符:   %zu\n", sizeof str);
 
#ifdef __STDC_LIB_EXT1__
    printf("不计入空字符: %zu\n", strnlen_s(str, sizeof str));
#endif
}
```

​	可能的输出：

```txt
不计入空字符: 45
计入空字符:   46
不计入空字符: 45
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.6.3 The strlen function （第 TBD 页）

  - K.3.7.4.4 The strnlen_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.6.3 The strlen function （第 TBD 页）

  - K.3.7.4.4 The strnlen_s function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.6.3 The strlen function （第 372 页）

  - K.3.7.4.4 The strnlen_s function （第 623 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.6.3 The strlen function （第 334 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.6.3 The strlen function

**参阅**

| [wcslen (C95)<br />wcsnlen_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcslen) | 返回宽字符串的长度 (函数)           |
| ------------------------------------------------------------ | ----------------------------------- |
| [mblen<br />](https://zh.cppreference.com/w/c/string/multibyte/mblen) | 返回下一个多字节字符的字节数 (函数) |
| **strlen** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strlen)** |                                     |
`__STDC_WANT_LIB_EXT1__`：






### strpbrk

原址：[https://zh.cppreference.com/w/c/string/byte/strpbrk](https://zh.cppreference.com/w/c/string/byte/strpbrk)

作用：查找字符串中的任意字符在另一个字符串中的首个位置  (函数)

备注：
```c
// 在标头 <string.h> 定义
char *strpbrk( const char *dest, const char *breakset );// (1)
/*QChar*/ *strpbrk( /*QChar*/ *dest, const char *breakset );// (2)(C23 起)
```

1） 在 `dest` 所指向的空终止字节串中，扫描来自 `breakset` 所指向的空终止字节串的任何字符，并返回指向该字符的指针。

2） 等价于 (1) 的泛型函数。令 `T` 为未限定的 字符对象类型。

  - 若 `dest` 类型为 `const T*`，则返回类型为 `const char*`。
  - 否则，若 `dest` 类型为 `T*`，返回类型为 `char*`。
  - 否则，行为未定义。

如果这些泛型函数中的某个宏定义被抑制无法访问实际函数（比如当使用了 `(strpbrk)` 或使用了函数指针时），则实际函数声明 (1) 即变得可见。

​	若 `dest` 或 `breakset` 不是指向空终止字节字符串的指针，则行为未定义。

**参数**

| dest     | -    | 指向要分析的空终止字节字符串的指针         |
| -------- | ---- | ------------------------------------------ |
| breakset | -    | 指向含要搜索的字符的空终止字节字符串的指针 |

**返回值**

​	指向 `dest` 中首个亦在 `breakset` 中的字符的指针，或若这种字符不存在则为空指针。

**注解**

​	名称代表“字符串指针打断 (string pointer break) ”，因为它返回指向首个分隔符（“打断”）的指针。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char* str = "hello world, friend of mine!";
    const char* sep = " ,!";
 
    unsigned int cnt = 0;
    do
    {
       str = strpbrk(str, sep); // 寻找分隔符
       if (str) str += strspn(str, sep); // 跳过分隔符
       ++cnt; // 增加词计数
    }
    while(str && *str);
 
    printf("共有 %d 个单词\n", cnt);
}
```

​	输出：

```txt
共有 5 个单词
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.4 The strpbrk function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.4 The strpbrk function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.4 The strpbrk function （第 368 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.4 The strpbrk function （第 331 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.4 The strpbrk function

**参阅**

| [strcspn<br />](https://zh.cppreference.com/w/c/string/byte/strcspn) | 返回另一个字符串所不具有的字符分割的最大起始段长度 (函数) |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [strchr<br />](https://zh.cppreference.com/w/c/string/byte/strchr) | 查找字符的首次出现 (函数)                                 |
| [strtok <br />strtok_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strtok) | 查找字节字符串中的下一个记号 (函数)                       |
| **strpbrk** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strpbrk)** |                                                           |





### strrchr

原址：[https://zh.cppreference.com/w/c/string/byte/strrchr](https://zh.cppreference.com/w/c/string/byte/strrchr)

作用：查找字符的最后一次出现  (函数)

备注：
```c
// 在标头 <string.h> 定义
char* strrchr( const char* str, int ch );// (1)
/*QChar*/* strrchr( /*QChar*/* str, int ch );// (2)(C23 起)
```

1） 寻找 `ch`（如同用 `(char)ch` 转换到 `char` 后）在 `str` 所指向的空终止字节串中（将每个字符转译成 `unsigned char`）的最后出现位置。若搜索 `'\0'`，则认为终止空字符为字符串的一部分，而且能找到。

2） 等价于 (1) 的泛型函数。令 `T` 为未限定的 字符对象类型。

  - 若 `str` 类型为 `const T*`，则返回类型为 `const char*`。
  - 否则，若 `str` 类型为 `T*`，返回类型为 `char*`。
  - 否则，行为未定义。

如果这些泛型函数中的某个宏定义被抑制无法访问实际函数（比如当使用了 `(strrchr)` 或使用了函数指针时），则实际函数声明 (1) 即变得可见。

​	若 `str` 不是指向空终止字节串的指针，则行为未定义。

**参数**

| str  | -    | 指向要分析的空终止字节字符串的指针 |
| ---- | ---- | ---------------------------------- |
| ch   | -    | 要搜索的字符                       |

**返回值**

​	指向 `str` 中找到的字符的指针，或若找不到这种字符则为空指针。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    char szSomeFileName[] = "foo/bar/foobar.txt";
    char* pLastSlash = strrchr(szSomeFileName, '/');
    char* pszBaseName = pLastSlash ? pLastSlash + 1 : szSomeFileName;
    printf("Base Name: %s", pszBaseName);
}
```

​	输出：

```txt
Base Name: foobar.txt
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.5 The strrchr function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.5 The strrchr function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.5 The strrchr function （第 368-369 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.5 The strrchr function （第 331 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.5 The strrchr function

**参阅**

| [strchr<br />](https://zh.cppreference.com/w/c/string/byte/strchr) | 查找字符的首次出现 (函数)                               |
| ------------------------------------------------------------ | ------------------------------------------------------- |
| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数) |
| **strrchr** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strrchr)** |                                                         |





### strspn

原址：[https://zh.cppreference.com/w/c/string/byte/strspn](https://zh.cppreference.com/w/c/string/byte/strspn)

作用：返回由另一个字符串中的字符分割的最大起始段长度   (函数)

备注：
```c
// 在标头 <string.h> 定义
size_t strspn( const char *dest, const char *src );
```

​	返回 `dest` 所指向的空终止字节串的最大起始段（span）长度，段仅由 `src` 所指向的空终止字节字符串中找到的字符组成。

​	若 `dest` 或 `src` 不是指向空终止字节字符串的指针，则行为未定义。

**参数**

| dest | -    | 指向要分析的空终止字节字符串的指针           |
| ---- | ---- | -------------------------------------------- |
| src  | -    | 指向含有要搜索的字符的空终止字节字符串的指针 |

**返回值**

​	仅由来自 `src` 所指向的空终止字节字符串的字符组成的最大起始段长度。

**示例**

```c
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    const char* string = "abcde312$#@";
    const char* low_alpha = "qwertyuiopasdfghjklzxcvbnm";
 
    size_t spnsz = strspn(string, low_alpha);
    printf("跳过 '%s' 中的开头小写字母\n"
           "剩余 '%s'\n", string, string + spnsz);
}
```

​	输出：

```txt
跳过 'abcde312$#@' 中的开头小写字母
剩余 '312$#@'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.6 The strspn function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.6 The strspn function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.6 The strspn function （第 369 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.6 The strspn function （第 332 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.6 The strspn function

**参阅**

| [strcspn<br />](https://zh.cppreference.com/w/c/string/byte/strcspn) | 返回另一个字符串所不具有的字符分割的最大起始段长度 (函数)    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcsspn (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsspn) | 返回仅由另一个宽字符串中出现的宽字符分隔的最长首段长度 (函数) |
| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数)      |
| **strspn** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strspn)** |                                                              |





### strstr

原址：[https://zh.cppreference.com/w/c/string/byte/strstr](https://zh.cppreference.com/w/c/string/byte/strstr)

作用：查找子串字符的首次出现  (函数)

备注：
```c
// 在标头 <string.h> 定义
char* strstr( const char* str, const char* substr );// (1)
/*QChar*/* strstr( /*QChar*/* str, const char* substr );// (2)(C23 起)
```

1） 查找 `substr` 所指的空终止字节字符串在 `str` 所指的空终止字节字符串中的首次出现。不比较空终止字符。

2） 等价于 (1) 的泛型函数。令 `T` 为未限定的 字符对象类型。

  - 若 `str` 类型为 `const T*`，则返回类型为 `const char*`。
  - 否则，若 `str` 类型为 `T*`，返回类型为 `char*`。
  - 否则，行为未定义。

如果这些泛型函数中的某个宏定义被抑制无法访问实际函数（比如当使用了 `(strstr)` 或使用了函数指针时），则实际函数声明 (1) 即变得可见。

​	若 `str` 或 `substr` 不是指向空终止字节字符串的指针，则行为未定义。

**参数**

| str    | -    | 指向要检验的空终止字节字符串的指针 |
| ------ | ---- | ---------------------------------- |
| substr | -    | 指向要查找的空终止字节字符串的指针 |

**返回值**

​	指向于 `str` 中找到的子串首字符的指针，或若找不到该子串则为空指针。若 `substr` 指向空字符串，则返回 `str`。

**示例**

```c
#include <string.h>
#include <stdio.h>
 
void find_str(char const* str, char const* substr)
{
    char const* pos = strstr(str, substr);
    pos ? printf("找到字符串 [%s] 位于 [%s] 的位置 %td\n",
                 substr, str, pos - str)
        : printf("没有在 [%s] 中找到 [%s]\n",
                 str, substr);
}
 
int main(void) 
{
    char const* str = "one two three";
    find_str(str, "two");
    find_str(str, "");
    find_str(str, "nine");
    find_str(str, "n");
 
    return 0;
}
```

​	输出：

```txt
找到字符串 [two] 位于 [one two three] 的位置 4
找到字符串 [] 位于 [one two three] 的位置 0
没有在 [one two three] 中找到 [nine]
找到字符串 [n] 位于 [one two three] 的位置 1
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.7 The strstr function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.7 The strstr function （第 269 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.7 The strstr function （第 369 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.7 The strstr function （第 332 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.7 The strstr function

**参阅**

| [strchr<br />](https://zh.cppreference.com/w/c/string/byte/strchr) | 查找字符的首次出现 (函数)     |
| ------------------------------------------------------------ | ----------------------------- |
| [strrchr<br />](https://zh.cppreference.com/w/c/string/byte/strrchr) | 查找字符的最后一次出现 (函数) |
| **strstr** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strstr)** |                               |





### strtok

原址：[https://zh.cppreference.com/w/c/string/byte/strtok](https://zh.cppreference.com/w/c/string/byte/strtok)

作用：查找字节字符串中的下一个记号  (函数)

备注：
```c
// 在标头 <string.h> 定义
// (1)
char* strtok( char* str, const char* delim );// (C99 前)
char* strtok( char* restrict str, const char* restrict delim );// (C99 起)
char* strtok_s( char* restrict str, rsize_t* restrict strmax,
                const char* restrict delim, char** restrict ptr );// (2)(C11 起)
```

​	记号化空终止字节字符串。

1） 对 `strtok` 进行一系列调用，将 `str` 指向的字符串拆分为记号序列，记号之间以 `delim` 中的某个字符分隔。调用序列中的每次调用都有一个*搜索目标* ﻿：

- 如果 `str` 非空，那么该调用是序列中的*首次调用*。搜索目标是 `str` 指向的空终止字节字符串。
- 如果 `str` 为空，那么该调用是序列中的*后续调用*。搜索目标由系列中的上一次调用确定。

 序列中的每次调用都会在搜索目标中搜索第一个**不**在 `delim` 指向的*分隔字符串* ﻿中出现的字符，每次调用中分隔字符串可以不一致。

- 如果没有找到这种字符，那么搜索目标中没有任何记号。序列中的下次调用的搜索目标保持不变。[[1\]](https://zh.cppreference.com/w/c/string/byte/strtok#cite_note-1)

- 如果找到了这种字符，那么它就是当前记号的起始。然后

   

  ```
  strtok
  ```

   

  会从此处开始搜索第一个在分隔字符串中出现的字符。

  - 如果没有找到这种字符，那么当前记号会持续到搜索目标的末尾。序列中的下次调用的搜索目标是空字符串。[[2\]](https://zh.cppreference.com/w/c/string/byte/strtok#cite_note-2)
  - 如果找到了这种字符，那么会用空字符覆盖它，并结束当前记号。序列中的下次调用的搜索目标从下一字符开始。

 如果 `str` 或 `delim` 不是指向空终止字节字符串的指针，那么行为未定义。

2） 同 (1)，但有以下不同：

- 每次调用都会将 `str` 中留待查看的字符数写入 `*strmax`，并将记号化器的内部状态写入 `*ptr`。

- 序列中的每次后续调用都必须传递先前的调用用以存储值的 `strmax` 和 `ptr`。

- 在运行时检测下列错误并调用当前安装的

  制约处理

  函数，而不存储任何内容到

   

  `ptr`

   

  所指向的对象：

  - `strmax`，`delim` 或 `ptr` 是空指针。
  - 对于序列中的后续调用，`*ptr` 是空指针。
  - `*strmax` 大于 RSIZE_MAX。
  - 找到的记号的末尾没有在搜索目标的开头 `*strmax` 个字符中出现。

 如果 `str` 指向的字符数组缺少空终止符，而 `strmax` 指向的值大于该字符数组长度，那么行为未定义。

 同所有边界检查函数，`strtok_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<string.h>`](https://zh.cppreference.com/w/c/header/string) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

1. [↑](https://zh.cppreference.com/w/c/string/byte/strtok#cite_ref-1) 后续调用使用其他分隔字符串仍然有可能组成记号。
2. [↑](https://zh.cppreference.com/w/c/string/byte/strtok#cite_ref-2) 后续调用中无法再组成记号。

**参数**

| str    | -    | 指向要记号化的空终止字节字符串的指针                         |
| ------ | ---- | ------------------------------------------------------------ |
| delim  | -    | 指向标识分隔符的空终止字节字符串的指针                       |
| strmax | -    | 指向最初保有 `str` 长度的对象指针：`strtok_s` 存储留待检验的字符数 |
| ptr    | -    | 指向 `char*` 类型对象的指针，`strtok_s` 以之存储其内部状态   |

**返回值**

1） 返回指向下一记号的首个字符的指针，或者在未找到记号时返回空指针。

2） 返回指向下一记号的首个字符的指针，或者在未找到记号或违反运行时约束时返回空指针。

**注解**

​	此函数是破坏性的：它写入 `'\0'` 字符到字符串 `str` 的元素。特别是，不能以字符串字面量为 `strtok` 的首参数。

​	每次对 `strtok` 的调用都会修改静态对象：它不是线程安全的。

​	与大多数其他记号化器不同，`strtok` 中的分隔符能对于后继记号不同，而且甚至能依赖于先前记号的内容。

​	`strtok_s` 函数异于 POSIX [`strtok_r`](https://pubs.opengroup.org/onlinepubs/9799919799/functions/strtok.html) 函数，前者通过在被记号化的字符串外部存储，和检查运行时制约来防护。微软 CRT 的 [`strtok_s`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l) 签名与这个 POSIX `strtok_r` 的定义相匹配，而不是 C11 的 `strtok_s`。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    char input[] = "A bird came down the walk";
    printf("Parsing the input string '%s'\n", input);
    char* token = strtok(input, " ");
    while (token)
    {
        puts(token);
        token = strtok(NULL, " ");
    }
 
    printf("Contents of the input string now: '");
    for (size_t n = 0; n < sizeof input; ++n)
        input[n] ? putchar(input[n]) : fputs("\\0", stdout);
    puts("'");
 
#ifdef __STDC_LIB_EXT1__
    char str[] = "A bird came down the walk";
    rsize_t strmax = sizeof str;
    const char* delim = " ";
    char* next_token;
    printf("解析输入字符串 '%s'\n", str);
    token = strtok_s(str, &strmax, delim, &next_token);
    while (token)
    {
        puts(token);
        token = strtok_s(NULL, &strmax, delim, &next_token);
    }
 
    printf("现在输入字符串的内容是：'");
    for (size_t n = 0; n < sizeof str; ++n)
        str[n] ? putchar(str[n]) : fputs("\\0", stdout);
    puts("'");
#endif
}
```

​	可能的输出：

```txt
解析输入字符串 'A bird came down the walk'
A
bird
came
down
the
walk
现在输入字符串的内容是：'A\0bird\0came\0down\0the\0walk\0'
解析输入字符串 'A bird came down the walk'
A
bird
came
down
the
walk
现在输入字符串的内容是：'A\0bird\0came\0down\0the\0walk\0'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.8 The strtok function （第 TBD 页）

  - K.3.7.3.1 The strtok_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.8 The strtok function （第 TBD 页）

  - K.3.7.3.1 The strtok_s function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.8 The strtok function （第 369-370 页）

  - K.3.7.3.1 The strtok_s function （第 620-621 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.8 The strtok function （第 332-333 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.8 The strtok function

**参阅**

| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数)   |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [strcspn<br />](https://zh.cppreference.com/w/c/string/byte/strcspn) | 返回另一个字符串所不具有的字符分割的最大起始段长度 (函数) |
| [strspn<br />](https://zh.cppreference.com/w/c/string/byte/strspn) | 返回由另一个字符串中的字符分割的最大起始段长度 (函数)     |
| [wcstok (C95)<br />wcstok_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstok) | 查找宽字符串中的下一个记号 (函数)                         |
| **strtok** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtok)** |                                                           |





### strtok_s

原址：[https://zh.cppreference.com/w/c/string/byte/strtok](https://zh.cppreference.com/w/c/string/byte/strtok)

作用：查找字节字符串中的下一个记号  (函数)

备注：仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 <string.h> 的所有包含之前定义了 
```c
// 在标头 <string.h> 定义
// (1)
char* strtok( char* str, const char* delim );// (C99 前)
char* strtok( char* restrict str, const char* restrict delim );// (C99 起)
char* strtok_s( char* restrict str, rsize_t* restrict strmax,
                const char* restrict delim, char** restrict ptr );// (2)(C11 起)
```

​	记号化空终止字节字符串。

1） 对 `strtok` 进行一系列调用，将 `str` 指向的字符串拆分为记号序列，记号之间以 `delim` 中的某个字符分隔。调用序列中的每次调用都有一个*搜索目标* ﻿：

- 如果 `str` 非空，那么该调用是序列中的*首次调用*。搜索目标是 `str` 指向的空终止字节字符串。
- 如果 `str` 为空，那么该调用是序列中的*后续调用*。搜索目标由系列中的上一次调用确定。

 序列中的每次调用都会在搜索目标中搜索第一个**不**在 `delim` 指向的*分隔字符串* ﻿中出现的字符，每次调用中分隔字符串可以不一致。

- 如果没有找到这种字符，那么搜索目标中没有任何记号。序列中的下次调用的搜索目标保持不变。[[1\]](https://zh.cppreference.com/w/c/string/byte/strtok#cite_note-1)

- 如果找到了这种字符，那么它就是当前记号的起始。然后

   

  ```
  strtok
  ```

   

  会从此处开始搜索第一个在分隔字符串中出现的字符。

  - 如果没有找到这种字符，那么当前记号会持续到搜索目标的末尾。序列中的下次调用的搜索目标是空字符串。[[2\]](https://zh.cppreference.com/w/c/string/byte/strtok#cite_note-2)
  - 如果找到了这种字符，那么会用空字符覆盖它，并结束当前记号。序列中的下次调用的搜索目标从下一字符开始。

 如果 `str` 或 `delim` 不是指向空终止字节字符串的指针，那么行为未定义。

2） 同 (1)，但有以下不同：

- 每次调用都会将 `str` 中留待查看的字符数写入 `*strmax`，并将记号化器的内部状态写入 `*ptr`。

- 序列中的每次后续调用都必须传递先前的调用用以存储值的 `strmax` 和 `ptr`。

- 在运行时检测下列错误并调用当前安装的

  制约处理

  函数，而不存储任何内容到

   

  `ptr`

   

  所指向的对象：

  - `strmax`，`delim` 或 `ptr` 是空指针。
  - 对于序列中的后续调用，`*ptr` 是空指针。
  - `*strmax` 大于 RSIZE_MAX。
  - 找到的记号的末尾没有在搜索目标的开头 `*strmax` 个字符中出现。

 如果 `str` 指向的字符数组缺少空终止符，而 `strmax` 指向的值大于该字符数组长度，那么行为未定义。

 同所有边界检查函数，`strtok_s`，仅若实现定义 `__STDC_LIB_EXT1__` 且用户在包含 [`<string.h>`](https://zh.cppreference.com/w/c/header/string) 前定义 `__STDC_WANT_LIB_EXT1__` 为整数常量 1 才保证可用。

1. [↑](https://zh.cppreference.com/w/c/string/byte/strtok#cite_ref-1) 后续调用使用其他分隔字符串仍然有可能组成记号。
2. [↑](https://zh.cppreference.com/w/c/string/byte/strtok#cite_ref-2) 后续调用中无法再组成记号。

**参数**

| str    | -    | 指向要记号化的空终止字节字符串的指针                         |
| ------ | ---- | ------------------------------------------------------------ |
| delim  | -    | 指向标识分隔符的空终止字节字符串的指针                       |
| strmax | -    | 指向最初保有 `str` 长度的对象指针：`strtok_s` 存储留待检验的字符数 |
| ptr    | -    | 指向 `char*` 类型对象的指针，`strtok_s` 以之存储其内部状态   |

**返回值**

1） 返回指向下一记号的首个字符的指针，或者在未找到记号时返回空指针。

2） 返回指向下一记号的首个字符的指针，或者在未找到记号或违反运行时约束时返回空指针。

**注解**

​	此函数是破坏性的：它写入 `'\0'` 字符到字符串 `str` 的元素。特别是，不能以字符串字面量为 `strtok` 的首参数。

​	每次对 `strtok` 的调用都会修改静态对象：它不是线程安全的。

​	与大多数其他记号化器不同，`strtok` 中的分隔符能对于后继记号不同，而且甚至能依赖于先前记号的内容。

​	`strtok_s` 函数异于 POSIX [`strtok_r`](https://pubs.opengroup.org/onlinepubs/9799919799/functions/strtok.html) 函数，前者通过在被记号化的字符串外部存储，和检查运行时制约来防护。微软 CRT 的 [`strtok_s`](https://learn.microsoft.com/en-us/cpp/c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l) 签名与这个 POSIX `strtok_r` 的定义相匹配，而不是 C11 的 `strtok_s`。

**示例**

```c
#define __STDC_WANT_LIB_EXT1__ 1
#include <stdio.h>
#include <string.h>
 
int main(void)
{
    char input[] = "A bird came down the walk";
    printf("Parsing the input string '%s'\n", input);
    char* token = strtok(input, " ");
    while (token)
    {
        puts(token);
        token = strtok(NULL, " ");
    }
 
    printf("Contents of the input string now: '");
    for (size_t n = 0; n < sizeof input; ++n)
        input[n] ? putchar(input[n]) : fputs("\\0", stdout);
    puts("'");
 
#ifdef __STDC_LIB_EXT1__
    char str[] = "A bird came down the walk";
    rsize_t strmax = sizeof str;
    const char* delim = " ";
    char* next_token;
    printf("解析输入字符串 '%s'\n", str);
    token = strtok_s(str, &strmax, delim, &next_token);
    while (token)
    {
        puts(token);
        token = strtok_s(NULL, &strmax, delim, &next_token);
    }
 
    printf("现在输入字符串的内容是：'");
    for (size_t n = 0; n < sizeof str; ++n)
        str[n] ? putchar(str[n]) : fputs("\\0", stdout);
    puts("'");
#endif
}
```

​	可能的输出：

```txt
解析输入字符串 'A bird came down the walk'
A
bird
came
down
the
walk
现在输入字符串的内容是：'A\0bird\0came\0down\0the\0walk\0'
解析输入字符串 'A bird came down the walk'
A
bird
came
down
the
walk
现在输入字符串的内容是：'A\0bird\0came\0down\0the\0walk\0'
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.24.5.8 The strtok function （第 TBD 页）

  - K.3.7.3.1 The strtok_s function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.24.5.8 The strtok function （第 TBD 页）

  - K.3.7.3.1 The strtok_s function （第 TBD 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.5.8 The strtok function （第 369-370 页）

  - K.3.7.3.1 The strtok_s function （第 620-621 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.5.8 The strtok function （第 332-333 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.5.8 The strtok function

**参阅**

| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数)   |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [strcspn<br />](https://zh.cppreference.com/w/c/string/byte/strcspn) | 返回另一个字符串所不具有的字符分割的最大起始段长度 (函数) |
| [strspn<br />](https://zh.cppreference.com/w/c/string/byte/strspn) | 返回由另一个字符串中的字符分割的最大起始段长度 (函数)     |
| [wcstok (C95)<br />wcstok_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstok) | 查找宽字符串中的下一个记号 (函数)                         |
| **strtok** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strtok)** |                                                           |
`__STDC_WANT_LIB_EXT1__`：






### strxfrm

原址：[https://zh.cppreference.com/w/c/string/byte/strxfrm](https://zh.cppreference.com/w/c/string/byte/strxfrm)

作用：变换字符串，使得 strcmp 会产生同 strcoll 的结果  (函数)

备注：
```c
// 在标头 <string.h> 定义
size_t strxfrm( char          *dest, const char          *src, size_t count );// (C99 前)
size_t strxfrm( char *restrict dest, const char *restrict src, size_t count );// (C99 起)
```

​	变换 `src` 所指向的空终止字节字符串为实现定义形式，满足当前 C 本地环境中，以 [strcmp](https://zh.cppreference.com/w/c/string/byte/strcmp) 比较二个变换后字符串给出与用 [strcoll](https://zh.cppreference.com/w/c/string/byte/strcoll) 比较源字符串相同的结果。

​	将变换后字符串的首 `count` 个字符写入目标，包含空终止字符，并返回排除空终止字符的完整转换后字符串的长度。

​	若 `dest` 数组不够大则行为未定义。若 `dest` 与 `src` 重叠则行为未定义。

​	若 `count` 为 `0`，则允许 `dest` 为空指针。

**注意**

​	能接收整个变换后字符串的正确缓冲区长度为 `1+strxfrm([NULL](http://zh.cppreference.com/w/c/types/NULL), src, 0)`。

​	在以同一字符串或字符串集合进行多个本地环境依赖的比较时，使用此函数，因为仅用 `strxfrm` 变换所有字符串一次，而以 [strcmp](https://zh.cppreference.com/w/c/string/byte/strcmp) 进行后继比较更为高效。

**参数**

| dest  | -    | 指向将写入变换后的字符串的数组首元素的指针 |
| ----- | ---- | ------------------------------------------ |
| src   | -    | 指向要变换的空终止字节字符串首元素的指针   |
| count | -    | 要写入的最大字符数                         |

**返回值**

​	变换后的字符串长度，不包含空终止字符。

**示例**

```c
#include <stdio.h>
#include <string.h>
#include <locale.h>
 
int main(void)
{
    setlocale(LC_COLLATE, "cs_CZ.iso88592");
 
    const char *in1 = "hrnec";
    char out1[1+strxfrm(NULL, in1, 0)];
    strxfrm(out1, in1, sizeof out1);
 
    const char *in2 = "chrt";
    char out2[1+strxfrm(NULL, in2, 0)];
    strxfrm(out2, in2, sizeof out2);
 
    printf("In the Czech locale: ");
    if(strcmp(out1, out2) < 0)
         printf("%s before %s\n",in1, in2);
    else
         printf("%s before %s\n",in2, in1);
 
    printf("In lexicographical comparison: ");
    if(strcmp(in1, in2)<0)
         printf("%s before %s\n",in1, in2);
    else
         printf("%s before %s\n",in2, in1);
 
}
```

​	输出：

```txt
In the Czech locale: hrnec before chrt
In lexicographical comparison: chrt before hrnec
```

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.24.4.5 The strxfrm function （第 366-367 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.21.4.5 The strxfrm function （第 329-330 页）

- C89/C90 标准（ISO/IEC 9899:1990）：

  - 4.11.4.5 The strxfrm function

**参阅**

| [strcoll<br />](https://zh.cppreference.com/w/c/string/byte/strcoll) | 比较两个字符串，根据当前本地环境 (函数)                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcscoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscoll) | 根据当前本地环境比较两个宽字符串 (函数)                      |
| [strcmp<br />](https://zh.cppreference.com/w/c/string/byte/strcmp) | 比较两个字符串 (函数)                                        |
| [wcsxfrm (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsxfrm) | 变换宽字符串，使得 [wcscmp](https://zh.cppreference.com/w/c/string/wide/wcscmp) 会产生与 [wcscoll](https://zh.cppreference.com/w/c/string/wide/wcscoll) 相同的结果 (函数) |
| **strxfrm** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/byte/strxfrm)** |                                                              |






