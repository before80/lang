+++
title = "<wchar.h> (C95)"
date = 2025-04-14T15:32:43+08:00
weight = 310
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/wchar](https://zh.cppreference.com/w/c/header/wchar)

​	此标头是[空终止宽字符串](https://zh.cppreference.com/w/c/string/wide)库的一部分。

## 函数

### 转换为数值格式

| [wcstol (C95)<br />wcstoll (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstol) | 转换宽字符串为整数 (函数)       |
| ------------------------------------------------------------ | ------------------------------- |
| [wcstoul (C95)<br />wcstoull (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstoul) | 转换宽字符串为无符号整数 (函数) |
| [wcstof (C99)<br />wcstod (C99)<br />wcstold (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcstof) | 转换宽字符串为浮点数 (函数)     |

### 字符串操纵

| [wcscpy (C95)<br />wcscpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscpy) | 复制宽字符串给另一个 (函数)                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [wcsncpy (C95)<br />wcsncpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsncpy) | 复制字符串一定量的宽字符到另一个 (函数)                      |
| [wcscat (C95)<br />wcscat_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcscat) | 追加一个宽字符串的副本到另一个 (函数)                        |
| [wcsncat (C95)<br />wcsncat_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsncat) | 追加宽字符串中的一定量宽字符串到另一个 (函数)                |
| [wcsxfrm (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcsxfrm) | 变换宽字符串，使得 [wcscmp](https://zh.cppreference.com/w/c/string/wide/wcscmp) 会产生与 [wcscoll](https://zh.cppreference.com/w/c/string/wide/wcscoll) 相同的结果 (函数) |

### 字符串检验

| [wcslen (C95)<br />wcsnlen_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wcslen) | 返回宽字符串的长度 (函数)                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
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

### 宽字符数组操纵

| [wmemcpy (C95)<br />wmemcpy_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcpy) | 在两个不重叠的数组间复制一定数量的宽字符 (函数)   |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [wmemmove (C95)<br />wmemmove_s (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemmove) | 在两个可能重叠的数组间复制一定数量的宽字符 (函数) |
| [wmemcmp (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemcmp) | 比较两个数组中一定数量的宽字符 (函数)             |
| [wmemchr (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemchr) | 在宽字符数组中查找宽字符的首次出现 (函数)         |
| [wmemset (C95)<br />](https://zh.cppreference.com/w/c/string/wide/wmemset) | 复制给定的宽字符到宽字符数组的所有位置 (函数)     |

## 类型

| wchar_t<br />      | 可以保有任意有效宽字符的整数类型 (typedef)                 |
| ------------------ | ---------------------------------------------------------- |
| wint_t (C95)<br /> | 可以保有任意有效宽字符和至少一个额外值的整数类型 (typedef) |

## 宏

| WEOF (C95)<br />      | wint_t 类型的非字符值，用于指示错误 (宏常量) |
| --------------------- | -------------------------------------------- |
| WCHAR_MIN (C95)<br /> | wchar_t 的最小有效值 (宏常量)                |
| WCHAR_MAX (C95)<br /> | wchar_t 的最大有效值 (宏常量)                |

## 概要

```c
#define __STDC_VERSION_WCHAR_H__ 202311L
 
typedef /* 见描述 */ wchar_t;
typedef /* 见描述 */ size_t;
typedef /* 见描述 */ mbstate_t;
typedef /* 见描述 */ wint_t;
 
struct tm { /* 见描述 */ };
 
#define MB_UTF16    /* 见描述 */
#define MB_UTF32    /* 见描述 */
#define MB_UTF8     /* 见描述 */
#define NULL        /* 见描述 */
#define WCHAR_MAX   /* 见描述 */
#define WCHAR_MIN   /* 见描述 */
#define WCHAR_UTF16 /* 见描述 */
#define WCHAR_UTF32 /* 见描述 */
#define WCHAR_UTF8  /* 见描述 */
#define WCHAR_WIDTH /* 见描述 */
#define WEOF        /* 见描述 */
 
int fwprintf(FILE* restrict stream, const wchar_t* restrict format, ...);
int fwscanf(FILE* restrict stream, const wchar_t* restrict format, ...);
int swprintf(wchar_t* restrict s, size_t n, const wchar_t* restrict format, ...);
int swscanf(const wchar_t* restrict s, const wchar_t* restrict format, ...);
int vfwprintf(FILE* restrict stream, const wchar_t* restrict format, va_list arg);
int vfwscanf(FILE* restrict stream, const wchar_t* restrict format, va_list arg);
int vswprintf(wchar_t* restrict s, size_t n, const wchar_t* restrict format,
              va_list arg);
int vswscanf(const wchar_t* restrict s, const wchar_t* restrict format, va_list arg);
int vwprintf(const wchar_t* restrict format, va_list arg);
int vwscanf(const wchar_t* restrict format, va_list arg);
int wprintf(const wchar_t* restrict format, ...);
int wscanf(const wchar_t* restrict format, ...);
wint_t fgetwc(FILE* stream);
wchar_t* fgetws(wchar_t* restrict s, int n, FILE* restrict stream);
wint_t fputwc(wchar_t c, FILE* stream);
int fputws(const wchar_t* restrict s, FILE* restrict stream);
int fwide(FILE* stream, int mode);
wint_t getwc(FILE* stream);
wint_t getwchar(void);
wint_t putwc(wchar_t c, FILE* stream);
wint_t putwchar(wchar_t c);
wint_t ungetwc(wint_t c, FILE* stream);
double wcstod(const wchar_t* restrict nptr, wchar_t** restrict endptr);
float wcstof(const wchar_t* restrict nptr, wchar_t** restrict endptr);
long double wcstold(const wchar_t* restrict nptr, wchar_t** restrict endptr);
long int wcstol(const wchar_t* restrict nptr, wchar_t** restrict endptr, int base);
long long int wcstoll(const wchar_t* restrict nptr, wchar_t** restrict endptr, int base);
unsigned long int wcstoul(const wchar_t* restrict nptr, wchar_t** restrict endptr,
                          int base);
unsigned long long int wcstoull(const wchar_t* restrict nptr, wchar_t** restrict endptr,
                                int base);
wchar_t* wcscpy(wchar_t* restrict s1, const wchar_t* restrict s2);
wchar_t* wcsncpy(wchar_t* restrict s1, const wchar_t* restrict s2, size_t n);
wchar_t* wmemcpy(wchar_t* restrict s1, const wchar_t* restrict s2, size_t n);
wchar_t* wmemmove(wchar_t* s1, const wchar_t* s2, size_t n);
wchar_t* wcscat(wchar_t* restrict s1, const wchar_t* restrict s2);
wchar_t* wcsncat(wchar_t* restrict s1, const wchar_t* restrict s2, size_t n);
int wcscmp(const wchar_t* s1, const wchar_t* s2);
int wcscoll(const wchar_t* s1, const wchar_t* s2);
int wcsncmp(const wchar_t* s1, const wchar_t* s2, size_t n);
size_t wcsxfrm(wchar_t* restrict s1, const wchar_t* restrict s2, size_t n);
int wmemcmp(const wchar_t* s1, const wchar_t* s2, size_t n);
/*QWchar_t*/* wcschr(/*QWchar_t*/* s, wchar_t c);
size_t wcscspn(const wchar_t* s1, const wchar_t* s2);
/*QWchar_t*/* wcspbrk(/*QWchar_t*/* s1, const wchar_t* s2);
/*QWchar_t*/* wcsrchr(/*QWchar_t*/* s, wchar_t c);
size_t wcsspn(const wchar_t* s1, const wchar_t* s2);
/*QWchar_t*/* wcsstr(/*QWchar_t*/* s1, const wchar_t* s2);
wchar_t* wcstok(wchar_t* restrict s1, const wchar_t* restrict s2,
                wchar_t** restrict ptr);
/*QWchar_t*/* wmemchr(/*QWchar_t*/* s, wchar_t c, size_t n);
size_t wcslen(const wchar_t* s);
size_t wcsnlen(const wchar_t* s, size_t n);
wchar_t* wmemset(wchar_t* s, wchar_t c, size_t n);
size_t wcsftime(wchar_t* restrict s, size_t maxsize, const wchar_t* restrict format,
                const struct tm* restrict timeptr);
wint_t btowc(int c);
int wctob(wint_t c);
int mbsinit(const mbstate_t* ps);
size_t mbrlen(const char* restrict s, size_t n, mbstate_t* restrict ps);
size_t mbrtowc(wchar_t* restrict pwc, const char* restrict s, size_t n,
               mbstate_t* restrict ps);
size_t wcrtomb(char* restrict s, wchar_t wc, mbstate_t* restrict ps);
size_t mbsrtowcs(wchar_t* restrict dst, const char** restrict src, size_t len,
                 mbstate_t* restrict ps);
size_t wcsrtombs(char* restrict dst, const wchar_t** restrict src, size_t len,
                 mbstate_t* restrict ps);
```

​	仅当实现定义了 `__STDC_IEC_60559_DFP__`：

```c
_Decimal32 wcstod32(const wchar_t* restrict nptr, wchar_t** restrict endptr);
_Decimal64 wcstod64(const wchar_t* restrict nptr, wchar_t** restrict endptr);
_Decimal128 wcstod128(const wchar_t* restrict nptr, wchar_t** restrict endptr);
```

​	仅当实现定义了 `__STDC_IEC_60559_TYPES__`，并且用户代码在对 **`<wchar.h>`** 的所有包含前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：

```c
#ifdef __STDC_WANT_IEC_60559_TYPES_EXT__
/*_FloatN*/ /*wcstofN*/(const wchar_t* restrict nptr, wchar_t** restrict endptr);
/*_FloatNx*/ /*wcstofNx*/(const wchar_t* restrict nptr, wchar_t** restrict endptr);
/*_DecimalN*/ /*wcstodN*/(const wchar_t* restrict nptr, wchar_t** restrict endptr);
/*_DecimalNx*/ /*wcstodNx*/(const wchar_t* restrict nptr, wchar_t** restrict endptr);
void /*wcstoencfN*/(unsigned char encptr[restrict static N/8],
                    const wchar_t* restrict nptr, wchar_t** restrict endptr);
void /*wcstoencdecdN*/(unsigned char encptr[restrict static N/8],
                       const wchar_t* restrict nptr, wchar_t** restrict endptr);
void /*wcstoencbindN*/(unsigned char encptr[restrict static N/8],
                       const wchar_t* restrict nptr, wchar_t** restrict endptr);
#endif
```

​	仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 **`<wchar.h>`** 的所有包含前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#ifdef __STDC_WANT_LIB_EXT1__
typedef /* 见描述 */ errno_t;
typedef /* 见描述 */ rsize_t;
 
int fwprintf_s(FILE* restrict stream, const wchar_t* restrict format, ...);
int fwscanf_s(FILE* restrict stream, const wchar_t* restrict format, ...);
int snwprintf_s(wchar_t* restrict s, rsize_t n, const wchar_t* restrict format, ...);
int swprintf_s(wchar_t* restrict s, rsize_t n, const wchar_t* restrict format, ...);
int swscanf_s(const wchar_t* restrict s, const wchar_t* restrict format, ...);
int vfwprintf_s(FILE* restrict stream, const wchar_t* restrict format, va_list arg);
int vfwscanf_s(FILE* restrict stream, const wchar_t* restrict format, va_list arg);
int vsnwprintf_s(wchar_t* restrict s, rsize_t n, const wchar_t* restrict format,
                 va_list arg);
int vswprintf_s(wchar_t* restrict s, rsize_t n, const wchar_t* restrict format,
                va_list arg);
int vswscanf_s(const wchar_t* restrict s, const wchar_t* restrict format, va_list arg);
int vwprintf_s(const wchar_t* restrict format, va_list arg);
int vwscanf_s(const wchar_t* restrict format, va_list arg);
int wprintf_s(const wchar_t* restrict format, ...);
int wscanf_s(const wchar_t* restrict format, ...);
errno_t wcscpy_s(wchar_t* restrict s1, rsize_t s1max, const wchar_t* restrict s2);
errno_t wcsncpy_s(wchar_t* restrict s1, rsize_t s1max, const wchar_t* restrict s2,
                  rsize_t n);
errno_t wmemcpy_s(wchar_t* restrict s1, rsize_t s1max, const wchar_t* restrict s2,
                  rsize_t n);
errno_t wmemmove_s(wchar_t* s1, rsize_t s1max, const wchar_t* s2, rsize_t n);
errno_t wcscat_s(wchar_t* restrict s1, rsize_t s1max, const wchar_t* restrict s2);
errno_t wcsncat_s(wchar_t* restrict s1, rsize_t s1max, const wchar_t* restrict s2,
                  rsize_t n);
wchar_t* wcstok_s(wchar_t* restrict s1, rsize_t* restrict s1max,
                  const wchar_t* restrict s2, wchar_t** restrict ptr);
size_t wcsnlen_s(const wchar_t* s, size_t maxsize);
errno_t wcrtomb_s(size_t* restrict retval, char* restrict s, rsize_t smax, wchar_t wc,
                  mbstate_t* restrict ps);
errno_t mbsrtowcs_s(size_t* restrict retval, wchar_t* restrict dst, rsize_t dstmax,
                    const char** restrict src, rsize_t len, mbstate_t* restrict ps);
errno_t wcsrtombs_s(size_t* restrict retval, char* restrict dst, rsize_t dstmax,
                    const wchar_t** restrict src, rsize_t len, mbstate_t* restrict ps);
#endif
```