+++
title = "<wctype.h> (C95)"
date = 2025-04-14T15:34:28+08:00
weight = 330
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/wctype](https://zh.cppreference.com/w/c/header/wctype)

​	此标头是[宽字符分类与映射工具](https://zh.cppreference.com/w/c/string/wide)库的一部分。

## 函数

### 字符分类

| [iswalnum (C95)<br />](https://zh.cppreference.com/w/c/string/wide/iswalnum) | 检查宽字符是否为字母或数字 (函数)                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
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

### 字符操纵

| [towlower (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towlower) | 转换宽字符为小写 (函数)                        |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [towupper (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towupper) | 转换宽字符为大写 (函数)                        |
| [towctrans (C95)<br />](https://zh.cppreference.com/w/c/string/wide/towctrans) | 按照指定的 LC_TYPE 映射分类进行字符映射 (函数) |
| [wctrans (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wctrans) | 查找当前 C 本地环境中的字符映射类别 (函数)     |

## 类型

| wint_t (C95)<br />    | 可以保有任意有效宽字符和至少一个额外值的整数类型 (typedef) |
| --------------------- | ---------------------------------------------------------- |
| wctrans_t (C95)<br /> | 可以保有本地环境特有字符映射的标量类型 (typedef)           |
| wctype_t (C95)<br />  | 可以保有本地环境特有字符分类的标量类型 (typedef)           |

## 宏

| WEOF (C95)<br /> | wint_t 类型的非字符值，用于指示错误 (宏常量) |
| ---------------- | -------------------------------------------- |

## 概要

``` c
typedef /* 见描述 */ wctrans_t;
typedef /* 见描述 */ wctype_t;
typedef /* 见描述 */ wint_t;
 
#define WEOF /* 见描述 */
 
int iswalnum(wint_t wc);
int iswalpha(wint_t wc);
int iswblank(wint_t wc);
int iswcntrl(wint_t wc);
int iswdigit(wint_t wc);
int iswgraph(wint_t wc);
int iswlower(wint_t wc);
int iswprint(wint_t wc);
int iswpunct(wint_t wc);
int iswspace(wint_t wc);
int iswupper(wint_t wc);
int iswxdigit(wint_t wc);
int iswctype(wint_t wc, wctype_t desc);
wctype_t wctype(const char* property);
wint_t towlower(wint_t wc);
wint_t towupper(wint_t wc);
wint_t towctrans(wint_t wc, wctrans_t desc);
wctrans_t wctrans(const char* property);
```