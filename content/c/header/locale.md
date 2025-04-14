+++
title = "<locale.h>"
date = 2025-04-14T10:02:55+08:00
weight = 110
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/locale](https://zh.cppreference.com/w/c/header/locale)

​	此标头是[本地化](https://zh.cppreference.com/w/c/locale)库的一部分。

## 类型

| [lconv   ](https://zh.cppreference.com/w/c/locale/lconv) | [localeconv](https://zh.cppreference.com/w/c/locale/localeconv) 所返回的格式化细节 (结构体) |
| -------------------------------------------------------- | ------------------------------------------------------------ |

## 常量

| [NULL   ](https://zh.cppreference.com/w/c/types/NULL)        | 实现定义的空指针常量 (宏常量)                                |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [LC_ALL   LC_COLLATE   LC_CTYPE   LC_MONETARY   LC_NUMERIC   LC_TIME   ](https://zh.cppreference.com/w/c/locale/LC_categories) | [setlocale](https://zh.cppreference.com/w/c/locale/setlocale) 所用的本地环境类别 (宏常量) |

## 函数

| [setlocale   ](https://zh.cppreference.com/w/c/locale/setlocale) | 获取和设置当前 C 本地环境 (函数)              |
| ------------------------------------------------------------ | --------------------------------------------- |
| [localeconv   ](https://zh.cppreference.com/w/c/locale/localeconv) | 查询当前本地环境的数值及货币格式化细节 (函数) |

### 概要

```c
// 在 "C" 本地环境中，各成员应当具有注释中指定的值
struct lconv
{
    char* decimal_point;        // "."
    char* thousands_sep;        // ""
    char* grouping;             // ""
    char* mon_decimal_point;    // ""
    char* mon_thousands_sep;    // ""
    char* mon_grouping;         // ""
    char* positive_sign;        // ""
    char* negative_sign;        // ""
    char* currency_symbol;      // ""
    char  frac_digits;          // CHAR_MAX
    char  p_cs_precedes;        // CHAR_MAX
    char  n_cs_precedes;        // CHAR_MAX
    char  p_sep_by_space;       // CHAR_MAX
    char  n_sep_by_space;       // CHAR_MAX
    char  p_sign_posn;          // CHAR_MAX
    char  n_sign_posn;          // CHAR_MAX
    char* int_curr_symbol;      // ""
    char  int_frac_digits;      // CHAR_MAX
    char  int_p_cs_precedes;    // CHAR_MAX
    char  int_n_cs_precedes;    // CHAR_MAX
    char  int_p_sep_by_space;   // CHAR_MAX
    char  int_n_sep_by_space;   // CHAR_MAX
    char  int_p_sign_posn;      // CHAR_MAX
    char  int_n_sign_posn;      // CHAR_MAX
};
 
char* setlocale(int category, const char* locale);
lconv* localeconv();
 
#define NULL        /* 见描述 */
#define LC_ALL      /* 见描述 */
#define LC_COLLATE  /* 见描述 */
#define LC_CTYPE    /* 见描述 */
#define LC_MONETARY /* 见描述 */
#define LC_NUMERIC  /* 见描述 */
#define LC_TIME     /* 见描述 */
```

## 注解

- 下列标头中也定义[NULL](https://zh.cppreference.com/w/c/types/NULL)：
  - [` <string.h>`](https://zh.cppreference.com/w/c/header/string)
  - [`<time.h>`](https://zh.cppreference.com/w/c/header/time)
  - [`<stddef.h>`](https://zh.cppreference.com/w/c/header/stddef)
  - [`<stdio.h>`](https://zh.cppreference.com/w/c/header/stdio)
  - [`<wchar.h>`](https://zh.cppreference.com/w/c/header/wchar)

