+++
title = "<threads.h>"
date = 2025-04-15T16:56:20+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型








### cnd_t

原址：

```c
typedef /* 见描述 */ cnd_t;
```

​	条件变量标识符










### mtx_t

原址：

```c
typedef /* 见描述 */ mtx_t;
```

​	互斥体标识符










### thrd_start_t

原址：

```c
typedef /* 见描述 */ thrd_start_t;
```




### thrd_t

原址：

```c
typedef /* 见描述 */ thrd_t;
```




### tss_dtor_t

原址：

```c
typedef /* 见描述 */ tss_dtor_t;
```




### tss_t

原址：

```c
typedef /* 见描述 */ tss_t;
```

​	线程特定存储的指针



## 宏








### ONCE_FLAG_INIT <- 11+

原址：[https://zh.cppreference.com/w/c/thread/call_once](https://zh.cppreference.com/w/c/thread/call_once)

```c
void call_once( once_flag* flag, void (*func)(void) );// (1) (C11 起)
typedef /* 未指明 */ once_flag  //	(2)	(C11 起)
#define ONCE_FLAG_INIT /* 未指明 */ //(3)	(C11 起)
```

1) 调用函数 `func` 恰好一次，即使从多个线程调用。函数 `func` 的完成与先前或后继的用同一 `flag` 对象的对 `call_once` 调用同步。
2) 足以保有 `call_once` 所用标志的完整对象类型。
3) 展开成能用于初始化 `once_flag` 类型对象的值。

**参数**

| flag | -    | 指向用于确保只调用一次 `func` 的 `call_once` 对象的指针 |
| ---- | ---- | ------------------------------------------------------- |
| func | -    | 只执行一次的函数                                        |

**返回值**

（无）

**注意**

此函数的 POSIX 等价物是 [`pthread_once`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_once.html)。

**示例**



```c
#include <stdio.h>
#include <threads.h>
 
void do_once(void) {
    puts("called once");
}
 
static once_flag flag = ONCE_FLAG_INIT;
int func(void* data)
{
    call_once(&flag, do_once);
}
 
int main(void)
{
    thrd_t t1, t2, t3, t4;
    thrd_create(&t1, func, NULL);
    thrd_create(&t2, func, NULL);
    thrd_create(&t3, func, NULL);
    thrd_create(&t4, func, NULL);
 
    thrd_join(t1, NULL);
    thrd_join(t2, NULL);
    thrd_join(t3, NULL);
    thrd_join(t4, NULL);
}
```

输出：

```txt
called once
```




### TSS_DTOR_ITERATIONS <- 11+

原址：[https://zh.cppreference.com/w/c/thread/TSS_DTOR_ITERATIONS](https://zh.cppreference.com/w/c/thread/TSS_DTOR_ITERATIONS)

```c
#define TSS_DTOR_ITERATIONS /* 未指明 */
(C11 起)
```

​	展开成正的整数 [常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它定义 [thrd_exit](https://zh.cppreference.com/w/c/thread/thrd_exit) 将对线程局域存储指针调用析构器的最大次数。

​	此常量等价于 POSIX 的 `PTHREAD_DESTRUCTOR_ITERATIONS`。










### mtx_plain <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_types](https://zh.cppreference.com/w/c/thread/mtx_types)

```c
// (C11 起)
enum {
    mtx_plain = /* 未指明 */,
    mtx_recursive = /* 未指明 */,
    mtx_timed = /* 未指明 */
};
```

​	定义互斥体的类型

​	传递给 [mtx_init](https://zh.cppreference.com/w/c/thread/mtx_init) 时，标识要创建的互斥体类型。

| 常量            | 解释       |
| --------------- | ---------- |
| `mtx_plain`     | 平常互斥体 |
| `mtx_recursive` | 递归互斥体 |
| `mtx_timed`     | 定时互斥体 |








### mtx_recursive <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_types](https://zh.cppreference.com/w/c/thread/mtx_types)

```c
// (C11 起)
enum {
    mtx_plain = /* 未指明 */,
    mtx_recursive = /* 未指明 */,
    mtx_timed = /* 未指明 */
};
```

​	定义互斥体的类型

​	传递给 [mtx_init](https://zh.cppreference.com/w/c/thread/mtx_init) 时，标识要创建的互斥体类型。

| 常量            | 解释       |
| --------------- | ---------- |
| `mtx_plain`     | 平常互斥体 |
| `mtx_recursive` | 递归互斥体 |
| `mtx_timed`     | 定时互斥体 |










### mtx_timed <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_types](https://zh.cppreference.com/w/c/thread/mtx_types)

```c
// (C11 起)
enum {
    mtx_plain = /* 未指明 */,
    mtx_recursive = /* 未指明 */,
    mtx_timed = /* 未指明 */
};
```

​	定义互斥体的类型

​	传递给 [mtx_init](https://zh.cppreference.com/w/c/thread/mtx_init) 时，标识要创建的互斥体类型。

| 常量            | 解释       |
| --------------- | ---------- |
| `mtx_plain`     | 平常互斥体 |
| `mtx_recursive` | 递归互斥体 |
| `mtx_timed`     | 定时互斥体 |










### once_flag <- 11+

原址：[https://zh.cppreference.com/w/c/thread/call_once](https://zh.cppreference.com/w/c/thread/call_once)

```c
void call_once( once_flag* flag, void (*func)(void) );// (1) (C11 起)
typedef /* 未指明 */ once_flag  //	(2)	(C11 起)
#define ONCE_FLAG_INIT /* 未指明 */ //(3)	(C11 起)
```

1) 调用函数 `func` 恰好一次，即使从多个线程调用。函数 `func` 的完成与先前或后继的用同一 `flag` 对象的对 `call_once` 调用同步。
2) 足以保有 `call_once` 所用标志的完整对象类型。
3) 展开成能用于初始化 `once_flag` 类型对象的值。

**参数**

| flag | -    | 指向用于确保只调用一次 `func` 的 `call_once` 对象的指针 |
| ---- | ---- | ------------------------------------------------------- |
| func | -    | 只执行一次的函数                                        |

**返回值**

​	（无）

**注意**

​	此函数的 POSIX 等价物是 [`pthread_once`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_once.html)。

**示例**



```c
#include <stdio.h>
#include <threads.h>
 
void do_once(void) {
    puts("called once");
}
 
static once_flag flag = ONCE_FLAG_INIT;
int func(void* data)
{
    call_once(&flag, do_once);
}
 
int main(void)
{
    thrd_t t1, t2, t3, t4;
    thrd_create(&t1, func, NULL);
    thrd_create(&t2, func, NULL);
    thrd_create(&t3, func, NULL);
    thrd_create(&t4, func, NULL);
 
    thrd_join(t1, NULL);
    thrd_join(t2, NULL);
    thrd_join(t3, NULL);
    thrd_join(t4, NULL);
}
```

输出：

```txt
called once
```




### thrd_busy <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_errors](https://zh.cppreference.com/w/c/thread/thrd_errors)

```c
// (C11 起)
enum {
    thrd_success = /* 未指明 */,
    thrd_nomem = /* 未指明 */,
    thrd_timedout = /* 未指明 */,
    thrd_busy = /* 未指明 */,
    thrd_error = /* 未指明 */
};
```

​	指示线程错误状态










### thrd_error <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_errors](https://zh.cppreference.com/w/c/thread/thrd_errors)

```c
// (C11 起)
enum {
    thrd_success = /* 未指明 */,
    thrd_nomem = /* 未指明 */,
    thrd_timedout = /* 未指明 */,
    thrd_busy = /* 未指明 */,
    thrd_error = /* 未指明 */
};
```




### thrd_nomem <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_errors](https://zh.cppreference.com/w/c/thread/thrd_errors)

```c
// (C11 起)
enum {
    thrd_success = /* 未指明 */,
    thrd_nomem = /* 未指明 */,
    thrd_timedout = /* 未指明 */,
    thrd_busy = /* 未指明 */,
    thrd_error = /* 未指明 */
};
```




### thrd_success <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_errors](https://zh.cppreference.com/w/c/thread/thrd_errors)

```c
// (C11 起)
enum {
    thrd_success = /* 未指明 */,
    thrd_nomem = /* 未指明 */,
    thrd_timedout = /* 未指明 */,
    thrd_busy = /* 未指明 */,
    thrd_error = /* 未指明 */
};
```




### thrd_timedout <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_errors](https://zh.cppreference.com/w/c/thread/thrd_errors)

```c
// (C11 起)
enum {
    thrd_success = /* 未指明 */,
    thrd_nomem = /* 未指明 */,
    thrd_timedout = /* 未指明 */,
    thrd_busy = /* 未指明 */,
    thrd_error = /* 未指明 */
};
```




### thread_local <- 11+ 23 R

原址：[https://zh.cppreference.com/w/c/thread/thread_local](https://zh.cppreference.com/w/c/thread/thread_local)

```c
#define thread_local _Thread_local // (C11 起) (C23 移除)
```

​	便利宏，用于指定对象拥有 [线程局部存储期](https://zh.cppreference.com/w/c/language/storage_duration)。

**注解**

​	自 C23 起，`thread_local` 自身是关键词，可能亦为预定义宏，故 `<threads.h>` 不再提供它。



## 函数







### call_once <- 11+

原址：[https://zh.cppreference.com/w/c/thread/call_once](https://zh.cppreference.com/w/c/thread/call_once)

```c
void call_once( once_flag* flag, void (*func)(void) );// (1) (C11 起)
typedef /* 未指明 */ once_flag  //	(2)	(C11 起)
#define ONCE_FLAG_INIT /* 未指明 */ //(3)	(C11 起)
```

1）调用函数 `func` 恰好一次，即使从多个线程调用。函数 `func` 的完成与先前或后继的用同一 `flag` 对象的对 `call_once` 调用同步。

2）足以保有 `call_once` 所用标志的完整对象类型。

3）展开成能用于初始化 `once_flag` 类型对象的值。

**参数**

| flag | -    | 指向用于确保只调用一次 `func` 的 `call_once` 对象的指针 |
| ---- | ---- | ------------------------------------------------------- |
| func | -    | 只执行一次的函数                                        |

**返回值**

​	（无）

**注意**

​	此函数的 POSIX 等价物是 [`pthread_once`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_once.html)。

**示例**



```c
#include <stdio.h>
#include <threads.h>
 
void do_once(void) {
    puts("called once");
}
 
static once_flag flag = ONCE_FLAG_INIT;
int func(void* data)
{
    call_once(&flag, do_once);
}
 
int main(void)
{
    thrd_t t1, t2, t3, t4;
    thrd_create(&t1, func, NULL);
    thrd_create(&t2, func, NULL);
    thrd_create(&t3, func, NULL);
    thrd_create(&t4, func, NULL);
 
    thrd_join(t1, NULL);
    thrd_join(t2, NULL);
    thrd_join(t3, NULL);
    thrd_join(t4, NULL);
}
```

输出：

```txt
called once
```




### cnd_broadcast <- 11+

原址：[https://zh.cppreference.com/w/c/thread/cnd_broadcast](https://zh.cppreference.com/w/c/thread/cnd_broadcast)

```c
int cnd_broadcast( cnd_t *cond );
(C11 起)
```

​	接触所有当前在 `cond` 所指向的条件变量上等待的线程的阻塞。若无在 `cond` 上阻塞的线程，则不做任何事并返回 `thrd_success`。

**参数**

| cond | -    | 指向条件变量的指针 |
| ---- | ---- | ------------------ |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### cnd_destroy <- 11+

原址：[https://zh.cppreference.com/w/c/thread/cnd_destroy](https://zh.cppreference.com/w/c/thread/cnd_destroy)

```c
void cnd_destroy( cnd_t* cond );
(C11 起)
```

​	销毁 `cond` 所指向的条件变量。

​	若有线程在 `cond` 上等待，则行为未定义。

**参数**

| cond | -    | 指向要销毁的条件变量的指针 |
| ---- | ---- | -------------------------- |

**返回值**

（无）










### cnd_init <- 11+

原址：[https://zh.cppreference.com/w/c/thread/cnd_init](https://zh.cppreference.com/w/c/thread/cnd_init)

```c
int cnd_init( cnd_t* cond );
(C11 起)
```

​	初始化新的条件变量。设置 `cond` 所指的对象为标识该条件变量的值。

**参数**

| cond | -    | 指针，指向要存储条件变量标识符到的对象 |
| ---- | ---- | -------------------------------------- |

**返回值**

​	若成功创建条件变量则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)。否则若内存量不足则返回 [thrd_nomem](https://zh.cppreference.com/w/c/thread/thrd_errors)，若出现其他错误则返回 `thrd_error`。










### cnd_signal <- 11+

原址：[https://zh.cppreference.com/w/c/thread/cnd_signal](https://zh.cppreference.com/w/c/thread/cnd_signal)

```c
int cnd_signal( cnd_t *cond );
(C11 起)
```

​	接触当前在 `cond` 所指向的条件变量上等待的一个线程的阻塞。若无线程被阻塞，则不做任何事并返回 `thrd_success`。

**参数**

| cond | -    | 指向条件变量的指针 |
| ---- | ---- | ------------------ |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### cnd_timedwait <- 11+

原址：[https://zh.cppreference.com/w/c/thread/cnd_timedwait](https://zh.cppreference.com/w/c/thread/cnd_timedwait)

```c
int cnd_timedwait( cnd_t* restrict cond, mtx_t* restrict mutex,
                   const struct timespec* restrict time_point );
(C11 起)
```

​	原子地解锁 `mutex` 所指向的互斥体，并在 `cond` 所指向的条件变量上阻塞，直到线程被 [cnd_signal](https://zh.cppreference.com/w/c/thread/cnd_signal) 或 [cnd_broadcast](https://zh.cppreference.com/w/c/thread/cnd_broadcast) 发信号，或直至抵达 `time_point` 所指向的基于 TIME_UTC 的时间点，或直至虚假唤醒出现。在函数返回前重新锁定该互斥体。

​	若调用方线程未锁定该互斥体，则行为未定义。

**参数**

| cond       | -    | 指向要在上面阻塞的条件变量的指针   |
| ---------- | ---- | ---------------------------------- |
| mutex      | -    | 指向要在阻塞期间解锁的互斥体的指针 |
| time_point | -    | 指向指定等待超时时间的对象的指针   |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，若在锁定互斥前抵达时限则为 thrd_timedout，若出现错误则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### cnd_wait <- 11+

原址：[https://zh.cppreference.com/w/c/thread/cnd_wait](https://zh.cppreference.com/w/c/thread/cnd_wait)

```c
int cnd_wait( cnd_t* cond, mtx_t* mutex );
(C11 起)
```

​	原子地解锁 `mutex` 所指向的互斥体，并在 `cond` 所指向的条件变量上阻塞，直至线程被 [cnd_signal](https://zh.cppreference.com/w/c/thread/cnd_signal) 或 [cnd_broadcast](https://zh.cppreference.com/w/c/thread/cnd_broadcast) 发信号，或直至虚假唤醒出现。在此函数返回前，重新锁定该互斥。

​	若调用方线程未锁定该互斥体，则行为未定义。

**参数**

| cond  | -    | 指向要在上面阻塞的条件变量的指针 |
| ----- | ---- | -------------------------------- |
| mutex | -    | 指向要在阻塞期解锁的互斥体的指针 |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。

**示例**

​	利用 cnd_wait 函数阻塞 main 线程



```c
#include <stdio.h>
#include <stdlib.h>
#include <assert.h>
#include <threads.h>
 
mtx_t mwait;
cnd_t cwait;
thrd_t th;
 
int thread_deal_fn(void *arg) {
    printf("thread_deal_fn 睡眠 10s\n");
    thrd_sleep(&(struct timespec){.tv_sec = 10}, NULL);
    printf("thread_deal_fn 唤醒 main 线程\n");
    cnd_broadcast(&cwait);
}
 
int main(){
    // 初始化
    assert(("mwait 初始化失败", mtx_init(&mwait, mtx_plain) == thrd_success));
    assert(("cwait 初始化失败", cnd_init(&cwait) == thrd_success));
 
    assert(("线程 thread_deal_fn 创建失败", thrd_create(&th, thread_deal_fn, NULL) == thrd_success));
 
    printf("main 线程阻塞\n");
    cnd_wait(&cwait, &mwait);
 
    printf("main 线程被唤醒，准备退出\n");
    return 0;
}
 
/* gcc 在某些平台上默认程序为单线程，可能需要手动添加 -pthread 选项开启多线程和链接 posix thread 库
*/
```

​	输出：

```txt
main 线程阻塞
thread_deal_fn 睡眠 10s
thread_deal_fn 唤醒 main 线程
main 线程被唤醒，准备退出
```




### mtx_destroy <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_destroy](https://zh.cppreference.com/w/c/thread/mtx_destroy)

```c
void mtx_destroy( mtx_t *mutex );
(C11 起)
```

​	销毁 `mutex` 所指向的互斥体。

​	若有线程在 `mutex` 上等待，则行为未定义。

**参数**

| mutex | -    | 指向要销毁的互斥体的指针 |
| ----- | ---- | ------------------------ |

**返回值**

（无）










### mtx_init <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_init](https://zh.cppreference.com/w/c/thread/mtx_init)

```c
int mtx_init( mtx_t* mutex, int type );
(C11 起)
```

​	创建新的拥有 `type` 类型的互斥体。设置 `mutex` 所指向的对象为新创建互斥体的标识符。

`type` 必须拥有下列值之一：

- [mtx_plain](https://zh.cppreference.com/w/c/thread/mtx_types) - 创建简单的，非递归互斥体。
- [mtx_timed](https://zh.cppreference.com/w/c/thread/mtx_types) - 创建非递归的，支持超时的互斥体。
- [mtx_plain](http://zh.cppreference.com/w/c/thread/mtx_types) | [mtx_recursive](http://zh.cppreference.com/w/c/thread/mtx_types) - 创建递归互斥体。
- [mtx_timed](http://zh.cppreference.com/w/c/thread/mtx_types) | [mtx_recursive](http://zh.cppreference.com/w/c/thread/mtx_types) - 创建递归的支持超时的互斥体。

**参数**

| mutex | -    | 指向要初始化的互斥体的指针 |
| ----- | ---- | -------------------------- |
| type  | -    | 互斥的类型                 |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### mtx_lock <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_lock](https://zh.cppreference.com/w/c/thread/mtx_lock)

```c
int mtx_lock( mtx_t* mutex );
(C11 起)
```

​	阻塞当前线程，直至锁定 `mutex` 所指向的互斥体。

​	若该互斥体已被当前线程锁定且非递归，则行为未定义。

​	先前在同一互斥体上对 [mtx_unlock](https://zh.cppreference.com/w/c/thread/mtx_unlock) 的调用 *同步于* 此操作，而且任何给定互斥体上的所有锁定/解锁操作构成单独全序（类似原子对象的修改顺序）。

**参数**

| mutex | -    | 指向要锁定的互斥体的指针 |
| ----- | ---- | ------------------------ |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### mtx_timedlock <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_timedlock](https://zh.cppreference.com/w/c/thread/mtx_timedlock)

```c
int mtx_timedlock( mtx_t *restrict mutex,
                   const struct timespec *restrict time_point );
(C11 起)
```

​	阻塞当前线程，直到 `mutex` 所指向的互斥体被锁，或直到抵达 `time_point` 所指向的基于 TIME_UTC 的时间点。

​	若当前线程已经锁定该互斥体且该互斥体非递归，则行为未定义。

​	若该互斥体不支持超时，则行为未定义。

​	先前在同一互斥体上对 [mtx_unlock](https://zh.cppreference.com/w/c/thread/mtx_unlock) 的调用 *同步于* 此操作（若此操作成功），而且任何给定的互斥体上的所有锁定/解锁组成单独全序（类似原子对象上的修改顺序）。

**参数**

| mutex      | -    | 指向要锁定的互斥体的指针             |
| ---------- | ---- | ------------------------------------ |
| time_point | -    | 指向要等待到超时的绝对日历时间的指针 |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，若已在锁定互斥体前抵达时限则为 thrd_timedout，若出现错误则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### mtx_trylock <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_trylock](https://zh.cppreference.com/w/c/thread/mtx_trylock)

```c
int mtx_trylock( mtx_t *mutex );
(C11 起)
```

​	尝试锁定 `mutex` 所指向的互斥而不阻塞。若该互斥已被锁定则立即返回。

​	同一互斥上对 [mtx_unlock](https://zh.cppreference.com/w/c/thread/mtx_unlock) 的先前调用 *同步于* 此操作（若此操作成功），而且任何给定互斥上的所有锁定/解锁操作构成单独全序（类似于原子对象上的修改顺序）。

**参数**

| mutex | -    | 指向要锁定的互斥的指针 |
| ----- | ---- | ---------------------- |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors) ，若已锁定该互斥或由于获取可用互斥的虚假失败则为 [thrd_busy](https://zh.cppreference.com/w/c/thread/thrd_errors) ，若出现错误则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors) 。

**缺陷报告**

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为                    | 正确行为 |
| ------------------------------------------------------------ | ------ | ------------------------------- | -------- |
| [DR 470](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_470) | C11    | 不允许 `mtx_trylock` 虚假地失败 | 允许     |










### mtx_unlock <- 11+

原址：[https://zh.cppreference.com/w/c/thread/mtx_unlock](https://zh.cppreference.com/w/c/thread/mtx_unlock)

```c
int mtx_unlock( mtx_t *mutex );
(C11 起)
```

​	解锁 `mutex` 所指向的互斥体。

​	若调用方线程未锁定该互斥体，则行为未定义。

​	在同一互斥体上，此函数 *同步于* 后继的 [mtx_lock](https://zh.cppreference.com/w/c/thread/mtx_lock)、[mtx_trylock](https://zh.cppreference.com/w/c/thread/mtx_trylock) 或 [mtx_timedlock](https://zh.cppreference.com/w/c/thread/mtx_timedlock)。给定互斥上的所有锁/解锁操作构成单独全序体（类似原子对象上的修改顺序）。

**参数**

| mutex | -    | 指向要解锁的互斥体的指针 |
| ----- | ---- | ------------------------ |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。










### thrd_create <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_create](https://zh.cppreference.com/w/c/thread/thrd_create)

```c
int thrd_create( thrd_t *thr, thrd_start_t func, void *arg ); // (C11 起)
```

​	创建一个执行函数 `func` 的新线程，以 `func(arg)` 调用此函数。

​	若成功，则设置 `thr` 所指向的对象为新线程的标识符。

​	此函数的完成 *同步于* 线程的开始。

**参数**

| thr  | -    | 指向放置新线程标识符的内存位置的指针 |
| ---- | ---- | ------------------------------------ |
| func | -    | 要执行的函数                         |
| arg  | -    | 传递给函数的参数                     |

**返回值**

​	若新线程创建成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)。否则若内存不足则返回 [thrd_nomem](https://zh.cppreference.com/w/c/thread/thrd_errors)，若出现其他错误则返回 `thrd_error`。

**注意**

​	一旦线程完结并融合或脱附，则可能重新使用线程标识符。

​	类型 `thrd_start_t` 是 `int(*)(void*)` 的 `typedef`，有别于 POSIX 的等价版本 `void*(*)(void*)`。

​	将所有所有线程特定存储值（见 [tss_create](https://zh.cppreference.com/w/c/thread/tss_create)）初始化为 [NULL](https://zh.cppreference.com/w/c/types/NULL)。

​	从函数 `func` 返回等价于以等于 `func` 返回值的参数调用 [thrd_exit](https://zh.cppreference.com/w/c/thread/thrd_exit)。










### thrd_current <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_current](https://zh.cppreference.com/w/c/thread/thrd_current)

```c
thrd_t thrd_current(void);
(C11 起)
```

​	返回调用方线程的标识符。

**参数**

​	（无）

**返回值**

​	调用方线程的标识符。










### thrd_detach <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_detach](https://zh.cppreference.com/w/c/thread/thrd_detach)

```c
int thrd_detach( thrd_t thr );
(C11 起)
```

​	将 `thr` 所标识的线程从当前环境中分离。一旦该线程退出，就自动释放其保有的资源。如果线程非分离状态则需要 join 等待线程结束，否则会产生一个僵尸线程。

**参数**

| thr  | -    | 要分离的线程的标识符 |
| ---- | ---- | -------------------- |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。

**僵尸线程产生的示例**



```c
#include<stdio.h>
#include<stdint.h>
#include<threads.h>
 
int test_fn(void *arg){
    return 0;
}
 
int test_detach_fn(void *arg){
    thrd_detach(thrd_current());
    return 0;
}
 
int main(){
    thrd_t th;
    int16_t i = 0;
    int ret = 0;
    int32_t status = 0;
 
    // 循环创建线程，但是不等待线程结束，但分离线程。
    for(i = 0; i < INT16_MAX; ++i) {
        status = thrd_create(&th, test_detach_fn, NULL);
 
        if(status != thrd_success) {
            printf("detach fail %d\n", i);
            break;
        }
 
    }
 
    // 循环创建线程，但是等待线程结束，但不分离线程。
    for(i = 0; i < INT16_MAX; ++i) {
        status = thrd_create(&th, test_fn, NULL);
 
        if(status != thrd_success) {
            printf("join nodetach fail %d\n", i);
            break;
        }
 
        thrd_join(th, &ret);
 
    }
 
    // 循环创建线程，但是不等待线程结束，也不分离线程。
    for(i = 0; i < INT16_MAX; ++i) {
        status = thrd_create(&th, test_fn, NULL);
 
        if(status != thrd_success) {
            printf("nodetach fail %d\n", i);
            break;
        }
 
    }
 
    return 0;
}
 
 
/* 如果你尝试用 gcc 编译，记得链接线程库
   gcc xx.c -o xx -lpthread
*/
```

输出：

```txt
nodetach fail 32754
```




### thrd_equal <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_equal](https://zh.cppreference.com/w/c/thread/thrd_equal)

```c
int thrd_equal( thrd_t lhs, thrd_t rhs );
(C11 起)
```

​	检查 `lhs` 与 `rhs` 是否表示同一线程。

**参数**

| lhs, rhs | -    | 要比较的线程 |
| -------- | ---- | ------------ |

**返回值**

​	若 `lhs` 与 `rhs` 表示同一线程则为非零值，否则为 0。










### thrd_exit <- 11+ 23 F

原址：[https://zh.cppreference.com/w/c/thread/thrd_exit](https://zh.cppreference.com/w/c/thread/thrd_exit)

```c
_Noreturn void thrd_exit( int res ); // (C11 起)(C23 前)
[[noreturn]] void thrd_exit( int res ); // (C23 起)
```

​	首先，对于每个以非空析构器创建，关联值非空的（见 [tss_create](https://zh.cppreference.com/w/c/thread/tss_create)）线程特定存储键，`thrd_exit` 设置与键关联的值为 [NULL](http://zh.cppreference.com/w/c/types/NULL)，然后以该键的先前值调用析构器。析构器的调用顺序是未指定的。

​	若在此后，有剩余键拥有非空的析构器和值（例如若析构器执行了 [tss_set](https://zh.cppreference.com/w/c/thread/tss_set)），则至多重复 [TSS_DTOR_ITERATIONS](https://zh.cppreference.com/w/c/thread/TSS_DTOR_ITERATIONS) 次处理。

​	最后，`thrd_exit` 函数终止调用方线程的执行，并设置其结果码为 `res`。

​	若程序中的最后线程以 `thrd_exit` 退出，则如同通过以 [EXIT_SUCCESS](https://zh.cppreference.com/w/c/program/EXIT_status) 为实参调用 [exit](https://zh.cppreference.com/w/c/program/exit) 一般终止整个程序（故 [atexit](https://zh.cppreference.com/w/c/program/atexit) 所注册的函数在最后线程的环境中执行）。

**参数**

| res  | -    | 要返回的值 |
| ---- | ---- | ---------- |

**返回值**

（无）










### thrd_join <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_join](https://zh.cppreference.com/w/c/thread/thrd_join)

```c
int thrd_join( thrd_t thr, int *res );
(C11 起)
```

​	阻塞当前线程，直到 `thr` 所标识的线程完成执行。

​	若 `res` 不是空指针，则将该线程的结果码放置到 `res` 所指向的位置。

​	该线程的终止 *同步于* 此函数的完成。

​	若该线程之前已被另一线程分离或合并，则行为未定义。

**参数**

| thr  | -    | 要合并的线程的标识符 |
| ---- | ---- | -------------------- |
| res  | -    | 放置结果码到的位置   |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors) ，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors) 。










### thrd_sleep <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_sleep](https://zh.cppreference.com/w/c/thread/thrd_sleep)

```c
int thrd_sleep( const struct timespec* duration,
                struct timespec* remaining );
(C11 起)
```

​	阻塞当前线程的执行，*至少* 直至经过 `duration` 所指向的基于 TIME_UTC 的时长。

​	若收到不忽略的信号（[signal](https://zh.cppreference.com/w/c/program/signal)），则可以较早地从休眠恢复。此情况下，若 `remaining` 非 [NULL](https://zh.cppreference.com/w/c/types/NULL)，则存储剩余时长到 `remaining` 所指向的对象中。

**参数**

| duration  | -    | 指向要休眠的时长的指针                                       |
| --------- | ---- | ------------------------------------------------------------ |
| remaining | -    | 指向要放置中断剩余时间的对象的指针。可为 [NULL](https://zh.cppreference.com/w/c/types/NULL)，此情况下忽略它 |

**返回值**

​	成功休眠时为 0，若出现信号则为 -1，若出现错误则为其他负值。

**注意**

​	`duration` 和 `remaining` 可以指向相同对象，这会简化函数在信号后的重新运行。

​	实际休眠时间可能长于请求，因为它会被向上舍入到计时器的粒度，而且还因为调度和环境切换开销。

​	此函数的 POSIX 等价版本是 [`nanosleep`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/nanosleep.html)。

**示例**



```c
#include <threads.h>
#include <time.h>
#include <stdio.h>
 
int main(void)
{
    printf("Time: %s", ctime(&(time_t){time(NULL)}));
    thrd_sleep(&(struct timespec){.tv_sec=1}, NULL); // 睡眠 1 秒
    printf("Time: %s", ctime(&(time_t){time(NULL)}));
}
```

​	输出：

```txt
Time: Mon Feb  2 16:18:41 2015
Time: Mon Feb  2 16:18:42 2015
```




### thrd_yield <- 11+

原址：[https://zh.cppreference.com/w/c/thread/thrd_yield](https://zh.cppreference.com/w/c/thread/thrd_yield)

```c
void thrd_yield(void);
(C11 起)
```

​	向实现提供一个重新安排线程执行的提示，允许其他线程运行。

**参数**

​	（无）

**返回值**

​	（无）

**注意**

​	此函数的准确行为取决于实现，特别是使用中的 OS 调度器和系统状态。例如，先进先出的实时调度器（Linux 的 `SCHED_FIFO`）会挂起当前线程，并将它放在准备运行的相同优先级线程队列尾部，而若无处于相同优先级的线程，则 `yield` 无效果。

​	此函数的 POSIX 等价版本是 [`sched_yield`](http://pubs.opengroup.org/onlinepubs/9699919799/functions/sched_yield.html)。

**示例**



```c
#include <stdio.h>
#include <time.h>
#include <threads.h>
 
// 工具函数：微秒单位的 timespec 差
double usdiff(struct timespec s, struct timespec e)
{
    double sdiff = difftime(e.tv_sec, s.tv_sec);
    long nsdiff = e.tv_nsec - s.tv_nsec;
    if(nsdiff < 0) return 1000000*(sdiff-1) + (1000000000L+nsdiff)/1000.0;
    else return 1000000*(sdiff) + nsdiff/1000.0;
}
 
// 在让出时等待
void sleep_100us()
{
    struct timespec start, end;
    timespec_get(&start, TIME_UTC);
    do {
        thrd_yield();
        timespec_get(&end, TIME_UTC);
    } while(usdiff(start, end) < 100.0);
}
 
int main()
{
    struct timespec start, end;
    timespec_get(&start, TIME_UTC);
    sleep_100us();
    timespec_get(&end, TIME_UTC);
    printf("Waited for %.3f us\n", usdiff(start, end));
}
```

​	可能的输出：

```txt
Waited for 100.344 us
```




### tss_create <- 11+

原址：

```c
```




### tss_delete <- 11+

原址：[https://zh.cppreference.com/w/c/thread/tss_delete](https://zh.cppreference.com/w/c/thread/tss_delete)

```c
void tss_delete( tss_t tss_id );
(C11 起)
```

​	销毁 `tss_id` 所标识的线程特定存储。

​	若以 [tss_create](https://zh.cppreference.com/w/c/thread/tss_create) 注册了一个析构器，则不调用它（仅在线程退出时调用，无论是由 [thrd_exit](https://zh.cppreference.com/w/c/thread/thrd_exit) 还是通过从线程函数返回）。程序员负责确保在调用 `tss_delete` 前，每个知晓 `tss_id` 的线程都进行了必要的清理。

​	若在另一线程执行 `tss_id` 的析构器时调用 `tss_delete`，则这是否会更改关联析构器的调用次数是未指定的。

​	若在调用方线程执行析构器时调用 `tss_delete`，则与 `tss_id` 关联的析构器将不会在此线程上再次执行。

**参数**

| tss_id | -    | 先前 [tss_create](https://zh.cppreference.com/w/c/thread/tss_create) 所返回，且仍未被 **tss_delete** 删除的线程特定存储键 |
| ------ | ---- | ------------------------------------------------------------ |

**返回值**

​	（无）

**注意**

​	此函数的 POSIX 等价版本是 [pthread_key_delete](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_key_delete.html)。

​	`tss_delete` 决不调用析构器，是因为正常情况下，有意令原先设置了的析构器所将处理的值（经由 [tss_set](https://zh.cppreference.com/w/c/thread/tss_set)）的同一线程来执行（线程退出时调用）该析构器，而且析构器甚至可能依赖该线程所见的该值或其他线程特定数据。执行 `tss_delete` 的线程对其他线程的 TSS 无访问权限。即使可能对每个线程的与 `tss_id` 关联的值都调用析构器，但若仅为检验该线程中此 TSS 的值是否为空，`tss_delete` 也必须与每个线程同步（仅对非空值调用析构器）。

**示例**

> 本节未完成 
>
> 原因：暂无示例








### tss_get <- 11+

原址：[https://zh.cppreference.com/w/c/thread/tss_get](https://zh.cppreference.com/w/c/thread/tss_get)

```c
void *tss_get( tss_t tss_key );
(C11 起)
```

​	返回 `tss_key` 所标识的，当前线程的线程特定存储中保有的值。不同线程可能获取同一键所标识的不同值。

​	线程启动时（见 [thrd_create](https://zh.cppreference.com/w/c/thread/thrd_create)），与所有 TSS 关键关联的值均为 `NULL`。可以用 [tss_set](https://zh.cppreference.com/w/c/thread/tss_set) 将相异的值置入线程指定存储。

**参数**

| tss_key | -    | 从 [tss_create](https://zh.cppreference.com/w/c/thread/tss_create) 获得，且未被 [tss_delete](https://zh.cppreference.com/w/c/thread/tss_delete) 删除的线程特定存储键 |
| ------- | ---- | ------------------------------------------------------------ |

**返回值**

​	成功时为值，失败时为 [NULL](https://zh.cppreference.com/w/c/types/NULL)。

**注意**

​	此函数的 POSIX 等价版本是 [pthread_getspecific](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_getspecific.html)。

**示例**

> 本节未完成 
>
> 原因：暂无示例








### tss_set <- 11+

原址：[https://zh.cppreference.com/w/c/thread/tss_set](https://zh.cppreference.com/w/c/thread/tss_set)

```c
int tss_set( tss_t tss_id, void *val );
(C11 起)
```

​	设置当前线程的 `tss_id` 所标识的线程特定存储的值为 `val`。不同线程可以对同一键设置不同的值。

​	若析构器可用，则不调用它。

**参数**

| tss_id | -    | 从 [tss_create](https://zh.cppreference.com/w/c/thread/tss_create) 获得，且未被 [tss_delete](https://zh.cppreference.com/w/c/thread/tss_delete) 删除的线程特定存储键 |
| ------ | ---- | ------------------------------------------------------------ |
| val    | -    | 要设置给线程特定存储的值                                     |

**返回值**

​	若成功则为 [thrd_success](https://zh.cppreference.com/w/c/thread/thrd_errors)，否则为 [thrd_error](https://zh.cppreference.com/w/c/thread/thrd_errors)。

**注意**

​	此函数的 POSIX 等价版本为 [pthread_setspecific](http://pubs.opengroup.org/onlinepubs/9699919799/functions/pthread_setspecific.html)。

​	TSS 的典型用法是存储指向动态分配内存块的指针，这些内存块为调用方线程的使用保留。

​	可以在 TSS 析构器中调用 `tss_set`。若 TSS 存储中析构器以非 NULL 值退出，则 [thrd_exit](https://zh.cppreference.com/w/c/thread/thrd_exit) 会重试析构器至多 [TSS_DTOR_ITERATIONS](https://zh.cppreference.com/w/c/thread/TSS_DTOR_ITERATIONS) 次，之后存储将丢失。

**示例**

> 本节未完成 
>
> 原因：改进，最好为启发寻找 POSIX 示例

```c
int thread_func(void *arg) {
    tss_t key;
    if (thrd_success == tss_create(&key, free)) {
        tss_set(key, malloc(4)); // 在 TSS 上存储指针
        // ...
    }
} // 对 TSS 上存储的指针调用 free()
```

