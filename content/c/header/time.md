+++
title = "<time.h>"
date = 2025-04-14T15:28:48+08:00
weight = 290
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://zh.cppreference.com/w/c/header/time](https://zh.cppreference.com/w/c/header/time)

​	此标头是[日期与时间工具](https://zh.cppreference.com/w/c/chrono)库的一部分。

## 函数

### 时间操纵

| [difftime<br />](https://zh.cppreference.com/w/c/chrono/difftime) | 计算时间差 (函数)                                 |
| ------------------------------------------------------------ | ------------------------------------------------- |
| [time<br />](https://zh.cppreference.com/w/c/chrono/time)    | 返回纪元开始经过的当前系统日历时间 (函数)         |
| [clock<br />](https://zh.cppreference.com/w/c/chrono/clock)  | 返回未加工的程序启动时开始经过的处理器时间 (函数) |
| [timespec_get (C11)<br />](https://zh.cppreference.com/w/c/chrono/timespec_get) | 返回基于给定时间基底的日历时间 (函数)             |
| [timespec_getres (C23)<br />](https://zh.cppreference.com/w/c/chrono/timespec_getres) | 返回基于给定时间基底的日历时间的分辨率 (函数)     |

### 格式转换

| [asctime (C23 弃用)<br />asctime_s (C23 弃用)<br />](https://zh.cppreference.com/w/c/chrono/asctime) | 将 `struct tm` 对象转换成文本表示 (函数)                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ctime (C23 弃用)<br />ctime_s (C23 弃用)<br />](https://zh.cppreference.com/w/c/chrono/ctime) | 将 `struct time_t` 对象转换成文本表示 (函数)                 |
| [strftime<br />](https://zh.cppreference.com/w/c/chrono/strftime) | 将 `struct tm` 对象转换成自定义文本表示 (函数)               |
| [gmtime <br />gmtime_r (C23)<br />gmtime_s (C23)<br />](https://zh.cppreference.com/w/c/chrono/gmtime) | 将从纪元开始的时间转换成以协调世界时（UTC）表示的日历时间 (函数) |
| [localtime <br />localtime_r (C23)<br />localtime_s (C23)<br />](https://zh.cppreference.com/w/c/chrono/localtime) | 将从纪元开始的时间转换成以本地时间表示的日历时间 (函数)      |
| [mktime<br />](https://zh.cppreference.com/w/c/chrono/mktime) | 将日历时间转换成纪元开始经过的时间 (函数)                    |

## 常量

| [CLOCKS_PER_SEC<br />](https://zh.cppreference.com/w/c/chrono/CLOCKS_PER_SEC) | 处理器每秒时钟滴答数 (宏常量) |
| ------------------------------------------------------------ | ----------------------------- |

## 类型

| [tm<br />](https://zh.cppreference.com/w/c/chrono/tm)        | 日历时间类型 (结构体)                |
| ------------------------------------------------------------ | ------------------------------------ |
| [time_t<br />](https://zh.cppreference.com/w/c/chrono/time_t) | 从纪元开始的日历时间类型 (typedef)   |
| [clock_t<br />](https://zh.cppreference.com/w/c/chrono/clock_t) | 从时点开始的处理器时间类型 (typedef) |
| [timespec (C11)<br />](https://zh.cppreference.com/w/c/chrono/timespec) | 单位为秒和纳秒的时间 (结构体)        |

## 概要

```c
#define __STDC_VERSION_TIME_H__ 202311L
 
#define NULL           /* 见描述 */
#define CLOCKS_PER_SEC /* 见描述 */
#define TIME_UTC       /* 见描述 */
 
typedef /* 见描述 */ clock_t;
typedef /* 见描述 */ size_t;
typedef /* 见描述 */ time_t;
 
struct timespec { /* 见描述 */ };
struct tm { /* 见描述 */ };
 
clock_t clock(void);
double difftime(time_t time1, time_t time0);
time_t mktime(struct tm* timeptr);
time_t timegm(struct tm* timeptr);
time_t time(time_t* timer);
int timespec_get(struct timespec* ts, int base);
int timespec_getres(struct timespec* ts, int base);
[[deprecated]] char* asctime(const struct tm* timeptr);
[[deprecated]] char* ctime(const time_t* timer);
struct tm* gmtime(const time_t* timer);
struct tm* gmtime_r(const time_t* timer, struct tm* buf);
struct tm* localtime(const time_t* timer);
struct tm* localtime_r(const time_t* timer, struct tm* buf);
size_t strftime(char* restrict s, size_t maxsize, const char* restrict format,
const struct tm* restrict timeptr);
```

​	仅当受实现支持：

```c
#define TIME_MONOTONIC /* 见描述 */
#define TIME_ACTIVE    /* 见描述 */
```

​	仅当支持线程且受实现支持：

```c
#define TIME_THREAD_ACTIVE /* 见描述 */
```

​	仅当实现定义了 `__STDC_LIB_EXT1__`，并且用户代码在对 **`<time.h>`** 的任何包含之前定义了 `__STDC_WANT_LIB_EXT1__`：

```c
#ifdef __STDC_WANT_LIB_EXT1__
typedef /* 见描述 */ errno_t;
typedef /* 见描述 */ rsize_t;
 
errno_t asctime_s(char* s, rsize_t maxsize, const struct tm* timeptr);
errno_t ctime_s(char* s, rsize_t maxsize, const time_t* timer);
struct tm* gmtime_s(const time_t* restrict timer, struct tm* restrict result);
struct tm* localtime_s(const time_t* restrict timer, struct tm* restrict result);
#endif
```
