+++
title = "<stdlib.h>"
date = 2025-04-14T14:50:10+08:00
weight = 230
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdlib](https://zh.cppreference.com/w/c/header/stdlib)

​	此标头是[程序支持工具](https://zh.cppreference.com/w/c/program)库的一部分，特别是，它提供用于程序终止、[内存管理](https://zh.cppreference.com/w/c/memory)、[字符串转换](https://zh.cppreference.com/w/c/string)、[随机数](https://zh.cppreference.com/w/c/numeric/random)生成的函数。此标头还提供了一些[算法](https://zh.cppreference.com/w/c/algorithm)。

## 函数

| [abort](https://zh.cppreference.com/w/c/program/abort)       | 引发非正常的程序终止（不清理） (函数)                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [exit](https://zh.cppreference.com/w/c/program/exit)         | 引发正常的程序终止并清理 (函数)                              |
| [quick_exit](https://zh.cppreference.com/w/c/program/quick_exit)(C11) | 引发正常的程序终止但不完全清理 (函数)                        |
| [_Exit](https://zh.cppreference.com/w/c/program/_Exit)(C99)  | 引发正常的程序终止但不清理 (函数)                            |
| [atexit](https://zh.cppreference.com/w/c/program/atexit)     | 注册一个要在调用 [`exit()`](https://zh.cppreference.com/w/c/program/exit) 时调用的函数 (函数) |
| [at_quick_exit](https://zh.cppreference.com/w/c/program/at_quick_exit)(C11) | 注册要在调用 [`quick_exit`](https://zh.cppreference.com/w/c/program/quick_exit) 时调用的函数 (函数) |
| [EXIT_SUCCESSEXIT_FAILURE](https://zh.cppreference.com/w/c/program/EXIT_status) | 表示程序的执行结果 (宏常量)                                  |

> 本节未完成 
>
> 原因：Add more from 7.24 General utilities <stdlib.h>

## 概要

> 本节未完成 
>
> 原因：Add more from B.23 General utilities <stdlib.h>

```c
#define __STDC_VERSION_STDLIB_H__ 202311L
 
// TODO: types and macros
 
void call_once(once_flag* flag, void (*func)(void));
double atof(const char* nptr);
int atoi(const char* nptr);
long int atol(const char* nptr);
long long int atoll(const char* nptr);
int strfromd(char* restrict s, size_t n, const char* restrict format, double fp);
int strfromf(char* restrict s, size_t n, const char* restrict format, float fp);
int strfroml(char* restrict s, size_t n, const char* restrict format, long double fp);
double strtod(const char* restrict nptr, char** restrict endptr);
float strtof(const char* restrict nptr, char** restrict endptr);
long double strtold(const char* restrict nptr, char** restrict endptr);
long int strtol(const char* restrict nptr, char** restrict endptr, int base);
long long int strtoll(const char* restrict nptr, char** restrict endptr, int base);
unsigned long int strtoul(const char* restrict nptr, char** restrict endptr, int base);
unsigned long long int strtoull(const char* restrict nptr,
                                char** restrict endptr, int base);
int rand(void);
void srand(unsigned int seed);
void* aligned_alloc(size_t alignment, size_t size);
void* calloc(size_t nmemb, size_t size);
void free(void* ptr);
void free_sized(void* ptr, size_t size);
void free_aligned_sized(void* ptr, size_t alignment, size_t size);
void* malloc(size_t size);
void* realloc(void* ptr, size_t size);
[[noreturn]] void abort(void);
int atexit(void (*func)(void));
int at_quick_exit(void (*func)(void));
[[noreturn]] void exit(int status);
[[noreturn]] void _Exit(int status);
char* getenv(const char* name);
[[noreturn]] void quick_exit(int status);
int system(const char* string);
QVoid* bsearch(const void* key, QVoid* base, size_t nmemb, size_t size,
               int (*compar)(const void* , const void* ));
void qsort(void* base, size_t nmemb, size_t size,
           int (*compar)(const void* , const void* ));
int abs(int j);
long int labs(long int j);
long long int llabs(long long int j);
div_t div(int numer, int denom);
ldiv_t ldiv(long int numer, long int denom);
lldiv_t lldiv(long long int numer, long long int denom);
int mblen(const char* s, size_t n);
int mbtowc(wchar_t* restrict pwc, const char* restrict s, size_t n);
int wctomb(char* s, wchar_t wc);
size_t mbstowcs(wchar_t* restrict pwcs, const char* restrict s, size_t n);
size_t wcstombs(char* restrict s, const wchar_t* restrict pwcs, size_t n);
size_t memalignment(const void* p);
```

​	仅当实现定义了 `__STDC_IEC_60559_DFP__`：

```c
int strfromd32(char* restrict s, size_t n, const char* restrict format, _Decimal32 fp);
int strfromd64(char* restrict s, size_t n, const char* restrict format, _Decimal64 fp);
int strfromd128(char* restrict s, size_t n, const char* restrict format, _Decimal128 fp);
_Decimal32 strtod32(const char* restrict nptr, char** restrict endptr);
_Decimal64 strtod64(const char* restrict nptr, char** restrict endptr);
_Decimal128 strtod128(const char* restrict nptr, char** restrict endptr);
```

​	仅当实现定义了 `__STDC_IEC_60559_TYPES__`，而且用户代码在对 `stdlib.h` 的所有包含之前定义了 `__STDC_WANT_IEC_60559_TYPES_EXT__`：

```c
#ifdef __STDC_WANT_IEC_60559_TYPES_EXT__
int strfromfN(char* restrict s, size_t n, const char* restrict format, _FloatN fp);
int strfromfNx(char* restrict s, size_t n, const char* restrict format, _FloatNx fp);
int strfromdN(char* restrict s, size_t n, const char* restrict format, _DecimalN fp);
int strfromdNx(char* restrict s, size_t n, const char* restrict format, _DecimalNx fp);
_FloatN strtofN(const char* restrict nptr, char** restrict endptr);
_FloatNx strtofNx(const char* restrict nptr, char** restrict endptr);
_DecimalN strtodN(const char* restrict nptr, char** restrict endptr);
_DecimalNx strtodNx(const char* restrict nptr, char** restrict endptr);
int strfromencfN(char* restrict s, size_t n, const char* restrict format,
                 const unsigned char encptr[restrict static N/8]);
int strfromencdecdN(char* restrict s, size_t n, const char* restrict format,
                    const unsigned char encptr[restrict static N/8]);
int strfromencbindN(char* restrict s, size_t n, const char* restrict format,
                    const unsigned char encptr[restrict static N/8]);
void strtoencfN(unsigned char encptr[restrict static N/8],
                const char* restrict nptr, char** restrict endptr);
void strtoencdecdN(unsigned char encptr[restrict static N/8],
                   const char* restrict nptr, char** restrict endptr);
void strtoencbindN(unsigned char encptr[restrict static N/8],
                   const char* restrict nptr, char** restrict endptr);
#endif
```

​	仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 `stdio.h` 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#if defined(__STDC_WANT_LIB_EXT1__)
constraint_handler_t set_constraint_handler_s(constraint_handler_t handler);
void abort_handler_s(const char* restrict msg, void* restrict ptr, errno_t error);
void ignore_handler_s(const char* restrict msg, void* restrict ptr, errno_t error);
errno_t getenv_s(size_t* restrict len, char* restrict value, rsize_t maxsize,
                 const char* restrict name);
QVoid* bsearch_s(const void* key, QVoid* base, rsize_t nmemb, rsize_t size,
                 int (*compar)(const void* k, const void* y, void* context),
                               void* context);
errno_t qsort_s(void* base, rsize_t nmemb, rsize_t size,
                int (*compar)(const void* x, const void* y, void* context),
                              void* context);
errno_t wctomb_s(int* restrict status, char* restrict s, rsize_t smax,
                 wchar_t wc);
errno_t mbstowcs_s(size_t* restrict retval, wchar_t* restrict dst, rsize_t dstmax,
                   const char* restrict src, rsize_t len);
errno_t wcstombs_s(size_t* restrict retval, char* restrict dst, rsize_t dstmax,
                   const wchar_t* restrict src, rsize_t len);
#endif
```