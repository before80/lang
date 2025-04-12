+++
title = "字符串字面量"
date = 2025-04-12T20:28:00+08:00
weight = 120
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/string_literal](https://zh.cppreference.com/w/c/language/string_literal)

​	原位构造指定字符数组类型的无名对象，在需要内嵌字符串到源代码中时使用。

## 语法

| `"` *串字符序列* `"`   | (1)  |          |
| ---------------------- | ---- | -------- |
| `u8"` *串字符序列* `"` | (2)  | (C11 起) |
| `u"` *串字符序列* `"`  | (3)  | (C11 起) |
| `U"` *串字符序列* `"`  | (4)  | (C11 起) |
| `L"` *串字符序列* `"`  | (5)  |          |

​	其中

| *串字符序列* | -    | 零或多个字符，每个或为来自源字符集的多字节字符（不含 `"`、`\` 及换行符），或为[转义序列](https://zh.cppreference.com/w/c/language/escape)中定义的字符转义、十六进制转义、八进制转义或通用字符名 (C99 起)。 |
| ------------ | ---- | ------------------------------------------------------------ |

1) *字符串字面量*：字面量的类型为 `char[N]`，其中 `N` 是以执行窄编码的编码单元数计的字符串的大小，包括空终止符。以执行字符集从 *串字符序列* 中的下个字符初始化数组的每个 char 元素。
2) *UTF-8 字符串字面量*：字面量的类型为 `char[N]`(C23 前)`char8_t[N](C23 起)`，其中 `N` 是以 UTF-8 编码单元数计的字符串大小，包括空终止符。以 UTF-8 编码从 *串字符序列* 中的下个多字节字符初始化数组中的每个 `char`(C23 前)`char8_t`(C23 起) 元素。
3) 16 位宽字符串字面量：字面量的类型为 `char16_t[N]`，其中 `N` 是以实现定义的 16 位编码（通常为 UTF-16）的编码单元数计的字符串大小，包括空终止符。如同通过在实现定义的本地环境中执行 [mbrtoc16](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc16) 初始化数组的每个 char16_t 元素。(C23 前)
4) 32 位宽字符串字面量：字面量的类型为 `char32_t[N]`，其中 `N` 是以实现定义的 32 位编码（通常为 UTF-32）的编码单元数计的字符串大小，包括空终止符。如同通过在实现定义的本地环境中执行 [mbrtoc32](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc32) 初始化数组的每个 char32_t 元素。(C23 前)
5) *UTF-16 字符串字面量*：字面量的类型为 `char16_t[N]`，其中 `N` 是以 UTF-16 编码单元数计的字符串大小，包括空终止符。以 UTF-16 编码从 *串字符序列* 中的下个多字节字符初始化数组中的每个 `char` 元素。(C23 起)
6) *UTF-32 字符串字面量*：字面量的类型为 `char32_t[N]`，其中 `N` 是以 UTF-32 编码单元数计的字符串大小，包括空终止符。以 UTF-32 编码从 *串字符序列* 中的下个多字节字符初始化数组中的每个 `char` 元素。(C23 起)
7) 宽字符串字面量：字面量的类型为 `wchar_t[N]`，其中 `N` 是以执行宽编码的编码单元数计的字符串大小，包括空终止符。如同通过在实现定义的本地环境中执行 [mbstowcs](https://zh.cppreference.com/w/c/string/multibyte/mbstowcs) 初始化数组的每个 `wchar_t` 元素。

## 解释

​	首先，在[翻译阶段 6](https://zh.cppreference.com/w/c/language/translation_phases)（宏展开后），连接相邻的字符串字面量（即仅为空白符所分隔的字符串字面量）。

​	仅可连接二个窄或二个宽字符串字面量。(C99 前)

​	若一个字面量无前缀，则结果字符串字面量拥有有前缀字面量所指定的宽度/编码。(C99 起)

```c
L"Δx = %" PRId16 // 在阶段 4，PRId16 展开成 "d"
                 // 在阶段 6，L"Δx = %" 和 "d" 组成 L"Δx = %d"
```

​	若两个字符串字面量拥有不同的编码前缀，则连接是实现定义的，但不能连接 UTF-8 字符串字面量和宽字符串字面量。(C11 起) (C23 前)

​	若两个字符串字面量拥有不同的编码前缀，则连接为非良构。(C23 起)

​	其次，在[翻译阶段 7](https://zh.cppreference.com/w/c/language/translation_phases)，添加空终止字符到每个字符串字面量，然后每个字符串字面量初始化一个拥有静态[存储期](https://zh.cppreference.com/w/c/language/storage_duration)，长度刚好能容纳字符串字面量的内容加一个空终止符的无名数组。

```c
char* p = "\x12" "3"; // 创建 static char[3] 数组，保有 {'\x12', '3', '\0'} 
                      // 设置 p 指向数组的首元素
```

​	字符串字面量不可修改（而且实际上可以放在例如 `.rodata` 的只读内存中）。若程序试图修改字符串字面量组成的静态数组，则行为未定义。

```c
char* p = "Hello";
p[1] = 'M'; // 未定义行为
char a[] = "Hello";
a[1] = 'M'; // OK：a 不是字符串字面量
```

​	既不要求亦不禁止等同的字符串字面量指代内存中的同一位置。而且，重叠的字符串字面量或作为其他字符串字面量子串的字符串字面量可以结合。

```c
"def" == 3+"abcdef"; // 可为 1 或 0，实现定义
```

## 注解

​	字符串字面量不必是一条字符串；若字符串字面量拥有内嵌的空字符，则它表示含有多于一条字符串的数组：

```c
char* p = "abc\0def"; // strlen(p) == 3，但数组大小为 8
```

​	若在字符串字面量中有合法十六进制数字跟在十六进制转义之后，则这会作为非法的转义序列导致编译失败，但可以用字符串连接作为一种变通方式：

```c
//char* p = "\xfff"; // 错误：十六进制转义序列超出范围
char* p = "\xff""f"; // OK：字面量为 char[3]，保有 {'\xff', 'f', '\0'}
```

​	字符串字面量可用于[初始化数组](https://zh.cppreference.com/w/c/language/array_initialization)，而若数组大小比字符串字面量大小少一，则忽略空终止符：

```c
char a1[] = "abc"; // a1 为 char[4] ，保有 {'a', 'b', 'c', '\0'}
char a2[4] = "abc"; // a2 为 char[4] ，保有 {'a', 'b', 'c', '\0'}
char a3[3] = "abc"; // a3 为 char[3] ，保有 {'a', 'b', 'c'}
```

​	字符串字面量 (1) 和宽字符串字面量 (5) 的编码是实现定义的。例如，gcc 用[命令行选项](https://gcc.gnu.org/onlinedocs/cpp/Invocation.html) -fexec-charset 和 -fwide-exec-charset 选择它们。

​	尽管 C11 中允许混合的宽字符串字面量连接，几乎所有编译器都拒绝这种连接（仅有的已知例外是 [SDCC](http://sdcc.sourceforge.net/)），而其使用经验是未知的。结果是，C23 中移除了对混合宽字符串字面量连接的许可。

## 示例

```c
#include <inttypes.h>
#include <locale.h>
#include <stddef.h>
#include <stdio.h>
#include <stdlib.h>
#include <uchar.h>
 
int main(void)
{
    char s1[] = "a猫🍌"; // 或 "a\u732B\U0001F34C"
#if __STDC_VERSION__ >= 202311L
    char8_t
#else
    char
#endif
    s2[] = u8"a猫🍌";
    char16_t s3[] = u"a猫🍌";
    char32_t s4[] = U"a猫🍌";
    wchar_t s5[] = L"a猫🍌";
 
    setlocale(LC_ALL, "en_US.utf8");
    printf("  \"%s\" is a char[%zu] holding     { ", s1, sizeof s1 / sizeof *s1);
    for(size_t n = 0; n < sizeof s1 / sizeof *s1; ++n)
        printf("0x%02X ", +(unsigned char)s1[n]);
    puts("}");
    printf(
#if __STDC_VERSION__ >= 202311L
    "u8\"%s\" is a char8_t[%zu] holding  { "
#else
    "u8\"%s\" is a char[%zu] holding     { "
#endif
, s2, sizeof s2 / sizeof *s2);
    for(size_t n = 0; n < sizeof s2 / sizeof *s2; ++n)
#if __STDC_VERSION__ >= 202311L
       printf("0x%02X ", s2[n]);
#else
       printf("0x%02X ", +(unsigned char)s2[n]);
#endif
    puts("}");
    printf(" u\"a猫🍌\" is a char16_t[%zu] holding { ", sizeof s3 / sizeof *s3);
    for(size_t n = 0; n < sizeof s3 / sizeof *s3; ++n)
       printf("0x%04" PRIXLEAST16" ", s3[n]);
    puts("}");
    printf(" U\"a猫🍌\" is a char32_t[%zu] holding { ", sizeof s4 / sizeof *s4);
    for(size_t n = 0; n < sizeof s4 / sizeof *s4; ++n)
       printf("0x%08" PRIXLEAST32" ", s4[n]);
    puts("}");
    printf(" L\"%ls\" is a wchar_t[%zu] holding  { ", s5, sizeof s5 / sizeof *s5);
    for(size_t n = 0; n < sizeof s5 / sizeof *s5; ++n)
       printf("0x%08X ", (unsigned)s5[n]);
    puts("}");
}
```

​	可能的输出：

```txt
  "a猫🍌" is a char[9] holding     { 0x61 0xE7 0x8C 0xAB 0xF0 0x9F 0x8D 0x8C 0x00 }
u8"a猫🍌" is a char[9] holding     { 0x61 0xE7 0x8C 0xAB 0xF0 0x9F 0x8D 0x8C 0x00 }
 u"a猫🍌" is a char16_t[5] holding { 0x0061 0x732B 0xD83C 0xDF4C 0x0000 }
 U"a猫🍌" is a char32_t[4] holding { 0x00000061 0x0000732B 0x0001F34C 0x00000000 }
 L"a猫🍌" is a wchar_t[4] holding  { 0x00000061 0x0000732B 0x0001F34C 0x00000000 }
```

## 参阅

字符串字面量的 [C++ 文档](https://zh.cppreference.com/w/cpp/language/string_literal)