+++
title = "<string.h>"
date = 2025-04-14T15:22:50+08:00
weight = 260
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/string](https://zh.cppreference.com/w/c/header/string)

​	此标题提供了用于处理[空终止字节字符串](https://zh.cppreference.com/w/c/string/byte)的函数。

## 宏

| [NULL<br />](https://zh.cppreference.com/w/c/types/NULL) | 实现定义的空指针常量 (宏常量) |
| -------------------------------------------------------- | ----------------------------- |

## 类型

| [size_t<br />](https://zh.cppreference.com/w/c/types/size_t) | [`<izeo>`](https://zh.cppreference.com/w/c/language/sizeof) 运算符返回的无符号整数类型 (typedef) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |

## 函数

### 字符串操纵

| [strcpy <br />strcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcpy) | 复制字符串给另一个 (函数)                              |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| [strncpy <br />strncpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncpy) | 从字符串复制一定数量的字符到另一个 (函数)              |
| [strcat <br />strcat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strcat) | 连接两个字符串 (函数)                                  |
| [strncat <br />strncat_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strncat) | 连接两个字符串的一定数量字符 (函数)                    |
| [strxfrm<br />](https://zh.cppreference.com/w/c/string/byte/strxfrm) | 变换字符串，使得 strcmp 会产生同 strcoll 的结果 (函数) |
| [strdup (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strdup) | 分配字符串的副本 (函数)                                |
| [strndup (C23)<br />](https://zh.cppreference.com/w/c/string/byte/strndup) | 分配拥有指定大小的字符串副本 (函数)                    |

### 字符串检验

| [strlen <br />strnlen_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strlen) | 返回给定字符串的长度 (函数)                               |
| ------------------------------------------------------------ | --------------------------------------------------------- |
| [strcmp<br />](https://zh.cppreference.com/w/c/string/byte/strcmp) | 比较两个字符串 (函数)                                     |
| [strncmp<br />](https://zh.cppreference.com/w/c/string/byte/strncmp) | 比较两个字符串的一定数量字符 (函数)                       |
| [strcoll<br />](https://zh.cppreference.com/w/c/string/byte/strcoll) | 比较两个字符串，根据当前本地环境 (函数)                   |
| [strchr<br />](https://zh.cppreference.com/w/c/string/byte/strchr) | 查找字符的首次出现 (函数)                                 |
| [strrchr<br />](https://zh.cppreference.com/w/c/string/byte/strrchr) | 查找字符的最后一次出现 (函数)                             |
| [strspn<br />](https://zh.cppreference.com/w/c/string/byte/strspn) | 返回由另一个字符串中的字符分割的最大起始段长度 (函数)     |
| [strcspn<br />](https://zh.cppreference.com/w/c/string/byte/strcspn) | 返回另一个字符串所不具有的字符分割的最大起始段长度 (函数) |
| [strpbrk<br />](https://zh.cppreference.com/w/c/string/byte/strpbrk) | 查找字符串中的任意字符在另一个字符串中的首个位置 (函数)   |
| [strstr<br />](https://zh.cppreference.com/w/c/string/byte/strstr) | 查找子串字符的首次出现 (函数)                             |
| [strtok <br />strtok_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strtok) | 查找字节字符串中的下一个记号 (函数)                       |

### 字符数组操纵

| [memchr<br />](https://zh.cppreference.com/w/c/string/byte/memchr) | 在数组中搜索字符的首次出现 (函数)               |
| ------------------------------------------------------------ | ----------------------------------------------- |
| [memcmp<br />](https://zh.cppreference.com/w/c/string/byte/memcmp) | 比较两块缓冲区 (函数)                           |
| [memset <br />memset_explicit (C23)<br />memset_s (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memset) | 以字符填充缓冲区 (函数)                         |
| [memcpy <br />memcpy_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memcpy) | 复制缓冲区到另一个 (函数)                       |
| [memmove <br />memmove_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/memmove) | 移动缓冲区到另一个 (函数)                       |
| [memccpy (C23)<br />](https://zh.cppreference.com/w/c/string/byte/memccpy) | 复制缓冲区到另一个，在指定的分隔符后停止 (函数) |

### 杂项

| [strerror <br />strerror_s (C11)<br />strerrorlen_s (C11)<br />](https://zh.cppreference.com/w/c/string/byte/strerror) | 返回给定错误码的文本版本 (函数) |
| ------------------------------------------------------------ | ------------------------------- |

## 概要

```c
#define __STDC_VERSION_STRING_H__ 202311L
 
#define NULL /* 见描述 */
 
typedef /* 见描述 */ size_t;
 
void* memcpy(void* restrict s1, const void* restrict s2, size_t n);
void* memccpy(void* restrict s1, const void* restrict s2, int c, size_t n);
void* memmove(void* s1, const void* s2, size_t n);
char* strcpy(char* restrict s1, const char* restrict s2);
char* strncpy(char* restrict s1, const char* restrict s2, size_t n);
char* strdup(const char* s);
char* strndup(const char* s, size_t n);
char* strcat(char* restrict s1, const char* restrict s2);
char* strncat(char* restrict s1, const char* restrict s2, size_t n);
int memcmp(const void* s1, const void* s2, size_t n);
int strcmp(const char* s1, const char* s2);
int strcoll(const char* s1, const char* s2);
int strncmp(const char* s1, const char* s2, size_t n);
size_t strxfrm(char* restrict s1, const char* restrict s2, size_t n);
/*QVoid*/* memchr(/*QVoid*/* s, int c, size_t n);
/*QChar*/* strchr(/*QChar*/* s, int c);
size_t strcspn(const char* s1, const char* s2);
/*QChar*/* strpbrk(/*QChar*/* s1, const char* s2);
/*QChar*/* strrchr(/*QChar*/* s, int c);
size_t strspn(const char* s1, const char* s2);
/*QChar*/* strstr(/*QChar*/* s1, const char* s2);
char* strtok(char* restrict s1, const char* restrict s2);
void* memset(void* s, int c, size_t n);
void* memset_explicit(void* s, int c, size_t n);
char* strerror(int errnum);
size_t strlen(const char* s);
size_t strnlen(const char* s, size_t n);
```

​	仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 `<string.h>` 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#ifdef __STDC_WANT_LIB_EXT1__
 
tyepdef /* 见描述 */ errno_t;
tyepdef /* 见描述 */ rsize_t;
 
errno_t memcpy_s(void* restrict s1, rsize_t s1max, const void* restrict s2, rsize_t n);
errno_t memmove_s(void* s1, rsize_t s1max, const void* s2, rsize_t n);
errno_t strcpy_s(char* restrict s1, rsize_t s1max, const char* restrict s2);
errno_t strncpy_s(char* restrict s1, rsize_t s1max, const char* restrict s2, rsize_t n);
errno_t strcat_s(char* restrict s1, rsize_t s1max, const char* restrict s2);
errno_t strncat_s(char* restrict s1, rsize_t s1max, const char* restrict s2, rsize_t n);
char* strtok_s(char* restrict s1, rsize_t* restrict s1max,
               const char* restrict s2, char** restrict ptr);
errno_t memset_s(void* s, rsize_t smax, int c, rsize_t n)
errno_t strerror_s(char* s, rsize_t maxsize, errno_t errnum);
size_t strerrorlen_s(errno_t errnum);
size_t strnlen_s(const char* s, size_t maxsize);
 
#endif
```