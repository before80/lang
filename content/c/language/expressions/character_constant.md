+++
title = "字符常量"
date = 2025-04-12T20:13:22+08:00
weight = 90
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/language/character_constant](https://zh.cppreference.com/w/c/language/character_constant)

## 语法

| `'`*c-字符* `'`      | (1)  |                    |
| -------------------- | ---- | ------------------ |
| `u8'`*c-字符* `'`    | (2)  | (C23 起)           |
| `u'`*c-字符* `'`     | (3)  | (C11 起)           |
| `U'`*c-字符* `'`     | (4)  | (C11 起)           |
| `L'`*c-字符* `'`     | (5)  |                    |
| `'`*c-字符序列* `'`  | (6)  |                    |
| `L'`*c-字符序列* `'` | (7)  |                    |
| `u'`*c-字符序列* `'` | (8)  | (C11 起)(C23 移除) |
| `U'`*c-字符序列* `'` | (9)  | (C11 起)(C23 移除) |

​	其中

- *c-char* 是以下之一：
  - 来自基本源字符集减去单引号（`'`）、反斜杠（`\`）或换行符的字符。
  - 转义序列：特殊字符转义 `\'` `\"` `\?` `\\` `\a` `\b` `\f` `\n` `\r` `\t` `\v`，十六进制转义 `\x...`，或八进制转义 `\...` 之一，如[转义序列](https://zh.cppreference.com/w/c/language/escape)中所定义。
  - 通用字符名，\u... 或 \U...，如[转义序列](https://zh.cppreference.com/w/c/language/escape)中所定义。(C99 起)

- *c-字符序列* 为二个或更多 *c-字符* 的序列：
  1. 单字节整数字符常量，例如 `'a'` 或 `'\n'` 或 `'\13'`。这种常量的类型为 `int`，其值等于该 *c-字符* 在执行字符集中作为映射到 `int` 的 `char` 类型的值。若该 *c-字符* 不能表示成执行字符集中的单字节，则值是实现定义的。
  2. UTF-8 字符常量，例如 `u8'a'`。这种常量的类型为 `char8_t`，其值等于该 *c-字符* 的 ISO 10646 码位的值，只要该码位值能以单个 UTF-8 编码单元表示（即该 *c-字符* 处于含上下界的范围 0x0-0x7F 内）。若该 *c-字符* 不可表示为单个 UTF-8 编码单元，则程序为非良构。
  3. 16 位宽字符常量，例如 `u'猫'` 但非 `u'🍌'`（`u'\U0001f34c'`）。这种常量的类型为 `char16_t`，其值等于该 *c-字符* 在 [mbrtoc16](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc16) 所产生的 16 位编码（通常为 UTF-16）中的值。若该 *c-字符* 不能表示为一个 16 位字符或映射到多于一个 16 位字符，则值是实现定义的。(C23 前)
  4. 32 位宽字符常量，例如 `U'猫'` 或 `U'🍌'`。这种常量的类型为 `char32_t`，其值等于该 *c-字符* 在 [mbrtoc32](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc32) 所产生的 32 位编码（通常为 UTF-32）中的值。若该 *c-字符* 不能表示为一个 32 位字符，或映射到多于一个 32 位字符，则值是实现定义的。(C23 前)
  5. UTF-16 字符常量，例如 `u'猫'` 但非 `u'🍌'`（`u'\U0001f34c'`）。这种常量的类型为 `char16_t`，其值等于该 *c-字符* 的 ISO 10646 码位的值，只要该码位值能以单个 UTF-16 编码单元表示（即该 *c-字符* 处于含上下界的范围 0x0-0xD7FF 或 0xE000-0xFFFF 内）。若该 *c-字符* 不可表示为单个 UTF-16 编码单元，则程序为非良构。(C23 起)
  6. UTF-32 字符常量，例如 `U'猫'` 或 `U'🍌'`。这种常量的类型为 `char32_t`，其值等于该 *c-字符* 的 ISO 10646 码位的值，只要该码位值能以单个 UTF-32 编码单元表示（即该 *c-字符* 处于含上下界的范围 0x0-0xD7FF 或 0xE000-0x10FFFF 内）。若该 *c-字符* 不可表示为单个 UTF-32 编码单元，则程序为非良构。(C23 起)
  7. 宽字符常量，例如 `L'β'` 或 `L'字'`。这种常量的类型为 `wchar_t`，其值等于该 *c-字符* 在执行宽字符集中的值（即 [mbtowc](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) 会产生的值）。若该 *c-字符* 不能表示为一个宽字符，或映射到多于一个宽字符（例如 Windows 上的非 BMP 值，其中 `wchar_t` 为 16 位），则值是实现定义的。
  8. 多字符常量，例如 `'AB'`，拥有 `int` 类型和实现定义的值。
  9. 宽多字符常量，例如 `L'AB'`，拥有 `wchar_t` 类型和实现定义的值。
  10. 16 位多字符常量，例如 `u'CD'`，拥有 `char16_t` 类型和实现定义的值。
  11. 32 位多字符常量，例如 `U'XY'`，拥有 `char32_t` 类型和实现定义的值。

## 注解

​	多字符常量是 C 从 B 编程语言继承而来的。尽管 C 标准不指定，大多数编译器（值得注意的例外是 MSVC ）也如 B 中所指定实现多字符常量：常量中的每个字符的值以大端序零填充右对齐顺序初始化结果整数的相继字节，例如 '\1' 的值为 0x00000001 而 `'\1\2\3\4'` 的值为 `0x01020304` 。

​	C++ 中，可编码的普通字符字面量的类型为 char 而非 int。

​	不同于[整数常量]({{< ref "/c/language/expressions/integer_constant" >}})，若 `char` 有符号，则字符常量可以有负值：这种实现中 `'\xFF'` 是值为 `-1` 的 int。

​	当用在 [`#if`]({{< ref "/c/language/preprocessor/conditional" >}}) 或 [`#elif`]({{< ref "/c/language/preprocessor/conditional" >}}) 的控制表达式中时，可能按照源字符集、执行字符集或其他实现定义的字符集转译字符常量。

​	16/32 位多字符常量未得到广泛支持并于 C23 中被移除。一些常见实现（如 clang）完全不接受它们。

## 示例

```c
#include <stddef.h>
#include <stdio.h>
#include <uchar.h>
 
int main (void)
{
    printf("constant    value     \n");
    printf("--------    ----------\n");
 
    // 整数字符常量
    int c1='a'; printf("'a':\t %#010x\n", c1);
    int c2='🍌'; printf("'🍌':\t %#010x\n\n", c2); // 实现定义
 
    // 多字符常量
    int c3='ab'; printf("'ab':\t %#010x\n\n", c3); // 实现定义
 
    // 16 位宽字符常量
    char16_t uc1 = u'a'; printf("'a':\t %#010x\n", (int)uc1);
    char16_t uc2 = u'¢'; printf("'¢':\t %#010x\n", (int)uc2);
    char16_t uc3 = u'猫'; printf("'猫':\t %#010x\n", (int)uc3);
    // 实现定义（🍌 映射到二个 16 位宽字符）
    char16_t uc4 = u'🍌'; printf("'🍌':\t %#010x\n\n", (int)uc4);
 
    // 32 位宽字符常量
    char32_t Uc1 = U'a'; printf("'a':\t %#010x\n", (int)Uc1);
    char32_t Uc2 = U'¢'; printf("'¢':\t %#010x\n", (int)Uc2);
    char32_t Uc3 = U'猫'; printf("'猫':\t %#010x\n", (int)Uc3);
    char32_t Uc4 = U'🍌'; printf("'🍌':\t %#010x\n\n", (int)Uc4);
 
    // 宽字符常量
    wchar_t wc1 = L'a'; printf("'a':\t %#010x\n", (int)wc1);
    wchar_t wc2 = L'¢'; printf("'¢':\t %#010x\n", (int)wc2);
    wchar_t wc3 = L'猫'; printf("'猫':\t %#010x\n", (int)wc3);
    wchar_t wc4 = L'🍌'; printf("'🍌':\t %#010x\n\n", (int)wc4);
}
```

​	可能的输出：

```txt
constant    value     
--------    ----------
'a':	 0x00000061
'🍌':	 0xf09f8d8c
 
'ab':	 0x00006162
 
'a':	 0x00000061
'¢':	 0x000000a2
'猫':	 0x0000732b
'🍌':	 0x0000df4c
 
'a':	 0x00000061
'¢':	 0x000000a2
'猫':	 0x0000732b
'🍌':	 0x0001f34c
 
'a':	 0x00000061
'¢':	 0x000000a2
'猫':	 0x0000732b
'🍌':	 0x0001f34c
```

## 参阅

**字符字面量**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/language/character_literal)**
