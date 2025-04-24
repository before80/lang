
+++
title = "<stdmchar.h> (C29)"
date = 2025-04-24T18:56:49+08:00
weight = 230
type = "docs"
description = "文本转码"
isCJKLanguage = true
draft = false

+++

## 类型



### char16_t

原址：

作用：

备注：





### char32_t

原址：

作用：

备注：





### char8_t

原址：

作用：

备注：





### mbstate_t

原址：[http://zh.cppreference.com/w/c/string/multibyte/mbstate_t](http://zh.cppreference.com/w/c/string/multibyte/mbstate_t)

作用：

备注：
```c
// 在标头 <uchar.h> 定义
// 在标头 <wchar.h> 定义
struct mbstate_t;// (C95 起)
```

​	类型 `mbstate_t` 是平凡非数组类型，可以表示能在实现定义的受支持多字节编码规则集合中出现的任何转换状态。 `mbstate_t` 的零初始化值表示初始转换状态，尽管亦可能存在 `mbstate_t` 的其他值也表示初始转换状态。

​	`mbstate_t` 的可行实现是一个结构体类型，保有表示不完整多字节字符的数组，指示数组中已处理字节数的整数，和当前迁移状态的一项表示。

​	由于可能的数据竞争，不应不带同步地从多个线程以空指针为 `mbstate_t*` 实参调用下列函数：[mbrlen](https://zh.cppreference.com/w/c/string/multibyte/mbrlen)、[mbrtowc](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc)、[mbsrtowcs](https://zh.cppreference.com/w/c/string/multibyte/mbsrtowcs)、[mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc)、[wcrtomb](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb)、[wcsrtombs](https://zh.cppreference.com/w/c/string/multibyte/wcsrtombs)、[wctomb](https://zh.cppreference.com/w/c/string/multibyte/wctomb)。

**引用**

- C11 标准（ISO/IEC 9899:2011）：

  - 7.29.1/2 Introduction （第 402 页）

- C99 标准（ISO/IEC 9899:1999）：

  - 7.24.1/2 Introduction （第 348 页）

**参阅**

| [mbsinit (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbsinit) | 检查 mbstate_t 对象是否表示初始迁移状态 (函数) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| **mbstate_t** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte/mbstate_t)** |                                                |





### size_t

原址：[http://zh.cppreference.com/w/c/types/size_t](http://zh.cppreference.com/w/c/types/size_t)

作用：

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





### stdc_mcerr

原址：

作用：

备注：





### wchar_t

原址：

作用：

备注：






## 枚举




## 宏



### MB_UTF16

原址：

作用：

备注：





### MB_UTF32

原址：

作用：

备注：





### MB_UTF8

原址：

作用：

备注：





### STDC_C16_MAX

原址：

作用：

备注：





### STDC_C32_MAX

原址：

作用：

备注：





### STDC_C8_MAX

原址：

作用：

备注：





### STDC_MC_MAX

原址：

作用：

备注：





### STDC_MWC_MAX

原址：

作用：

备注：





### WCHAR_MAX

原址：

作用：

备注：





### WCHAR_MIN

原址：

作用：

备注：





### WCHAR_UTF16

原址：

作用：

备注：





### WCHAR_UTF32

原址：

作用：

备注：





### WCHAR_UTF8

原址：

作用：

备注：





### WCHAR_WIDTH

原址：

作用：

备注：





### __STDC_VERSION_STDMCHAR_H__

原址：

作用：

备注：






## 函数



### stdc_c16nrtoc16n

原址：

作用：

备注：





### stdc_c16nrtoc32n

原址：

作用：

备注：





### stdc_c16nrtoc8n

原址：

作用：

备注：





### stdc_c16nrtomcn

原址：

作用：

备注：





### stdc_c16nrtomwcn

原址：

作用：

备注：





### stdc_c16snrtoc16sn

原址：

作用：

备注：





### stdc_c16snrtoc32sn

原址：

作用：

备注：





### stdc_c16snrtoc8sn

原址：

作用：

备注：





### stdc_c16snrtomcsn

原址：

作用：

备注：





### stdc_c16snrtomwcsn

原址：

作用：

备注：





### stdc_c32nrtoc16n

原址：

作用：

备注：





### stdc_c32nrtoc32n

原址：

作用：

备注：





### stdc_c32nrtoc8n

原址：

作用：

备注：





### stdc_c32nrtomcn

原址：

作用：

备注：





### stdc_c32nrtomwcn

原址：

作用：

备注：





### stdc_c32snrtoc16sn

原址：

作用：

备注：





### stdc_c32snrtoc32sn

原址：

作用：

备注：





### stdc_c32snrtoc8sn

原址：

作用：

备注：





### stdc_c32snrtomcsn

原址：

作用：

备注：





### stdc_c32snrtomwcsn

原址：

作用：

备注：





### stdc_c8nrtoc16n

原址：

作用：

备注：





### stdc_c8nrtoc32n

原址：

作用：

备注：





### stdc_c8nrtoc8n

原址：

作用：

备注：





### stdc_c8nrtomcn

原址：

作用：

备注：





### stdc_c8nrtomwcn

原址：

作用：

备注：





### stdc_c8snrtoc16sn

原址：

作用：

备注：





### stdc_c8snrtoc32sn

原址：

作用：

备注：





### stdc_c8snrtoc8sn

原址：

作用：

备注：





### stdc_c8snrtomcsn

原址：

作用：

备注：





### stdc_c8snrtomwcsn

原址：

作用：

备注：





### stdc_mcnrtoc16n

原址：

作用：

备注：





### stdc_mcnrtoc32n

原址：

作用：

备注：





### stdc_mcnrtoc8n

原址：

作用：

备注：





### stdc_mcnrtomcn

原址：

作用：

备注：





### stdc_mcnrtomwcn

原址：

作用：

备注：





### stdc_mcsnrtoc16sn

原址：

作用：

备注：





### stdc_mcsnrtoc32sn

原址：

作用：

备注：





### stdc_mcsnrtoc8sn

原址：

作用：

备注：





### stdc_mcsnrtomcsn

原址：

作用：

备注：





### stdc_mcsnrtomwcsn

原址：

作用：

备注：





### stdc_mwcnrtoc16n

原址：

作用：

备注：





### stdc_mwcnrtoc32n

原址：

作用：

备注：





### stdc_mwcnrtoc8n

原址：

作用：

备注：





### stdc_mwcnrtomcn

原址：

作用：

备注：





### stdc_mwcnrtomwcn

原址：

作用：

备注：





### stdc_mwcsnrtoc16sn

原址：

作用：

备注：





### stdc_mwcsnrtoc32sn

原址：

作用：

备注：





### stdc_mwcsnrtoc8sn

原址：

作用：

备注：





### stdc_mwcsnrtomcsn

原址：

作用：

备注：





### stdc_mwcsnrtomwcsn

原址：

作用：

备注：






