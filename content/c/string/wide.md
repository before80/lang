+++
title = "空终止宽字符串"
date = 2025-04-15T09:04:22+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/string/wide](https://zh.cppreference.com/w/c/string/wide)

​	空终止宽字符串（NTWS）是以空字符为结尾的合法宽字符序列。

## 函数

### 字符分类

| 在标头 `<wctype.h>` 定义                                   |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [iswalnum (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswalnum) | 检查宽字符是否为字母或数字 (函数)                            |
| [iswalpha (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswalpha) | 检查宽字符是否为字母 (函数)                                  |
| [iswlower (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswlower) | 检查宽字符是否为小写 (函数)                                  |
| [iswupper (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswupper) | 检查宽字符是否为大写 (函数)                                  |
| [iswdigit (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswdigit) | 检查宽字符是否为数字 (函数)                                  |
| [iswxdigit (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswxdigit) | 检查宽字符是否为十六进制字符 (函数)                          |
| [iswcntrl (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | 检查宽字符是否为控制字符 (函数)                              |
| [iswgraph (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswgraph) | 检查宽字符是否为图形字符 (函数)                              |
| [iswspace (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswspace) | 检查宽字符是否为空白符 (函数)                                |
| [iswblank (C99)<br />](https://zh.cppreference.com/w/c/string/wide/iswblank) | 检查宽字符是否为空格 (函数)                                  |
| [iswprint (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswprint) | 检查宽字符是否为打印字符 (函数)                              |
| [iswpunct (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswpunct) | 检查宽字符是否为标点字符 (函数)                              |
| [iswctype (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswctype) | 按照指定的 [LC_CTYPE](https://zh.cppreference.com/w/c/locale/LC_categories) 类别分类宽字符 (函数) |
| [wctype (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wctype) | 查找当前 C 本地环境中的字符分类类别 (函数)                   |

### 字符操作

| 在标头 `<wctype.h>` 定义                                   |                                                |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [towlower (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towlower) | 转换宽字符为小写 (函数)                        |
| [towupper (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towupper) | 转换宽字符为大写 (函数)                        |
| [towctrans (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towctrans) | 按照指定的 LC_TYPE 映射分类进行字符映射 (函数) |
| [wctrans (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wctrans) | 查找当前 C 本地环境中的字符映射类别 (函数)     |

| ASCII 值 |   ASCII 值 |   ASCII 值    |              字符               | [`iscntrl`](https://zh.cppreference.com/w/c/string/byte/iscntrl) [`iswcntrl`](https://zh.cppreference.com/w/c/string/wide/iswcntrl) | [`isprint`](https://zh.cppreference.com/w/c/string/byte/isprint) [`iswprint`](https://zh.cppreference.com/w/c/string/wide/iswprint) | [`isspace`](https://zh.cppreference.com/w/c/string/byte/isspace) [`iswspace`](https://zh.cppreference.com/w/c/string/wide/iswspace) | [`isblank`](https://zh.cppreference.com/w/c/string/byte/isblank) [`iswblank`](https://zh.cppreference.com/w/c/string/wide/iswblank) | [`isgraph`](https://zh.cppreference.com/w/c/string/byte/isgraph) [`iswgraph`](https://zh.cppreference.com/w/c/string/wide/iswgraph) | [`ispunct`](https://zh.cppreference.com/w/c/string/byte/ispunct) [`iswpunct`](https://zh.cppreference.com/w/c/string/wide/iswpunct) | [`isalnum`](https://zh.cppreference.com/w/c/string/byte/isalnum) [`iswalnum`](https://zh.cppreference.com/w/c/string/wide/iswalnum) | [`isalpha`](https://zh.cppreference.com/w/c/string/byte/isalpha) [`iswalpha`](https://zh.cppreference.com/w/c/string/wide/iswalpha) | [`isupper`](https://zh.cppreference.com/w/c/string/byte/isupper) [`iswupper`](https://zh.cppreference.com/w/c/string/wide/iswupper) | [`islower`](https://zh.cppreference.com/w/c/string/byte/islower) [`iswlower`](https://zh.cppreference.com/w/c/string/wide/iswlower) | [`isdigit`](https://zh.cppreference.com/w/c/string/byte/isdigit) [`iswdigit`](https://zh.cppreference.com/w/c/string/wide/iswdigit) | [`isxdigit`](https://zh.cppreference.com/w/c/string/byte/isxdigit) [`iswxdigit`](https://zh.cppreference.com/w/c/string/wide/iswxdigit) |
| :------: | :-----------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | :----------------------------------------------------------: | ---- | ---- |
|  十进制  |   十六进制    |                            八进制                            |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |      |      |
|   0–8    |  `\x0`–`\x8`  |                          `\0`–`\10`                          |                      控制码 (`NUL` 等)                       |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|    9     |     `\x9`     |                            `\11`                             |                        制表符 (`\t`)                         |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  10–13   |  `\xA`–`\xD`  |                         `\12`–`\15`                          |               空白符 (`\n`, `\v`, `\f`, `\r`)                |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  14–31   | `\xE`–`\x1F`  |                         `\16`–`\37`                          |                            控制码                            |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|    32    |    `\x20`     |                            `\40`                             |                             空格                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  33–47   | `\x21`–`\x2F` |                         `\41`–`\57`                          |                      `!"#$%&'()*+,-./`                       |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  48–57   | `\x30`–`\x39` |                         `\60`–`\71`                          |                         `0123456789`                         |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              | `≠0` | `≠0` |
|  58–64   | `\x3A`–`\x40` |                         `\72`–`\100`                         |                          `:;<=>?@`                           |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|  65–70   | `\x41`–`\x46` |                        `\101`–`\106`                         |                           `ABCDEF`                           |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `≠0`                             |                             `0`                              | `0`  | `≠0` |
|  71–90   | `\x47`–`\x5A` |                        `\107`–`\132`                         |                  `GHIJKLMNOP` `QRSTUVWXYZ`                   |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `≠0`                             |                             `0`                              | `0`  | `0`  |
|  91–96   | `\x5B`–`\x60` |                        `\133`–`\140`                         |                     [\]^_`  |**`0`**|**`≠0`**|**`0`**|**`0`**|**`≠0`**|**`≠0`**|**`0`**|**`0`**|**`0`**|**`0`**|**`0`**|**`0`**|
|  97–102  | `\x61`–`\x66` |                        `\141`–`\146`                         |                           `abcdef`                           |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `≠0`                             | `0`  | `≠0` |
| 103–122  | `\x67`–`\x7A` |                        `\147`–`\172`                         |                  `ghijklmnop` `qrstuvwxyz`                   |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `≠0`                             | `0`  | `0`  |
| 123–126  | `\x7B`–`\x7E` |                        `\173`–`\176`                         |                            `{|}~`                            |                             `0`                              |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `≠0`                             |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |
|   127    |    `\x7F`     |                            `\177`                            |                        退格符 (`DEL`)                        |                             `≠0`                             |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              |                             `0`                              | `0`  | `0`  |





### 转换成数值格式

| 在标头 `<wchar.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)                                    |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数)                              |
| [wcstof (C99)<br />wcstod (C99)<br />wcstold (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstof) | 转换宽字符串为浮点数 (函数)                                  |
| 在标头 `<inttypes.h>` 定义                                 |                                                              |
| [wcstoimax (C99)<br />wcstoumax (C99)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoimax) | 转换宽字符串为 [intmax_t](https://zh.cppreference.com/w/c/types/integer) 或 [uintmax_t](https://zh.cppreference.com/w/c/types/integer) (函数) |

### 字符串操作

| 在标头 `<wchar.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcscpy (C95)<br />wcscpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscpy) | 复制宽字符串给另一个 (函数)                                  |
| [wcsncpy (C95)<br />wcsncpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsncpy) | 复制字符串一定量的宽字符到另一个 (函数)                      |
| [wcscat (C95)<br />wcscat_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscat) | 追加一个宽字符串的副本到另一个 (函数)                        |
| [wcsncat (C95)<br />wcsncat_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsncat) | 追加宽字符串中的一定量宽字符串到另一个 (函数)                |
| [wcsxfrm (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsxfrm) | 变换宽字符串，使得 [wcscmp](https://zh.cppreference.com/w/c/string/wide/wcscmp) 会产生与 [wcscoll](https://zh.cppreference.com/w/c/string/wide/wcscoll) 相同的结果 (函数) |

### 字符串检验

| 在标头 `<wchar.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcslen (C95)<br />wcsnlen_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcslen) | 返回宽字符串的长度 (函数)                                    |
| [wcscmp (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscmp) | 比较两个宽字符串 (函数)                                      |
| [wcsncmp (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsncmp) | 比较来自两个宽字符串的一定量字符 (函数)                      |
| [wcscoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscoll) | 根据当前本地环境比较两个宽字符串 (函数)                      |
| [wcschr (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcschr) | 查找宽字符在宽字符串中的首次出现 (函数)                      |
| [wcsrchr (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsrchr) | 查找宽字符在宽字符串中的最后一次出现 (函数)                  |
| [wcsspn (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsspn) | 返回仅由另一个宽字符串中出现的宽字符分隔的最长首段长度 (函数) |
| [wcscspn (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscspn) | 返回仅由*不* ﻿出现于另一个宽字符串中的宽字符分隔的最长首段长度 (函数) |
| [wcspbrk (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcspbrk) | 查找一个宽字符串中的任何字符在另一个宽字符串中的首个位置 (函数) |
| [wcsstr (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsstr) | 查找一个宽字符串在另一个宽字符串中的首次出现 (函数)          |
| [wcstok (C95)<br />wcstok_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstok) | 查找宽字符串中的下一个记号 (函数)                            |



### 宽字符数组操作

| 在标头 `<wchar.h>` 定义                                    |                                                   |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [wmemcpy (C95)<br />wmemcpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcpy) | 在两个不重叠的数组间复制一定数量的宽字符 (函数)   |
| [wmemmove (C95)<br />wmemmove_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemmove) | 在两个可能重叠的数组间复制一定数量的宽字符 (函数) |
| [wmemcmp (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcmp) | 比较两个数组中一定数量的宽字符 (函数)             |
| [wmemchr (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemchr) | 在宽字符数组中查找宽字符的首次出现 (函数)         |
| [wmemset (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemset) | 复制给定的宽字符到宽字符数组的所有位置 (函数)     |

## 类型

| 在标头 `<stddef.h>` 定义 |                                                            |
| -------------------------- | ---------------------------------------------------------- |
| 在标头 `<stdlib.h>` 定义 |                                                            |
| 在标头 `<wchar.h>` 定义  |                                                            |
| wchar_t<br />            | 可保有任何合法宽字符的整数类型 (typedef)                   |
| 在标头 `<wchar.h>` 定义  |                                                            |
| 在标头 `<wctype.h>` 定义 |                                                            |
| wint_t (C95)<br />       | 可保有任何合法宽字符，并至少多出一个值的整数类型 (typedef) |
| 在标头 `<wctype.h>` 定义 |                                                            |
| wctrans_t (C95)<br />    | 保有本地环境特定的字符映射的标量类型 (typedef)             |
| wctype_t (C95)<br />     | 保有本地环境特定的字符分类的标量类型 (typedef)             |

## 宏

| 在标头 `<wchar.h>` 定义  |                                               |
| -------------------------- | --------------------------------------------- |
| 在标头 `<wctype.h>` 定义 |                                               |
| WEOF (C95)<br />         | 用于指示错误的 `wint_t` 类型的非字符值 (宏常量) |
| 在标头 `<wchar.h>` 定义  |                                               |
| 在标头 `<stdint.h>` 定义 |                                               |
| WCHAR_MIN (C95)<br />    | `wchar_t` 的最小合法值 (宏常量)               |
| WCHAR_MAX (C95)<br />    | `wchar_t` 的最大合法值 (宏常量)               |

## 参阅

​	**空终止宽字符串**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/string/wide)**