+++
title = "<threads.h> (C11)"
date = 2025-04-14T15:26:29+08:00
weight = 280
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/threads](https://zh.cppreference.com/w/c/header/threads)

​	此标头是[并发支持库](https://zh.cppreference.com/w/c/thread)的一部分，并提供了对线程、互斥、条件变量和线程专有存储的支持。

## 线程

| `thrd_t`                                                     | 实现定义的标识线程的完整对象类型                             |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [thrd_create (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_create) | 创建线程 (函数)                                              |
| [thrd_equal (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_equal) | 检查两个标识符是否表示同一线程 (函数)                        |
| [thrd_current (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_current) | 获取当前线程标识符 (函数)                                    |
| [thrd_sleep (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_sleep) | 在给定的时间段内挂起调用方线程的执行 (函数)                  |
| [thrd_yield (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_yield) | 让出当前时间片段 (函数)                                      |
| [thrd_exit (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_exit) | 终止调用方线程 (函数)                                        |
| [thrd_detach (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_detach) | 分离线程 (函数)                                              |
| [thrd_join (C11)<br />](https://zh.cppreference.com/w/c/thread/thrd_join) | 阻塞到线程终止为止 (函数)                                    |
| [thrd_success (C11)<br />thrd_timedout (C11)<br />thrd_busy<br />thrd_nomem<br />thrd_error<br />](https://zh.cppreference.com/w/c/thread/thrd_errors) | 指示线程错误状态 (常量)                                      |
| thrd_start_t (C11)<br />                                     | 函数指针类型 int(*)(void*) 的 typedef，为 [thrd_create](http://zh.cppreference.com/w/c/thread/thrd_create) 所用 (typedef) |

## 互斥

| `mtx_t`                                                      | 互斥体标识符                              |
| ------------------------------------------------------------ | ----------------------------------------- |
| [mtx_init (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_init) | 创建互斥体 (函数)                         |
| [mtx_lock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_lock) | 阻塞到锁定互斥体为止 (函数)               |
| [mtx_timedlock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_timedlock) | 阻塞到锁定互斥体或超时为止 (函数)         |
| [mtx_trylock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_trylock) | 锁定互斥体，若已锁定则返回而不阻塞 (函数) |
| [mtx_unlock (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_unlock) | 解锁互斥体 (函数)                         |
| [mtx_destroy (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_destroy) | 销毁互斥体 (函数)                         |
| [mtx_plain (C11)<br />mtx_recursive (C11)<br />mtx_timed (C11)<br />](https://zh.cppreference.com/w/c/thread/mtx_types) | 定义互斥体的类型 (枚举)                   |

### 单次调用

| [call_once (C11)<br />](https://zh.cppreference.com/w/c/thread/call_once) | 对一个函数恰好调用一次 (函数) |
| ------------------------------------------------------------ | ----------------------------- |

## 条件变量

| `cnd_t`                                                      | 条件变量标识符                        |
| ------------------------------------------------------------ | ------------------------------------- |
| [cnd_init (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_init) | 创建条件变量 (函数)                   |
| [cnd_signal (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_signal) | 除阻阻塞于条件变量上的一个线程 (函数) |
| [cnd_broadcast (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_broadcast) | 除阻所有阻塞于条件变量上的线程 (函数) |
| [cnd_wait (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_wait) | 在条件变量上阻塞 (函数)               |
| [cnd_timedwait (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_timedwait) | 在条件变量上阻塞一段时长 (函数)       |
| [cnd_destroy (C11)<br />](https://zh.cppreference.com/w/c/thread/cnd_destroy) | 销毁条件变量 (函数)                   |

## 线程局部存储

| [thread_local (C11)<br />](https://zh.cppreference.com/w/c/thread/thread_local) | 存储类说明符 _Thread_local 的便利宏 (关键词宏)         |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| `tss_t`                                                      | 线程特定存储的指针                                     |
| [TSS_DTOR_ITERATIONS (C11)<br />](https://zh.cppreference.com/w/c/thread/TSS_DTOR_ITERATIONS) | 析构器被调用的最大次数 (宏常量)                        |
| tss_dtor_t (C11)<br />                                       | 函数指针类型 void(*)(void*)，用作 TSS 析构器 (typedef) |
| [tss_create (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_create) | 以给定的析构器，创建线程特定存储指针 (函数)            |
| [tss_get (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_get) | 从线程特定存储读取 (函数)                              |
| [tss_set (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_set) | 写入线程特定存储 (函数)                                |
| [tss_delete (C11)<br />](https://zh.cppreference.com/w/c/thread/tss_delete) | 释放给定的线程特定存储指针所保有的资源 (函数)          |

### 概要

```c
#define __STDC_NO_THREADS__ 202311L
 
#define ONCE_FLAG_INIT      /* 见描述 */
#define TSS_DTOR_ITERATIONS /* 见描述 */
 
typedef /* 见描述 */ cnd_t;
typedef /* 见描述 */ thrd_t;
typedef /* 见描述 */ tss_t;
typedef /* 见描述 */ mtx_t;
typedef /* 见描述 */ tss_dtor_t;
typedef /* 见描述 */ thrd_start_t;
 
#define mtx_plain     /* 见描述 */
#define mtx_recursive /* 见描述 */
#define mtx_timed     /* 见描述 */
#define once_flag     /* 见描述 */
#define thrd_busy     /* 见描述 */
#define thrd_error    /* 见描述 */
#define thrd_nomem    /* 见描述 */
#define thrd_success  /* 见描述 */
#define thrd_timedout /* 见描述 */
 
void call_once(once_flag* flag, void (*func)(void));
int cnd_broadcast(cnd_t* cond);
void cnd_destroy(cnd_t* cond);
int cnd_init(cnd_t* cond);
int cnd_signal(cnd_t* cond);
int cnd_timedwait(cnd_t* restrict cond, mtx_t* restrict mtx,
const struct timespec* restrict ts);
int cnd_wait(cnd_t* cond, mtx_t* mtx);
void mtx_destroy(mtx_t* mtx);
int mtx_init(mtx_t* mtx, int type);
int mtx_lock(mtx_t* mtx);
int mtx_timedlock(mtx_t* restrict mtx, const struct timespec* restrict ts);
int mtx_trylock(mtx_t* mtx);
int mtx_unlock(mtx_t* mtx);
int thrd_create(thrd_t* thr, thrd_start_t func, void* arg);
thrd_t thrd_current(void);
int thrd_detach(thrd_t thr);
int thrd_equal(thrd_t thr0, thrd_t thr1);
[[noreturn]] void thrd_exit(int res);
int thrd_join(thrd_t thr, int* res);
int thrd_sleep(const struct timespec* duration, struct timespec* remaining);
void thrd_yield(void);
int tss_create(tss_t* key, tss_dtor_t dtor);
void tss_delete(tss_t key);
void* tss_get(tss_t key);
int tss_set(tss_t key, void* val);
```