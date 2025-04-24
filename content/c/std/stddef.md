
+++
title = "<stddef.h>"
date = 2025-04-24T18:42:21+08:00
weight = 190
type = "docs"
description = "常用宏定义"
isCJKLanguage = true
draft = false

+++

## 类型



### max_align_t

原址：[https://zh.cppreference.com/w/c/types/max_align_t](https://zh.cppreference.com/w/c/types/max_align_t)

作用：对齐要求不小于任何其他标量类型的类型  (typedef)

备注：
```c
// 在标头 <stddef.h> 定义
typedef /* 由实现定义 */ max_align_t;// (C11 起)
```

​	`max_align_t` 是对齐要求至少和其他任何一种标量类型一样严格（一样大）的类型。

**注解**

​	如 [malloc](https://zh.cppreference.com/w/c/memory/malloc) 这样的分配函数所返回的指针是为任意对象对齐的，这表示它们至少和 `max_align_t` 一样严格。

**示例**

```c
#include <inttypes.h>
#include <stdalign.h>
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
#include <stdlib.h>
 
int main(void)
{
    size_t a = alignof(max_align_t);
    printf("max_align_t 的对齐是 %zu (%#zx)\n", a, a);
 
    void *p = malloc(123);
    printf("从 malloc(123) 获得的地址为 %#" PRIxPTR"\n",
            (uintptr_t)p);
    free(p);
}
```

​	可能的输出：

```txt
max_align_t 的对齐是 16 (0x10)
从 malloc(123) 获得的地址为 0x1fa67010
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.19 Common definitions <stddef.h> （第 211 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.19 Common definitions <stddef.h> （第 288 页）

**参阅**

**max_align_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/max_align_t)**





### nullptr_t

原址：[https://zh.cppreference.com/w/c/types/nullptr_t](https://zh.cppreference.com/w/c/types/nullptr_t)

作用：预定义空指针常量 nullptr 的类型   (typedef)

备注：
```c
// 在标头 <stddef.h> 定义
typedef typeof(nullptr) nullptr_t;// (C23 起)
```

​	`nullptr_t` 是预定义空指针常量 [`<ullpt>`](https://zh.cppreference.com/w/c/language/nullptr) 的类型。它是自身并非指针类型的单独类型。它能[隐式转换到](https://zh.cppreference.com/w/c/language/conversion)任何指针类型或 `bool`，而结果分别为该类型的空指针值或 `false`。除了 `nullptr_t` 自身，没有其他类型能转换或显式转型成 `nullptr_t`。

​	`sizeof(nullptr_t)` 与 `alignof(nullptr_t)` 分别等于 `sizeof(void*)` 与 `alignof(void*)`。

​	`nullptr_t` 仅有一个合法值，即 `nullptr`。`nullptr` 的对象表示与 `(void*)0` 的相同。若[左值转换](https://zh.cppreference.com/w/c/language/conversion#.E5.B7.A6.E5.80.BC.E8.BD.AC.E6.8D.A2)产生拥有不同对象表示的 `nullptr_t` 值，则行为未定义。

**示例**

​	演示 `nullptr_t` 为单独的类型。

```c
#include <stddef.h>
#include <stdio.h>
 
#define DETECT_NULL_POINTER_CONSTANT(e) \
    _Generic(e,                         \
        void* : puts("void*"),          \
        nullptr_t : puts("nullptr_t"),  \
        default : puts("other")         \
    )
 
int main()
{
    DETECT_NULL_POINTER_CONSTANT(((void*)0));
    DETECT_NULL_POINTER_CONSTANT(0);
    DETECT_NULL_POINTER_CONSTANT(nullptr);
}
```

​	输出：

```txt
void*
other
nullptr_t
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.21.2 The nullptr_t type （第 315-316 页）

**参阅**

| [NULL<br />](https://zh.cppreference.com/w/c/types/NULL)   | 实现定义的空指针常量 (宏常量) |
| ------------------------------------------------------------ | ----------------------------- |
| **nullptr_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/nullptr_t)** |                               |





### ptrdiff_t

原址：[https://zh.cppreference.com/w/c/types/ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)

作用：两个指针相减返回的有符号整数类型  (typedef)

备注：
```c
// 在标头 <stddef.h> 定义
typedef /* 由实现定义 */ ptrdiff_t;
```

​	`ptrdiff_t` 是[二个指针相减](https://zh.cppreference.com/w/c/language/operator_arithmetic#.E6.8C.87.E9.92.88.E7.AE.97.E6.9C.AF)结果所拥有的有符号整数类型。

​	`ptrdiff_t` 的位宽不小于 17。 (C99 起)(C23 前)

​	`ptrdiff_t` 的位宽不小于 16。 (C23 起)

**注解**

​	若可能出现负值，则使用 `ptrdiff_t` 进行指针算术和数组索引。使用其他类型（如 `int`）的程序，可能会在譬如在 64 位系统上，当下标超过 [INT_MAX](https://zh.cppreference.com/w/c/types/limits) 时，或若依赖 32 位模算术时失败。

​	只有指向同一数组中的元素（包括指向数组尾后一个位置）的指针可以相减。

​	若数组足够大（大于 [PTRDIFF_MAX](https://zh.cppreference.com/w/c/types/limits) 个元素，但等于或小于 [SIZE_MAX](https://zh.cppreference.com/w/c/types/limits) 个字节），则两个指针间的距离可能无法以 **ptrdiff_t** 表示，这两个指针相减的结果未定义。

​	对于短于 [PTRDIFF_MAX](https://zh.cppreference.com/w/c/types/limits) 的 char 数组，`ptrdiff_t` 表现为 [size_t](https://zh.cppreference.com/w/c/types/size_t) 的有符号对应类型：它能存储任何类型的数组大小，而且在大多数平台上是 `intptr_t` 的同义词。

**可能的实现**

```c
typedef typeof((int*)nullptr - (int*)nullptr) ptrdiff_t; // C23 起合法
```

**示例**

```c
#include <stddef.h>
#include <stdint.h>
#include <stdio.h>
 
int main(void)
{
    const size_t N = 100;
    int numbers[N];
 
    printf("PTRDIFF_MAX = %ld\n", PTRDIFF_MAX);
    int *p1 = &numbers[18], *p2 = &numbers[23];
    ptrdiff_t diff = p2 - p1;
    printf("p2-p1 = %td\n", diff);
}
```

​	可能的输出：

```txt
PTRDIFF_MAX = 9223372036854775807
p2-p1 = 5
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

| [size_t<br />](https://zh.cppreference.com/w/c/types/size_t) | [`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 运算符返回的无符号整数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [offsetof<br />](https://zh.cppreference.com/w/c/types/offsetof) | 从结构体类型的起始到指定成员的字节偏移 (宏函数)              |
| **ptrdiff_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/ptrdiff_t)** |                                                              |





### rsize_t

原址：

作用：

备注：仅当实现定义了 `__STDC_LIB_EXT1__` 而且用户代码在对 stddef.h 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：






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





### wchar_t

原址：

作用：

备注：






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





### __STDC_VERSION_STDDEF_H__

原址：

作用：

备注：





### offsetof

原址：[https://zh.cppreference.com/w/c/types/offsetof](https://zh.cppreference.com/w/c/types/offsetof)

作用：从结构体类型的起始到指定成员的字节偏移  (宏函数)

备注：
```c
// 在标头 <stddef.h> 定义
#define offsetof(type, member) /* 由实现定义 */
```

​	宏 **offsetof** 展开成 [size_t](https://zh.cppreference.com/w/c/types/size_t) 类型的[整数常量表达式](https://zh.cppreference.com/w/c/language/constant_expression#.E6.95.B4.E6.95.B0.E5.B8.B8.E9.87.8F.E8.A1.A8.E8.BE.BE.E5.BC.8F)，其值为从指定类型对象起始到其指定子对象的偏移，若填充存在则包含之。

​	给定拥有静态存储期的 `type` 类型对象 `o`，`&(o.member)` 应当为地址常量表达式并指向 `o` 的子对象。否则行为未定义。

​	若在 `type` 中指定的类型含有不在匹配的括号中的逗号，则行为未定义。 (C23 起)

**注解**

​	若将 `offsetof` 应用到位域成员，则行为未定义，因为不能取位域的地址。

​	不限制 `member` 为直接成员。它能指代给定成员的子对象，例如数组成员的元素。

​	尽管 C23 中指定在 `offsetof` 中指定含有不带括号的逗号的新类型为未定义行为，这种用法在较早模式的实现中通常不支持：`offsetof(struct Foo { int a, b; }, a)` 通常不能编译。

​	[`<ypeo>`](https://zh.cppreference.com/w/c/language/typeof) 能用于避免在新类型定义中的逗号的坏效果，例如 `offsetof(typeof(struct { int i, j; }), i)` 为良定义。 (C23 起)

**示例**

```c
#include <stdio.h>
#include <stddef.h>
 
struct S {
    char c;
    double d;
};
 
int main(void)
{
    printf("the first element is at offset %zu\n", offsetof(struct S, c));
    printf("the double is at offset %zu\n", offsetof(struct S, d));
}
```

​	可能的输出：

```txt
the first element is at offset 0
the double is at offset 8
```

**缺陷报告**

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为             | 正确行为                 |
| ------------------------------------------------------------ | ------ | ------------------------ | ------------------------ |
| [DR 496](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_496) | C89    | 仅提及结构体与结构体成员 | 亦支持联合体与其他子对象 |

**参阅**

| [size_t<br />](https://zh.cppreference.com/w/c/types/size_t) | [`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 运算符返回的无符号整数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **offsetof** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/types/offsetof)** |                                                              |





### unreachable

原址：

作用：

备注：






## 函数




