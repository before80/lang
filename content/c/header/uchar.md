+++
title = "<uchar.h> (C11)"
date = 2025-04-14T15:31:34+08:00
weight = 300
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/uchar](https://zh.cppreference.com/w/c/header/uchar)

​	此标头是[空终结多字节字符串](https://zh.cppreference.com/w/c/string/multibyte)库的一部分。

## 函数

| [mbrtoc8 (C23)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc8) | 转换窄多字节字符为 UTF-8 编码 (函数)   |
| ------------------------------------------------------------ | -------------------------------------- |
| [c8rtomb (C23)<br />](https://zh.cppreference.com/w/c/string/multibyte/c8rtomb) | 转换 UTF-8 字符串为窄多字节编码 (函数) |
| [mbrtoc16 (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc16) | 转换窄多字节字符为 UTF-16 编码 (函数)  |
| [c16rtomb (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/c16rtomb) | 转换 UTF-16 字符为窄多字节编码 (函数)  |
| [mbrtoc32 (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbrtoc32) | 转换窄多字节字符为 UTF-32 编码 (函数)  |
| [c32rtomb (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/c32rtomb) | 转换 UTF-32 字符为窄多字节编码 (函数)  |

## 类型

| [mbstate_t (C95)<br />](https://zh.cppreference.com/w/c/string/multibyte/mbstate_t) | 迭代多字节字符串所需的转换信息 (结构体) |
| ------------------------------------------------------------ | --------------------------------------- |
| [char8_t (C23)<br />](https://zh.cppreference.com/w/c/string/multibyte/char8_t) | 8 位字符类型 (typedef)                  |
| [char16_t (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/char16_t) | 16 位字符类型 (typedef)                 |
| [char32_t (C11)<br />](https://zh.cppreference.com/w/c/string/multibyte/char32_t) | 32 位字符类型 (typedef)                 |

## 概要

``` c
#define __STDC_VERSION_UCHAR_H__ 202311L
 
typedef /* 见描述 */ mbstate_t;
typedef /* 见描述 */ size_t;
typedef /* 见描述 */ char8_t;
typedef /* 见描述 */ char16_t;
typedef /* 见描述 */ char32_t;
 
size_t mbrtoc8(char8_t* restrict pc8, const char* restrict s, size_t n,
               mbstate_t* restrict ps);
size_t c8rtomb(char* restrict s, char8_t c8, mbstate_t* restrict ps);
size_t mbrtoc16(char16_t* restrict pc16, const char* restrict s, size_t n,
                mbstate_t* restrict ps);
size_t c16rtomb(char* restrict s, char16_t c16, mbstate_t* restrict ps);
size_t mbrtoc32(char32_t* restrict pc32, const char* restrict s, size_t n,
                mbstate_t* restrict ps);
size_t c32rtomb(char* restrict s, char32_t c32, mbstate_t* restrict ps);
```