+++
title = "<ctype.h>"
date = 2025-04-14T09:37:34+08:00
weight = 30
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/ctype](https://zh.cppreference.com/w/c/header/ctype)

​	此标头是[空终结字节字符串](https://zh.cppreference.com/w/c/string/byte)库的一部分。

| Functions                                                    |                                   |
| ------------------------------------------------------------ | --------------------------------- |
| [isalnum](https://zh.cppreference.com/w/c/string/byte/isalnum) | 检查字符是否是字母或数字 (函数)   |
| [isalpha](https://zh.cppreference.com/w/c/string/byte/isalpha) | 检查字符是否是字母 (函数)         |
| [islower](https://zh.cppreference.com/w/c/string/byte/islower) | 检查字符是否是小写字母 (函数)     |
| [isupper](https://zh.cppreference.com/w/c/string/byte/isupper) | 检查字符是否是大写字母 (函数)     |
| [isdigit](https://zh.cppreference.com/w/c/string/byte/isdigit) | 检查字符是否是数字 (函数)         |
| [isxdigit](https://zh.cppreference.com/w/c/string/byte/isxdigit) | 检查字符是否是十六进制字符 (函数) |
| [iscntrl](https://zh.cppreference.com/w/c/string/byte/iscntrl) | 检查字符是否是控制字符 (函数)     |
| [isgraph](https://zh.cppreference.com/w/c/string/byte/isgraph) | 检查字符是否是图形字符 (函数)     |
| [isspace](https://zh.cppreference.com/w/c/string/byte/isspace) | 检查字符是否是空白字符 (函数)     |
| [isblank](https://zh.cppreference.com/w/c/string/byte/isblank)(C99) | 检查字符是否是空格字符 (函数)     |
| [isprint](https://zh.cppreference.com/w/c/string/byte/isprint) | 检查字符是否是可打印字符 (函数)   |
| [ispunct](https://zh.cppreference.com/w/c/string/byte/ispunct) | 检查字符是否是标点字符 (函数)     |
| [tolower](https://zh.cppreference.com/w/c/string/byte/tolower) | 将字符转换成小写 (函数)           |
| [toupper](https://zh.cppreference.com/w/c/string/byte/toupper) | 将字符转换成大写 (函数)           |

### 概要

```c
int isalnum(int c);
int isalpha(int c);
int isblank(int c);
int iscntrl(int c);
int isdigit(int c);
int isgraph(int c);
int islower(int c);
int isprint(int c);
int ispunct(int c);
int isspace(int c);
int isupper(int c);
int isxdigit(int c);
int tolower(int c);
int toupper(int c);
```