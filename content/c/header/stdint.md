+++
title = "<stdint.h>"
date = 2025-04-14T14:48:27+08:00
weight = 210
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdint](https://zh.cppreference.com/w/c/header/stdint)

​	本标头是[类型支持]({{< ref "/c/types" >}})库的一部分，提供[定宽整数类型]({{< ref "/c/types/integer#.E7.B1.BB.E5.9E.8B" >}})，且是[数值极限]({{< ref "/c/types/limits#.E5.BA.93.E7.B1.BB.E5.9E.8B.E5.88.AB.E5.90.8D.E7.9A.84.E6.9E.81.E9.99.90" >}})接口的一部分。

> 本节未完成 
>
> 原因：7.22 Integer types <stdint.h>, copy/share parts of [c/types/integer]({{< ref "/c/types/integer" >}}) and [c/types/limits]({{< ref "/c/types/limits" >}})

## 概要

> 本节未完成 
>
> 原因：B.21 Integer types <stdint.h>

```c
typedef /*signed-integer-type*/     int8_t         ; // 可选
typedef /*signed-integer-type*/     int16_t        ; // 可选
typedef /*signed-integer-type*/     int32_t        ; // 可选
typedef /*signed-integer-type*/     int64_t        ; // 可选
typedef /* 见描述 */                 intN_t         ; // 可选，见描述
 
typedef /*signed-integer-type*/     int_fast8_t    ;
typedef /*signed-integer-type*/     int_fast16_t   ;
typedef /*signed-integer-type*/     int_fast32_t   ;
typedef /*signed-integer-type*/     int_fast64_t   ;
typedef /* 见描述 */                 int_fastN_t    ; // 可选，见描述
 
typedef /*signed-integer-type*/     int_least8_t   ;
typedef /*signed-integer-type*/     int_least16_t  ;
typedef /*signed-integer-type*/     int_least32_t  ;
typedef /*signed-integer-type*/     int_least64_t  ;
typedef /* 见描述 */                 int_leastN_t   ; // 可选，见描述
 
typedef /*signed-integer-type*/     intmax_t       ;
typedef /*signed-integer-type*/     intptr_t       ; // 可选
 
typedef /*unsigned-integer-type*/   uint8_t        ; // 可选
typedef /*unsigned-integer-type*/   uint16_t       ; // 可选
typedef /*unsigned-integer-type*/   uint32_t       ; // 可选
typedef /*unsigned-integer-type*/   uint64_t       ; // 可选
typedef /* 见描述 */                 uintN_t        ; // 可选，见描述
 
typedef /*unsigned-integer-type*/   uint_fast8_t   ;
typedef /*unsigned-integer-type*/   uint_fast16_t  ;
typedef /*unsigned-integer-type*/   uint_fast32_t  ;
typedef /*unsigned-integer-type*/   uint_fast64_t  ;
typedef /* 见描述 */                 uint_fastN_t   ; // 可选，见描述
 
typedef /*unsigned-integer-type*/   uint_least8_t  ;
typedef /*unsigned-integer-type*/   uint_least16_t ;
typedef /*unsigned-integer-type*/   uint_least32_t ;
typedef /*unsigned-integer-type*/   uint_least64_t ;
typedef /* 见描述 */                 uint_leastN_t  ; // 可选，见描述
 
typedef /*unsigned-integer-type*/   uintmax_t      ;
typedef /*unsigned-integer-type*/   uintptr_t      ; // 可选
 
#define INTN_MIN         /* 见描述 */
#define INTN_MAX         /* 见描述 */
#define UINTN_MAX        /* 见描述 */
 
#define INT_FASTN_MIN    /* 见描述 */
#define INT_FASTN_MAX    /* 见描述 */
#define UINT_FASTN_MAX   /* 见描述 */
 
#define INT_LEASTN_MIN   /* 见描述 */
#define INT_LEASTN_MAX   /* 见描述 */
#define UINT_LEASTN_MAX  /* 见描述 */
 
#define INTMAX_MIN       /* 见描述 */
#define INTMAX_MAX       /* 见描述 */
#define UINTMAX_MAX      /* 见描述 */
 
#define INTPTR_MIN       /* 见描述 */        // 可选
#define INTPTR_MAX       /* 见描述 */        // 可选
#define UINTPTR_MAX      /* 见描述 */        // 可选
 
#define PTRDIFF_MIN      /* 见描述 */
#define PTRDIFF_MAX      /* 见描述 */
#define SIZE_MAX         /* 见描述 */
 
#define SIG_ATOMIC_MIN   /* 见描述 */
#define SIG_ATOMIC_MAX   /* 见描述 */
 
#define WCHAR_MIN        /* 见描述 */
#define WCHAR_MAX        /* 见描述 */
 
#define WINT_MIN         /* 见描述 */
#define WINT_MAX         /* 见描述 */
 
#define INTN_C(value)    /* 见描述 */
#define UINTN_C(value)   /* 见描述 */
#define INTMAX_C(value)  /* 见描述 */
#define UINTMAX_C(value) /* 见描述 */
```

​	仅当实现定义了 `__STDC_LIB_EXT1__`，而且用户代码在对 `stdint.h` 的所有包含之前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#if defined(__STDC_WANT_LIB_EXT1__)
#define RSIZE_MAX /* 见描述 */
#endif
```
