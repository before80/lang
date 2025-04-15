+++
title = "并发支持库"
date = 2025-04-15T19:26:00+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文[https://zh.cppreference.com/w/c/thread](https://zh.cppreference.com/w/c/thread)

​	C 提供线程、原子操作、互斥、条件变量及线程特定存储的内建支持。

​	这些特性是可选地提供的：

- 若编译器定义宏常量 `__STDC_NO_THREADS__`，则不提供头文件 [`<threads.h>`](https://zh.cppreference.com/w/c/header/threads) 及所有在其中提供的名称；
- 若编译器定义宏常量 `__STDC_NO_ATOMICS__`，则不提供头文件 [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) 及所有在其中提供的名称。

​	另见 [`_Atomic` 类型说明符和限定符](https://zh.cppreference.com/w/c/language/atomic)。

## 线程

| 在标头 `<threads.h>` 定义                                    |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `thrd_t`                                                     | 实现定义的标识线程的完整对象类型                             |
| [thrd_create (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_create) | 创建线程 (函数)                                              |
| [thrd_equal (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_equal) | 检查两个标识符是否表示同一线程 (函数)                        |
| [thrd_current (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_current) | 获取当前线程标识符 (函数)                                    |
| [thrd_sleep (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_sleep) | 在给定的时间段内挂起调用方线程的执行 (函数)                  |
| [thrd_yield (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_yield) | 让出当前时间片段 (函数)                                      |
| [thrd_exit (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_exit) | 终止调用方线程 (函数)                                        |
| [thrd_detach (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_detach) | 分离线程 (函数)                                              |
| [thrd_join (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_join) | 阻塞到线程终止为止 (函数)                                    |
| [thrd_success (C11)<br />thrd_timedout (C11)<br />thrd_busy<br />thrd_nomem<br />thrd_error<br />](https://zh.cppreference.com/w/c/thread/thrd_errors) | 指示线程错误状态 (常量)                                      |
| thrd_start_t (C11)<br />                                     | 函数指针类型 `int(*)(void*)` 的 typedef，为 [thrd_create](http://zh.cppreference.com/w/c/thread/thrd_create) 所用 (typedef) |

## 原子操作

| 在标头 `<stdatomic.h>` 定义 |
| ----------------------------- |

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

### 标志类型及操作

| [atomic_flag (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag) | 免锁原子布尔标志 (结构体)                      |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [atomic_flag_test_and_set (C11)<br />atomic_flag_test_and_set_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set) | 设置 `atomic_flag` 为 `true` 并返回旧值 (函数) |
| [atomic_flag_clear (C11)<br />atomic_flag_clear_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear) | 设置 `atomic_flag` 为 `false` (函数)           |

### 初始化

| [atomic_init (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_init) | 初始化既存的原子对象 (函数)                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ATOMIC_VAR_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_VAR_INIT) | 初始化新的原子对象 (宏函数)                                  |
| [ATOMIC_FLAG_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_FLAG_INIT) | 初始化新的 [atomic_flag](http://zh.cppreference.com/w/c/atomic/atomic_flag) (宏常量) |

### 内存同步顺序

| [memory_order (C11)<br />](https://zh.cppreference.com/w/c/atomic/memory_order) | 定义内存顺序制约 (枚举)                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [kill_dependency (C11)<br />](https://zh.cppreference.com/w/c/atomic/kill_dependency) | 打破 [memory_order_consume](http://zh.cppreference.com/w/c/atomic/memory_order) 的依赖链 (宏函数) |
| [atomic_thread_fence (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) | 通用的内存顺序依赖的栅栏同步原语 (函数)                      |
| [atomic_signal_fence (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_signal_fence) | 线程与执行于同一线程的信号处理函数间的栅栏 (函数)            |



### 便利类型别名

| typedef 名                    | 完整类型名                                                   |
| ----------------------------- | ------------------------------------------------------------ |
| `atomic_bool` (C11)           | _Atomic _Bool(C23 前)_Atomic bool(C23 起)                    |
| `atomic_char` (C11)           | _Atomic char                                                 |
| `atomic_schar` (C11)          | _Atomic signed char                                          |
| `atomic_uchar` (C11)          | _Atomic unsigned char                                        |
| `atomic_short` (C11)          | _Atomic short                                                |
| `atomic_ushort` (C11)         | _Atomic unsigned short                                       |
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
| `atomic_intmax_t` (C11)       | _Atomic [intmax_t](http://zh.cppreference.com/w/c/types/integer) |
| `atomic_uintmax_t` (C11)      | _Atomic [uintmax_t](http://zh.cppreference.com/w/c/types/integer) |

## 互斥

| 在标头 `<threads.h>` 定义                                    |                                           |
| ------------------------------------------------------------ | ----------------------------------------- |
| `**mtx_t**`                                                  | 互斥体标识符                              |
| [mtx_init (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_init) | 创建互斥体 (函数)                         |
| [mtx_lock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_lock) | 阻塞到锁定互斥体为止 (函数)               |
| [mtx_timedlock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_timedlock) | 阻塞到锁定互斥体或超时为止 (函数)         |
| [mtx_trylock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_trylock) | 锁定互斥体，若已锁定则返回而不阻塞 (函数) |
| [mtx_unlock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_unlock) | 解锁互斥体 (函数)                         |
| [mtx_destroy (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_destroy) | 销毁互斥体 (函数)                         |
| [mtx_plain (C11)<br />mtx_recursive (C11)<br />mtx_timed (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_types) | 定义互斥体的类型 (枚举)                   |

### 一次调用

| [call_once (C11)<br />](https://zh.cppreference.com/w/c/thread/call_once) | 对一个函数恰好调用一次 (函数) |
| ------------------------------------------------------------ | ----------------------------- |

## 条件变量

| 在标头 `<threads.h>` 定义                                  |                                       |
| ------------------------------------------------------------ | ------------------------------------- |
| `**cnd_t**`                                                  | 条件变量标识符                        |
| [cnd_init (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_init) | 创建条件变量 (函数)                   |
| [cnd_signal (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_signal) | 除阻阻塞于条件变量上的一个线程 (函数) |
| [cnd_broadcast (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_broadcast) | 除阻所有阻塞于条件变量上的线程 (函数) |
| [cnd_wait (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_wait) | 在条件变量上阻塞 (函数)               |
| [cnd_timedwait (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_timedwait) | 在条件变量上阻塞一段时长 (函数)       |
| [cnd_destroy (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_destroy) | 销毁条件变量 (函数)                   |

## 线程局域存储

| 在标头 `<threads.h>` 定义                                    |                                                          |
| ------------------------------------------------------------ | -------------------------------------------------------- |
| [thread_local (C11)<br />](https://zh.cppreference.com/w/c/thread/thread_local) | 存储类说明符 `_Thread_local` 的便利宏 (关键词宏)         |
| `**tss_t**`                                                  | 线程特定存储的指针                                       |
| [TSS_DTOR_ITERATIONS (C11)<br />](https://zh.cppreference.com/w/c/thread/TSS_DTOR_ITERATIONS) | 析构器被调用的最大次数 (宏常量)                          |
| tss_dtor_t (C11)<br />                                       | 函数指针类型 `void(*)(void*)`，用作 TSS 析构器 (typedef) |
| [tss_create (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_create) | 以给定的析构器，创建线程特定存储指针 (函数)              |
| [tss_get (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_get) | 从线程特定存储读取 (函数)                                |
| [tss_set (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_set) | 写入线程特定存储 (函数)                                  |
| [tss_delete (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_delete) | 释放给定的线程特定存储指针所保有的资源 (函数)            |

## 保留标识符

​	在 C 标准的未来修订中：

- 以 `cnd_`、`mtx_`、`thrd_` 或 `tss_` 带一个小写字母开始的函数名、类型名与枚举常量可能添加到 `<threads.h>` 头文件中的声明；
- 以 `ATOMIC_` 带一个大写字母开始的宏名可能添加到 [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) 头文件中的宏定义；
- 以 `atomic_` 或 `memory_` 带一个小写字母开始的 typedef 名可能添加到 [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) 头文件中的声明；
- 以 `memory_order_` 带一个小写字母开始的枚举常量可能添加到 [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) 头文件中的 [memory_order](https://zh.cppreference.com/w/c/atomic/memory_order) 类型的定义；
- 以 `atomic_` 带一个小写字母开始的函数名可能添加到 [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) 头文件。

​	为函数名保留的表示符始终潜在地(C23 起)对作为带外部链接的标识符的使用保留，而此处列出的其他标识符在包含 [`<stdatomic.h>`](https://zh.cppreference.com/w/c/header/stdatomic) 时潜在地(C23 起)被保留。

​	声明、定义或 #undef 这种标识符导致未定义行为，若标准或实现提供它(C23 起)。可移植的程序不应使用这些标识符。

## 参阅

​	**并发支持库**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/thread)**

## 外部链接

​	[GNU GCC Libc Manual: ISO C Mutexes](https://www.gnu.org/software/libc/manual/html_node/ISO-C-Mutexes.html)