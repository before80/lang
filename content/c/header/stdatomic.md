+++
title = "<stdatomic.h>"
date = 2025-04-14T14:39:30+08:00
weight = 160
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/stdatomic](https://zh.cppreference.com/w/c/header/stdatomic)

​	此标头提供[原子操作](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)，特别是，它是[并发支持](https://zh.cppreference.com/w/c/thread)库的一部分。

## 原子操作

### 原子类型上的操作

| [ATOMIC_BOOL_LOCK_FREE (C11)<br />ATOMIC_CHAR_LOCK_FREE (C11)<br />ATOMIC_CHAR16_T_LOCK_FREE<br />ATOMIC_CHAR32_T_LOCK_FREE<br />ATOMIC_WCHAR_T_LOCK_FREE<br />ATOMIC_SHORT_LOCK_FREE<br />ATOMIC_INT_LOCK_FREE<br />ATOMIC_LONG_LOCK_FREE<br />ATOMIC_LLONG_LOCK_FREE<br />ATOMIC_POINTER_LOCK_FREE<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts) | 指示给定的原子类型为免锁 (宏常量)                            |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [atomic_is_lock_free (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_is_lock_free) | 指示原子对象是否免锁 (函数)                                  |
| [atomic_store (C11)<br />atomic_store_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_store) | 存储值到原子对象 (函数)                                      |
| [atomic_load (C11)<br />atomic_load_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_load) | 从原子对象读取值 (函数)                                      |
| [atomic_exchange (C11)<br />atomic_exchange_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_exchange) | 将原子对象的值与一个值交换 (函数)                            |
| [atomic_compare_exchange_strong (C11)<br />atomic_compare_exchange_strong_explicit (C11)<br />atomic_compare_exchange_weak<br />atomic_compare_exchange_weak_explicit<br />](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange) | 若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值 (函数) |
| [atomic_fetch_add (C11)<br />atomic_fetch_add_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_add) | 原子加法 (函数)                                              |
| [atomic_fetch_sub (C11)<br />atomic_fetch_sub_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub) | 原子减法 (函数)                                              |
| [atomic_fetch_or (C11)<br />atomic_fetch_or_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or) | 原子逐位或（OR） (函数)                                      |
| [atomic_fetch_xor (C11)<br />atomic_fetch_xor_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor) | 原子逐位异或（XOR） (函数)                                   |
| [atomic_fetch_and (C11)<br />atomic_fetch_and_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and) | 原子逐位与（AND） (函数)                                     |

### 标志类型与操作

| [atomic_flag (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag) | 免锁原子布尔标志 (结构体)                      |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [atomic_flag_test_and_set (C11)<br />atomic_flag_test_and_set_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set) | 设置 `atomic_flag` 为 `true` 并返回旧值 (函数) |
| [atomic_flag_clear (C11)<br />atomic_flag_clear_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear) | 设置 `atomic_flag` 为 `false` (函数)           |

### 初始化

| [atomic_init (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_init) | 初始化既存的原子对象 (函数)                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ATOMIC_VAR_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_VAR_INIT) | 初始化新的原子对象 (宏函数)                                  |
| [ATOMIC_FLAG_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_FLAG_INIT) | 初始化新的 [atomic_flag](http://zh.cppreference.com/w/c/atomic/atomic_flag) (宏常量) |

### 内存同步定序

| [memory_order (C11)<br />](https://zh.cppreference.com/w/c/atomic/memory_order) | 定义内存顺序制约 (枚举)                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [kill_dependency (C11)<br />](https://zh.cppreference.com/w/c/atomic/kill_dependency) | 打破 [memory_order_consume](http://zh.cppreference.com/w/c/atomic/memory_order) 的依赖链 (宏函数) |
| [atomic_thread_fence (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) | 通用的内存顺序依赖的栅栏同步原语 (函数)                      |
| [atomic_signal_fence (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_signal_fence) | 线程与执行于同一线程的信号处理函数间的栅栏 (函数)            |



### 便利类型别名

| typedef 名                    | 完整类型名                                                   |
| ----------------------------- | ------------------------------------------------------------ |
| `atomic_bool` (C11)           | `_Atomic` _Bool                                              |
| `atomic_char` (C11)           | `_Atomic` char                                               |
| `atomic_schar` (C11)          | `_Atomic` signed char                                        |
| `atomic_uchar` (C11)          | `_Atomic` unsigned char                                      |
| `atomic_short` (C11)          | `_Atomic` short                                              |
| `atomic_ushort` (C11)         | `_Atomic` unsigned short                                     |
| `atomic_int` (C11)            | _Atomic int                                                  |
| `atomic_uint` (C11)           | _Atomic unsigned int                                         |
| `atomic_long` (C11)           | _Atomic long                                                 |
| `atomic_ulong` (C11)          | _Atomic unsigned long                                        |
| `atomic_llong` (C11)          | _Atomic long long                                            |
| `atomic_ullong` (C11)         | _Atomic unsigned long long                                   |
| `atomic_char8_t` (C23)        | _Atomic char8_t                                              |
| `atomic_char16_t` (C11)       | _Atomic char16_t                                             |
| `atomic_char32_t` (C11)       | _Atomic char32_t                                             |
| `atomic_wchar_t` (C11)        | _Atomic wchar_t                                              |
| `atomic_int_least8_t` (C11)   | _Atomic [int_least8_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_least8_t` (C11)  | _Atomic [uint_least8_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_least16_t` (C11)  | _Atomic [int_least16_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_least16_t` (C11) | _Atomic [uint_least16_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_least32_t` (C11)  | _Atomic [int_least32_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_least32_t` (C11) | _Atomic [uint_least32_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_least64_t` (C11)  | _Atomic [int_least64_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_least64_t` (C11) | _Atomic [uint_least64_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_fast8_t` (C11)    | _Atomic [int_fast8_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_fast8_t` (C11)   | _Atomic [uint_fast8_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_fast16_t` (C11)   | _Atomic [int_fast16_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_fast16_t` (C11)  | _Atomic [uint_fast16_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_fast32_t` (C11)   | _Atomic [int_fast32_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_fast32_t` (C11)  | _Atomic [uint_fast32_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_int_fast64_t` (C11)   | _Atomic [int_fast64_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uint_fast64_t` (C11)  | _Atomic [uint_fast64_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_intptr_t` (C11)       | _Atomic [intptr_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uintptr_t` (C11)      | _Atomic [uintptr_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_size_t` (C11)         | _Atomic [size_t](http://zh.cppreference.com/w/c/types/size_t) |
| `atomic_ptrdiff_t` (C11)      | _Atomic [ptrdiff_t](http://zh.cppreference.com/w/c/types/ptrdiff_t) |
| `atomic_intmax_t` (C11)       | `_Atomic` [intmax_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uintmax_t` (C11)      | _Atomic [uintmax_t](http://zh.cppreference.com/w/c/types/integer) |

## 概要

> 本节未完成 
>
> 原因：add more from 7.17 Atomics <stdatomic.h> and B.16 Atomics <stdatomic.h>

```c
#define __STDC_VERSION_STDATOMIC_H__ 202311L
 
void atomic_init(volatile A* obj, /*C*/ value);
/*type*/ kill_dependency(/*type*/ y);
void atomic_thread_fence(memory_order order);
void atomic_signal_fence(memory_order order);
bool atomic_is_lock_free(const volatile A* obj);
void atomic_store(volatile A* object, /*C*/ desired);
void atomic_store_explicit(volatile A* object, /*C*/ desired, memory_order order);
/*C*/ atomic_load(const volatile A* object);
/*C*/ atomic_load_explicit(const volatile A* object, memory_order order);
/*C*/ atomic_exchange(volatile A* object, /*C*/ desired);
/*C*/ atomic_exchange_explicit(volatile A* object, /*C*/ desired, memory_order order);
bool atomic_compare_exchange_strong(volatile A* object, /*C*/* expected, /*C*/ desired);
bool atomic_compare_exchange_strong_explicit(volatile A* object, /*C*/* expected,
/*C*/ desired, memory_order success, memory_order failure);
bool atomic_compare_exchange_weak(volatile A* object, /*C*/* expected, /*C*/ desired);
bool atomic_compare_exchange_weak_explicit(volatile A* object, /*C*/* expected,
/*C*/ desired, memory_order success, memory_order failure);
/*C*/ /*atomic_fetch_key*/(volatile A* object, M operand);
/*C*/ /*atomic_fetch_key_explicit*/(volatile A* object, M operand, memory_order order);
bool atomic_flag_test_and_set(volatile atomic_flag* object);
bool atomic_flag_test_and_set_explicit(volatile atomic_flag* object,
memory_order order);
void atomic_flag_clear(volatile atomic_flag* object);
void atomic_flag_clear_explicit(volatile atomic_flag* object,
                                memory_order order);
```