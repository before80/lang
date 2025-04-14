+++
title = "<inttypes.h>"
date = 2025-04-14T09:58:11+08:00
weight = 80
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/inttypes](https://zh.cppreference.com/w/c/header/inttypes)

​	此标头是[类型支持](https://zh.cppreference.com/w/c/types)库的一部分，特别是，它是[整数类型格式转换](https://zh.cppreference.com/w/c/types/integer#.E6.A0.BC.E5.BC.8F.E5.AE.8F.E5.B8.B8.E9.87.8F)接口的一部分。

> 本节未完成 
>
> 原因：Add macros from B.7. Format conversion of integer types <inttypes.h>

## 概要

```c
intmax_t imaxabs(intmax_t j);
imaxdiv_t imaxdiv(intmax_t numer, intmax_t denom);
intmax_t strtoimax(const char* restrict nptr, char** restrict endptr, int base);
uintmax_t strtoumax(const char* restrict nptr, char** restrict endptr, int base);
intmax_t wcstoimax(const wchar_t* restrict nptr, wchar_t** restrict endptr, int base);
uintmax_t wcstoumax(const wchar_t* restrict nptr, wchar_t** restrict endptr, int base);
```