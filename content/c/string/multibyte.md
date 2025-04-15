+++
title = "空终止多字节字符串"
date = 2025-04-15T09:02:04+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/string/multibyte](https://zh.cppreference.com/w/c/string/multibyte)

​	空终止多字节字符串（NTMBS），或称“多字节字符串”，是后面跟随一个零值字节（空终止字符'\0'）的一串非零字节。

​	字符串中存储的每个字符可能占用多于一个字节。在多字节字符串中，用于表示字符的编码是本地环境限定的：它可以是 UTF-8、GB18030、EUC-JP、Shift-JIS 等等。例如，字符数组 `{'\xe4','\xbd','\xa0','\xe5','\xa5','\xbd','\0'}` 是一个以 UTF-8 多字节编码表示字符串 `"你好"` 的 NTMBS：前三字节编码字符 `"你"`，后三字节编码字符 `"好"`。用 GB18030 编码的相同字符串是字符数组 `{'\xc4', '\xe3', '\xba', '\xc3', '\0'}`，其中两个字符都编码成双字节序列。

​	一些多字节字符串中，任何给定的多字节字符序列可能会根据前置的字节序列表示不同的字符，这个前置序列称为“迁移序列”。此类编码是依赖状态的：需要当前迁移状态来转译每一个字符。只有起始和终止均为初始迁移状态，NTMBS 才是合法的：即若多字节编码使用迁移序列，则字符串结束前的整个序列必须为未迁移序列。这类编码的例子是 `BOCU-1` 和 [SCSU](https://www.unicode.org/reports/tr6)。

​	多字节字符串与[空终止字节字符串](https://zh.cppreference.com/w/c/string/byte)（NTBS）布局兼容，即是说，可以使用同样的工具存储、复制和检验，除了计算字符数的情况。若正确的本地环境正在发挥作用，则输入/输出函数亦可控制多字节字符串。运用下列依赖本地环境的函数，多字节字符串可以与宽字符串相互转换：

## 函数



### 多字节/宽字符转换

| 在标头 `<stdlib.h>` 定义                                   |                                                |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [mblen<br />](https://zh.cppreference.com/w/c/string/multibyte/mblen) | 返回下一个多字节字符的字节数 (函数)            |
| [mbtowc<br />](https://zh.cppreference.com/w/c/string/multibyte/mbtowc) | 转换下一个多字节字符为宽字符 (函数)            |
| [wctomb <br />wctomb_s (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/wctomb) | 转换宽字符为多字节表示 (函数)                  |
| [mbstowcs <br />mbstowcs_s (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbstowcs) | 转换窄多字节字符串为宽字符串 (函数)            |
| [wcstombs <br />wcstombs_s (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/wcstombs) | 转换宽字符串为窄多字节字符串 (函数)            |
| 在标头 `<wchar.h>` 定义                                    |                                                |
| [mbsinit (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbsinit) | 检查 mbstate_t 对象是否表示初始迁移状态 (函数) |
| [btowc (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/btowc) | 若可能，加宽单字节窄字符为宽字符 (函数)        |
| [wctob (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/wctob) | 若可能，收窄宽字符为单字节窄字符 (函数)        |
| [mbrlen (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrlen) | 给定状态，返回下一个多字节字符的字节数 (函数)  |
| [mbrtowc (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtowc) | 给定状态，转换下一个多字节字符为宽字符 (函数)  |
| [wcrtomb (C95)<br />wcrtomb_s (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/wcrtomb) | 给定状态，转换宽字符成其多字节表示 (函数)      |
| [mbsrtowcs (C95)<br />mbsrtowcs_s (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbsrtowcs) | 给定状态，转换窄多字节字符串为宽字符串 (函数)  |
| [wcsrtombs (C95)<br />wcsrtombs_s (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/wcsrtombs) | 给定状态，转换宽字符串为窄多字节字符串 (函数)  |
| 在标头 `<uchar.h>` 定义                                    |                                                |
| [mbrtoc8 (C23)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc8) | 转换窄多字节字符为 UTF-8 编码 (函数)           |
| [c8rtomb (C23)<br />](https://zh.cppreference.com/w/c/string/multibyte/c8rtomb) | 转换 UTF-8 字符串为窄多字节编码 (函数)         |
| [mbrtoc16 (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc16) | 转换窄多字节字符为 UTF-16 编码 (函数)          |
| [c16rtomb (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/c16rtomb) | 转换 UTF-16 字符为窄多字节编码 (函数)          |
| [mbrtoc32 (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc32) | 转换窄多字节字符为 UTF-32 编码 (函数)          |
| [c32rtomb (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/c32rtomb) | 转换 UTF-32 字符为窄多字节编码 (函数)          |

## 类型

| 在标头 `<uchar.h>` 定义                                    |                                         |
| ------------------------------------------------------------ | --------------------------------------- |
| 在标头 `<wchar.h>` 定义                                    |                                         |
| [mbstate_t (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) | 迭代多字节字符串所需的转换信息 (结构体) |
| 在标头 `<uchar.h>` 定义                                    |                                         |
| [char8_t (C23)<br />](https://zh.cppreference.com/w/c/string/multibyte/char8_t) | 8 位字符类型 (typedef)                  |
| [char16_t (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/char16_t) | 16 位字符类型 (typedef)                 |
| [char32_t (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/char32_t) | 32 位字符类型 (typedef)                 |

## 宏

| 在标头 `<limits.h>` 定义 |                                                       |
| -------------------------- | ----------------------------------------------------- |
| MB_LEN_MAX<br />           | 所支持的任何本地环境中多字节字符的最大字节数 (宏常量) |
| 在标头 `<stdlib.h>` 定义 |                                                       |
| MB_CUR_MAX<br />           | 当前本地环境中的多字节字符最大字节数 (宏变量)         |

## 参阅

空终止多字节字符串的 [C++ 文档](https://zh.cppreference.com/w/cpp/string/multibyte)