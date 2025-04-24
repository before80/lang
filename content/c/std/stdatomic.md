
+++
title = "<stdatomic.h> (C11)"
date = 2025-04-24T18:35:56+08:00
weight = 150
type = "docs"
description = "原子操作"
isCJKLanguage = true
draft = false

+++

## 类型



### atomic_flag

原址：[https://zh.cppreference.com/w/c/atomic/atomic_flag](https://zh.cppreference.com/w/c/atomic/atomic_flag)

作用：免锁原子布尔标志  (结构体)

备注：
```c
// 在标头 <stdatomic.h> 定义
typedef struct /* unspecified */ atomic_flag;// (C11 起)
```

​	`atomic_flag` 是一种原子布尔类型。不同于其他原子类型，它保证是免锁的。不同于 [`<tomic_boo>`](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C) ， `atomic_flag` 不提供加载或存储操作。

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.17.1/5 atomic_flag （第 293 页）

  - 7.17.8 Atomic flag type and operations （第 302-303 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/4 atomic_flag （第 200 页）

  - 7.17.8 Atomic flag type and operations （第 208-209 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/4 atomic_flag （第 273 页）

  - 7.17.8 Atomic flag type and operations （第 285-286 页）

**参阅**

| [ATOMIC_FLAG_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_FLAG_INIT) | 初始化新的 `atomic_flag` (宏常量)              |
| ------------------------------------------------------------ | ---------------------------------------------- |
| [atomic_flag_test_and_set (C11)<br />atomic_flag_test_and_set_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set) | 设置 `atomic_flag` 为 `true` 并返回旧值 (函数) |
| [atomic_flag_clear (C11)<br />atomic_flag_clear_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear) | 设置 `atomic_flag` 为 `false` (函数)           |
| **atomic_flag** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_flag)** |                                                |






## 枚举



### memory_order

原址：[https://zh.cppreference.com/w/c/atomic/memory_order](https://zh.cppreference.com/w/c/atomic/memory_order)

作用：定义内存顺序制约   (枚举)

备注：
```c
// 在标头 <stdatomic.h> 定义
enum memory_order
{
    memory_order_relaxed,
    memory_order_consume,
    memory_order_acquire,
    memory_order_release,
    memory_order_acq_rel,
    memory_order_seq_cst

};// (C11 起)
```

​	`memory_order` 指定内存访问，包括常规的非原子内存访问，如何围绕原子操作排序。在没有任何约束的多处理器系统上，多个线程同时读或写数个变量时，一个线程能观测到变量值更改的顺序不同于另一个线程写它们的顺序。实际上，更改的顺序甚至能在多个读取线程间相异。一些类似的效果还能在单处理器系统上出现，因为内存模型允许编译器进行变换。

​	[语言](https://zh.cppreference.com/w/c/language/atomic)和库中所有原子操作的默认行为提供*序列一致定序*（见后述讨论）。该默认行为可能有损性能，不过可以给予库的原子操作额外的 `memory_order` 实参，以指定确切的约束，在原子性外，编译器和处理器还必须强制该操作。

### 常量

| 在标头 `<stdatomic.h>` 定义       |                                                              |
| ----------------------------------- | ------------------------------------------------------------ |
| 值                                  | 解释                                                         |
| `memory_order_relaxed`              | 宽松操作：没有同步或定序约束，仅对此操作要求原子性（见下方[宽松定序](https://zh.cppreference.com/w/c/atomic/memory_order#.E5.AE.BD.E6.9D.BE.E5.AE.9A.E5.BA.8F)）。 |
| `memory_order_consume` (C++26 弃用) | 有此内存定序的加载操作，在其影响的内存位置进行*消费操作*：当前线程中依赖于当前加载的值的读或写不能被重排到此加载之前。其他线程中对有数据依赖的变量进行的释放同一原子变量的写入，能为当前线程所见。在大多数平台上，这只影响到编译器优化（见下方[释放-消费定序](https://zh.cppreference.com/w/c/atomic/memory_order#.E9.87.8A.E6.94.BE-.E6.B6.88.E8.B4.B9.E5.AE.9A.E5.BA.8F)）。 |
| `memory_order_acquire`              | 有此内存定序的加载操作，在其影响的内存位置进行*获得操作*：当前线程中读或写不能被重排到此加载之前。其他线程的所有释放同一原子变量的写入，能为当前线程所见（见下方[释放-获得定序](https://zh.cppreference.com/w/c/atomic/memory_order#.E9.87.8A.E6.94.BE-.E8.8E.B7.E5.BE.97.E5.AE.9A.E5.BA.8F)）。 |
| `memory_order_release`              | 有此内存定序的存储操作进行*释放操作*：当前线程中的读或写不能被重排到此存储之后。当前线程的所有写入，可见于获得该同一原子变量的其他线程（见下方[释放-获得定序](https://zh.cppreference.com/w/c/atomic/memory_order#.E9.87.8A.E6.94.BE-.E8.8E.B7.E5.BE.97.E5.AE.9A.E5.BA.8F)），并且对该原子变量的带依赖写入变得对于其他消费同一原子对象的线程可见（见下方[释放-消费定序](https://zh.cppreference.com/w/c/atomic/memory_order#.E9.87.8A.E6.94.BE-.E6.B6.88.E8.B4.B9.E5.AE.9A.E5.BA.8F)）。 |
| `memory_order_acq_rel`              | 带此内存定序的读修改写操作既是*获得操作*又是*释放操作*。当前线程的读或写内存不能被重排到此存储之前或之后。所有释放同一原子变量的线程的写入可见于修改之前，而且修改可见于其他获得同一原子变量的线程。 |
| `memory_order_seq_cst`              | 有此内存定序的加载操作进行*获得操作*，存储操作进行*释放操作*，而读修改写操作进行*获得操作*和*释放操作*，再加上存在一个单独全序，其中所有线程以同一顺序观测到所有修改（见下方[序列一致定序](https://zh.cppreference.com/w/c/atomic/memory_order#.E5.BA.8F.E5.88.97.E4.B8.80.E8.87.B4.E5.AE.9A.E5.BA.8F)）。 |

> 本节未完成
>
> 原因：先发生于和其他概念同 C++ ，但保持修改顺序和[c/language/atomic](https://zh.cppreference.com/w/c/language/atomic)中的四种一致

> 本节未完成
>
> 原因：在做上面的时候，不要忘记在 C11 出版时先发生于不是不成环的，这经由 DR 401 被更新到匹配 C++11

#### 宽松顺序

​	被标以 `memory_order_relaxed` 的原子操作不是同步操作；它们不会为并发的内存访问行为添加定序约束。它们只保证原子性和修改顺序的一致性。

​	例如，对于初始值为零的 `x` 和 `y`，

​	`// 线程 1：
r1 = [atomic_load_explicit](http://zh.cppreference.com/w/c/atomic/atomic_load)(y, memory_order_relaxed); // A
[atomic_store_explicit](http://zh.cppreference.com/w/c/atomic/atomic_store)(x, r1, memory_order_relaxed); // B
// 线程 2：
r2 = [atomic_load_explicit](http://zh.cppreference.com/w/c/atomic/atomic_load)(x, memory_order_relaxed); // C
[atomic_store_explicit](http://zh.cppreference.com/w/c/atomic/atomic_store)(y, 42, memory_order_relaxed); // D` 允许产生 `r1 == 42 && r2 == 42`。因为即使线程 1 中 A *先序于* B 且线程 2 中 C *先序于* D，却无法避免在 `y` 的修改顺序中 D 会出现于 A 之前，且在 `x` 的修改顺序中 B 会出现于 C 之前。D 的对 `y` 的副效应可能可见于线程 1 中 A 的加载操作，而 B 对 `x` 的副效应可能可见于线程 2 中 C 的加载操作。尤其是，这可能在线程 2 中 D 于 C 之前完成的情况下发生，无论因为编译器重排还是发生于运行时。

​	宽松内存定序的典型的应用是计数器自增，例如引用计数器，因为这只要求原子性，但不要求定序或同步。

#### 释放消费顺序

​	若线程 A 中的原子存储被标以 `memory_order_release`，而线程 B 中从同一变量的原子加载被标以 `memory_order_consume`，而线程 B 中的加载读到了由线程 A 中的存储所写入的值，则线程 A 中的存储*按依赖先序于*线程 B 中的加载。

​	线程 A 视角中*先发生于*原子存储的所有内存写入（非原子和宽松原子的），会在线程 B 中该加载操作所*携带依赖*进入的操作中变成*可见副效应*，即一旦完成原子加载，则保证线程 B 中，使用从该加载获得的值的运算符和函数，能见到线程 A 写入内存的内容。

​	同步仅在*释放*和*消费*同一原子变量的线程间建立。其他线程能见到与被同步线程的一者或两者相异的内存访问顺序。

​	在除 DEC Alpha 之外的所有主流 CPU 上，依赖定序是自动的，无需为此同步模式发出额外的 CPU 指令，只有某些编译器优化会受影响（例如，编译器被禁止牵涉到依赖链的对象上的推测性加载）。

​	此定序的典型使用情况，包括对很少被写入的并发数据结构（路由表、配置、安全策略、防火墙规则等）的读取访问，和有指针中介发布的发布者-订阅者的情形，即生产者所发布的指针，消费者能通过其访问信息：无需令生产者写入内存的所有其他内容对消费者可见（这在弱顺序架构上可能是昂贵的操作）。这种场景的例子之一是 [`rcu_dereference`](https://en.wikipedia.org/wiki/Read-copy-update)。

​	注意到 2015 年 2 月为止没有任何已知产品级编译器跟踪依赖链：消费操作均被提升为获得操作。

#### 释放序列

​	若一些原子对象被存储-释放，而有数个其他线程对该原子对象进行读修改写操作，则会形成“释放序列”：所有对该原子对象读修改写的线程与首个线程同步，而且彼此同步，即使它们没有 `memory_order_release` 语义。这使得单产出-多消费情况可行，而无需在每个消费线程间强加不必要的同步。

#### 释放获得顺序

​	若线程 A 中的一个原子存储被标以 `memory_order_release`，而线程 B 中从同一变量的原子加载被标以 `memory_order_acquire`，且线程 B 中的加载读到了线程 A 中的存储所写入的值，则线程 A 中的存储*同步于*线程 B 中的加载。

​	从线程 A 的视角*先发生于*原子存储的所有内存写入（包括非原子及宽松原子的），在线程 B 中成为*可见副效应*。即一旦原子加载完成，则保证线程 B 能观察到线程 A 写入内存的所有内容。仅当 B 实际上返回了 A 所存储的值或其释放序列中后面的值时，才有此保证。

​	同步仅建立在*释放*和*获得*同一原子变量的线程之间。其他线程可能看到与被同步线程的一者或两者相异的内存访问顺序。

​	在强顺序系统（x86、SPARC TSO、IBM 大型机）上，释放-获得定序对于多数操作是自动进行的。无需为此同步模式发出额外的 CPU 指令，只有某些编译器优化受影响（例如，编译器被禁止将非原子存储移到原子存储-释放之后，或将非原子加载移到原子加载-获得之前）。在弱顺序系统（ARM、Itanium、Power PC）上，必须使用特别的 CPU 加载或内存栅栏指令。

​	互斥锁（例如[互斥体](https://zh.cppreference.com/w/c/thread#.E4.BA.92.E6.96.A5)或[原子自旋锁](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set)）是释放-获得同步的例子：线程 A 释放锁而线程 B 获得它时，发生于线程 A 上下文的临界区（释放之前）中的所有事件，必须对于执行同一临界区的线程 B（获得之后）可见。

#### 序列一致顺序

​	被标为 `memory_order_seq_cst` 的原子操作不仅以与释放-获得定序相同的方式进行内存定序（在一个线程中*先发生于*存储的任何副作用都变成进行加载的线程中的*可见副作用*），还对所有带此标签的内存操作建立了一个*单独全序*。

​	正式而言，

​	对原子对象 M 进行加载的每个 `memory_order_seq_cst` 操作 B，均会观测到以下之一：

- 修改 M 的上个操作 A 的结果，A 在单独全序中先出现于 B，
- 或者，若存在这种 A，则 B 可能观测到 M 上的某次修改结果，此次修改非 `memory_order_seq_cst` 而且不*先发生于* A，
- 或者，若不存在这种 A，则 B 可能观测到 M 上的某次无关联修改的结果，此次修改非 `memory_order_seq_cst`。

​	若存在 `memory_order_seq_cst` 的 [atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) 操作 X *先序于* B，则 B 观测到以下之一：

- 在单独全序中先出现于 X 的上个 M 的 `memory_order_seq_cst` 修改，
- 在单独全序中后出现于它的某次 M 的无关联修改。

​	设有 M 上的一对原子操作，称之为 A 和 B，这里 A 写入、B 读取 M 的值，若存在二个 `memory_order_seq_cst` 的 [atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) X 和 Y，且若 A *先序于* X，Y *先序于* B，且 X 在单独全序中先出现于 Y，则 B 观测到二者之一：

- A 的效应，
- 在 M 的修改顺序中后出现于 A 的某次无关联修改。

​	设有 M 上的一对原子操作，称之为 A 和 B，若符合下列条件之一，则 M 的修改顺序中 B 先发生于 A：

- 存在一个 `memory_order_seq_cst` 的 [atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) X，它满足 A *先序于* X，且 X 在单独全序中先出现于 B，
- 或者，存在一个 `memory_order_seq_cst` 的 [atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) Y，它满足 Y *先序于* B，且 A 在单独全序中先出现于 Y，
- 或者，存在 `memory_order_seq_cst` 的 [atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) X 和 Y，它们满足 A *先序于* X，Y *先序于* B，且 X 在单独全序中先出现于 Y。

​	注意这表明：

1） 一旦出现未标记 `memory_order_seq_cst` 的原子操作，则立即丧失序列一致性，

2） 序列一致栅栏仅为栅栏自身建立全序，而不为通常情况下的原子操作建立（*先序于* 不是跨线程关系，不同于*先发生于*）

​	在多生产者-多消费者的情形中，若所有消费者都必须以相同顺序观察到所有生产者的动作出现，则可能必须进行序列定序。

​	全序列定序在所有多核系统上都要求完全的内存栅栏 CPU 指令。这可能成为性能瓶颈，因为它强制受影响的内存访问传播到每个核心。

### 与 volatile 的关系

​	在执行线程中，不能将通过 [volatile 左值](https://zh.cppreference.com/w/c/language/volatile)进行的访问（读和写）重排到同线程内为序列点所分隔的可观测副效应（包含其他 volatile 访问）后，但不保证另一线程观察到此顺序，因为 volatile 访问不建立线程间同步。

​	另外，volatile 访问不是原子的（共时的读和写是[数据竞争](https://zh.cppreference.com/w/c/language/memory_model)），且没有内存定序（非 volatile 内存访问可以自由地重排到 volatile 访问前后）。

​	一个值得注意的例外是 Visual Studio，其中默认设置下，每个 volatile 写拥有释放语义，而每个 volatile 读拥有获得语义（[微软文档](https://learn.microsoft.com/en-us/cpp/cpp/volatile-cpp)），故而可将 volatile 对象用于线程间同步。标准的 `volatile` 语义不可应用于多线程编程，尽管它们在应用到 `[sig_atomic_t](http://zh.cppreference.com/w/c/program/sig_atomic_t)` 对象时，足以用于例如与运行于同一线程的 [signal](https://zh.cppreference.com/w/c/program/signal) 处理函数间的通信。可以使用编译器选项 `/volatile:iso` 恢复和标准一致的行为，当目标平台是 ARM 时这是默认设置。

**示例**

> 本节未完成
>
> 原因：暂无示例

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.17.1/4 memory_order （第 TBD 页）

  - 7.17.3 Order and consistency （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/4 memory_order （第 200 页）

  - 7.17.3 Order and consistency （第 201-203 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/4 memory_order （第 273 页）

  - 7.17.3 Order and consistency （第 275-277 页）

**参阅**

**内存顺序**的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/memory_order)**

**外部链接**

| 1.   | [MOESI 协议](https://en.wikipedia.org/wiki/MOESI_protocol)   |
| ---- | ------------------------------------------------------------ |
| 2.   | [x86-TSO：x86 多处理器上严格而有用的程序员模型](http://www.cl.cam.ac.uk/~pes20/weakmemory/cacm.pdf) P. Sewell 等，2010 |
| 3.   | [ARM 及 POWER 宽松内存模型的入门教程](http://www.cl.cam.ac.uk/~pes20/ppc-supplemental/test7.pdf) P. Sewell 等，2012 |
| 4.   | [MESIF：点对点互联的两跳缓存一致性协议](https://researchspace.auckland.ac.nz/bitstream/handle/2292/11594/MESIF-2009.pdf?sequence=6) J.R. Goodman, H.H.J. Hum，2009 |
| 5.   | [内存模型](https://research.swtch.com/mm) Russ Cox, 2021     |

> 本节未完成
>
> 原因：让我们在 QPI、MOESI，也许还有 Dragon 上找到好的参考资料。






## 宏



### ATOMIC_BOOL_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_CHAR16_T_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_CHAR32_T_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_CHAR_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_FLAG_INIT

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_FLAG_INIT](https://zh.cppreference.com/w/c/atomic/ATOMIC_FLAG_INIT)

作用：初始化新的 `atomic_flag`   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_FLAG_INIT /* 未指明 */// (C11 起)
```

​	展开成能用于初始化 [atomic_flag](https://zh.cppreference.com/w/c/atomic/atomic_flag) 类型为清除状态的初始化器。不用此宏初始化的 `atomic_flag` 的值不确定。

**示例**

```c
#include <stdatomic.h>
 
atomic_flag flag = ATOMIC_FLAG_INIT;
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 ATOMIC_FLAG_INIT （第 200 页）

  - 7.17.8/4 ATOMIC_FLAG_INIT （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 ATOMIC_FLAG_INIT （第 273 页）

  - 7.17.8/4 ATOMIC_FLAG_INIT （第 285 页）

**参阅**

| [ATOMIC_VAR_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_VAR_INIT) | 初始化新的原子对象 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| [atomic_flag (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag) | 免锁原子布尔标志 (结构体)   |
| **ATOMIC_FLAG_INIT** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/ATOMIC_FLAG_INIT)** |                             |





### ATOMIC_INT_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_LLONG_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_LONG_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_POINTER_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_SHORT_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### ATOMIC_VAR_INIT

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_VAR_INIT](https://zh.cppreference.com/w/c/atomic/ATOMIC_VAR_INIT)

作用：初始化新的原子对象  (宏函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_VAR_INIT(value) /* 未指明 */// (C11 起) (C17 弃用) (C23 移除)
```

​	展开成能用于初始化类型同 `value` 的原子对象的表达式。

​	拥有自动存储期而不显式初始化的原子对象的初始值不确定。不过，静态和线程局域对象的默认（零）初始化产生合法值。

​	初始化原子对象时，任何同时访问，即使通过原子操作，都是数据竞争（若立即将地址以 [memory_order_relaxed](https://zh.cppreference.com/w/c/atomic/memory_order) 操作传递给另一线程，就可能发生）。

**注解**

​	此宏曾是 C11 原子类型设计早期方案的一部分。在 C11 中不需要，于 C17 中弃用并于 C23 中移除。

**缺陷报告**

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为             | 正确行为 |
| ------------------------------------------------------------ | ------ | ------------------------ | -------- |
| [DR 485](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_485) | C11    | 规范冗余并与核心语言矛盾 | 已更正   |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.2.1 The ATOMIC_VAR_INIT macro （第 201 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.2.1 The ATOMIC_VAR_INIT macro （第 274 页）

**参阅**

| [ATOMIC_FLAG_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_FLAG_INIT) | 初始化新的 `[atomic_flag](http://zh.cppreference.com/w/c/atomic/atomic_flag)` (宏常量) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **ATOMIC_VAR_INIT** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/ATOMIC_VAR_INIT)** |                                                              |





### ATOMIC_WCHAR_T_LOCK_FREE

原址：[https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts)

作用：指示给定的原子类型为免锁   (宏常量)

备注：
```c
// 在标头 <stdatomic.h> 定义
#define ATOMIC_BOOL_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_CHAR16_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_CHAR32_T_LOCK_FREE /* 由实现定义 */
#define ATOMIC_WCHAR_T_LOCK_FREE  /* 由实现定义 */
#define ATOMIC_SHORT_LOCK_FREE    /* 由实现定义 */
#define ATOMIC_INT_LOCK_FREE      /* 由实现定义 */
#define ATOMIC_LONG_LOCK_FREE     /* 由实现定义 */
#define ATOMIC_LLONG_LOCK_FREE    /* 由实现定义 */

#define ATOMIC_POINTER_LOCK_FREE  /* 由实现定义 */// (C11 起)
#define ATOMIC_CHAR8_T_LOCK_FREE  /* 由实现定义 */// (C23 起)
```

​	展开成求值为 `0` 或 `1` 或 `2` 的[预处理器常量表达式](https://zh.cppreference.com/w/c/language/constant_expression)，它指示对应[原子类型](https://zh.cppreference.com/w/c/thread#.E5.8E.9F.E5.AD.90.E6.93.8D.E4.BD.9C)（有符号及无符号一同）的免锁属性。

| 值   | 解释               |
| ---- | ------------------ |
| `0`  | 该原子类型决不免锁 |
| `1`  | 该原子类型有时免锁 |
| `2`  | 该原子类型始终免锁 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.1/3 atomic lock-free macros （第 200 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.1/3 atomic lock-free macros （第 273 页）





### __STDC_VERSION_STDATOMIC_H__

原址：

作用：

备注：





### kill_dependency

原址：[https://zh.cppreference.com/w/c/atomic/kill_dependency](https://zh.cppreference.com/w/c/atomic/kill_dependency)

作用：打破 `memory_order_consume` 的依赖链   (宏函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
A kill_dependency(A y);// (C11 起)
```

​	告知编译器： [memory_order_consume](https://zh.cppreference.com/w/c/atomic/memory_order) 原子加载操作所开始的依赖树不再延伸过 `kill_dependency` 的返回值；即该参数不把依赖带入返回值。

​	函数实现为宏。 `A` 为 `y` 的类型。

**参数**

| y    | -    | 要从依赖树移除返回值的表达式 |
| ---- | ---- | ---------------------------- |
|      |      |                              |

**返回值**

​	返回 `y` ，它不再是依赖树的一部分。

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.17.3.1 The kill_dependency macro （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.3.1 The kill_dependency macro （第 203-204 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.3.1 The kill_dependency macro （第 278 页）

**参阅**

**kill_dependency** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/kill_dependency)**






## 函数



### atomic_compare_exchange_strong

原址：[https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange)

作用：若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_compare_exchange_strong( volatile A* obj,
                                      C* expected, C desired );// (1)(C11 起)
_Bool atomic_compare_exchange_weak( volatile A *obj, 
                                    C* expected, C desired );// (2)(C11 起)
_Bool atomic_compare_exchange_strong_explicit( volatile A* obj, 
                                               C* expected, C desired,
                                               memory_order succ, 

                                               memory_order fail );// (3)(C11 起)
_Bool atomic_compare_exchange_weak_explicit( volatile A *obj, 
                                             C* expected, C desired,
                                             memory_order succ, 

                                             memory_order fail );// (4)(C11 起)
```

​	原子地比较 `obj` 所指向对象的内存的内容与 `expected` 所指向的内存的内容。若它们逐位相等，则以 `desired` 替换前者（进行读修改写操作）。否则，将 `obj` 所指向的实际内存内容加载到 `*expected` （进行加载操作）。

​	读修改写和加载操作的内存模型分别为 `succ` 和 `fail` 。 (1-2) 版本默认使用 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 。

​	函数的弱形式（ (2) 与 (4) ）允许虚假失败，即表现为如同 `*obj != *expected` ，即使它们相等。当比较并交换在循环中时，弱版本在某些平台上会生成更好的性能。在弱版本会要求循环而强版本不要求时，最好用强版本。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_compare_exchange)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj      | -    | 指向要测试及修改的原子对象的指针                             |
| -------- | ---- | ------------------------------------------------------------ |
| expected | -    | 指向期待在原子对象中找到的值的指针                           |
| desired  | -    | 要存储于原子对象的值，若它得到期待                           |
| succ     | -    | 读修改写操作的内存同步顺序，若比较成功。容许所有值。         |
| fail     | -    | 加载操作的内存同步顺序，若比较失败。不能为 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_acq_rel](https://zh.cppreference.com/w/c/atomic/memory_order) 且不能指定强于 `succ` 的顺序 |

**返回值**

​	比较结果：若 `*obj` 等于 `*expected` 则为 `true` ，否则 `false` 。

**注解**

​	`atomic_compare_exchange_*` 一族函数的行为表现为如同原子地执行下列代码：

```
if (memcmp(obj, expected, sizeof *obj) == 0) {
    memcpy(obj, &desired, sizeof *obj);
    return true
} else {
    memcpy(expected, obj, sizeof *obj);
    return false;
}
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 207 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 283-284 页）

**参阅**

| [atomic_exchange (C11)<br />atomic_exchange_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_exchange) | 将原子对象的值与一个值交换 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **atomic_compare_exchange_weak, atomic_compare_exchange_strong, atomic_compare_exchange_weak_explicit, atomic_compare_exchange_strong_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_compare_exchange)** |                                   |





### atomic_compare_exchange_strong_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange)

作用：若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_compare_exchange_strong( volatile A* obj,
                                      C* expected, C desired );// (1)(C11 起)
_Bool atomic_compare_exchange_weak( volatile A *obj, 
                                    C* expected, C desired );// (2)(C11 起)
_Bool atomic_compare_exchange_strong_explicit( volatile A* obj, 
                                               C* expected, C desired,
                                               memory_order succ, 

                                               memory_order fail );// (3)(C11 起)
_Bool atomic_compare_exchange_weak_explicit( volatile A *obj, 
                                             C* expected, C desired,
                                             memory_order succ, 

                                             memory_order fail );// (4)(C11 起)
```

​	原子地比较 `obj` 所指向对象的内存的内容与 `expected` 所指向的内存的内容。若它们逐位相等，则以 `desired` 替换前者（进行读修改写操作）。否则，将 `obj` 所指向的实际内存内容加载到 `*expected` （进行加载操作）。

​	读修改写和加载操作的内存模型分别为 `succ` 和 `fail` 。 (1-2) 版本默认使用 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 。

​	函数的弱形式（ (2) 与 (4) ）允许虚假失败，即表现为如同 `*obj != *expected` ，即使它们相等。当比较并交换在循环中时，弱版本在某些平台上会生成更好的性能。在弱版本会要求循环而强版本不要求时，最好用强版本。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_compare_exchange)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj      | -    | 指向要测试及修改的原子对象的指针                             |
| -------- | ---- | ------------------------------------------------------------ |
| expected | -    | 指向期待在原子对象中找到的值的指针                           |
| desired  | -    | 要存储于原子对象的值，若它得到期待                           |
| succ     | -    | 读修改写操作的内存同步顺序，若比较成功。容许所有值。         |
| fail     | -    | 加载操作的内存同步顺序，若比较失败。不能为 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_acq_rel](https://zh.cppreference.com/w/c/atomic/memory_order) 且不能指定强于 `succ` 的顺序 |

**返回值**

​	比较结果：若 `*obj` 等于 `*expected` 则为 `true` ，否则 `false` 。

**注解**

​	`atomic_compare_exchange_*` 一族函数的行为表现为如同原子地执行下列代码：

```
if (memcmp(obj, expected, sizeof *obj) == 0) {
    memcpy(obj, &desired, sizeof *obj);
    return true
} else {
    memcpy(expected, obj, sizeof *obj);
    return false;
}
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 207 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 283-284 页）

**参阅**

| [atomic_exchange (C11)<br />atomic_exchange_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_exchange) | 将原子对象的值与一个值交换 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **atomic_compare_exchange_weak, atomic_compare_exchange_strong, atomic_compare_exchange_weak_explicit, atomic_compare_exchange_strong_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_compare_exchange)** |                                   |





### atomic_compare_exchange_weak

原址：[https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange)

作用：若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_compare_exchange_strong( volatile A* obj,
                                      C* expected, C desired );// (1)(C11 起)
_Bool atomic_compare_exchange_weak( volatile A *obj, 
                                    C* expected, C desired );// (2)(C11 起)
_Bool atomic_compare_exchange_strong_explicit( volatile A* obj, 
                                               C* expected, C desired,
                                               memory_order succ, 

                                               memory_order fail );// (3)(C11 起)
_Bool atomic_compare_exchange_weak_explicit( volatile A *obj, 
                                             C* expected, C desired,
                                             memory_order succ, 

                                             memory_order fail );// (4)(C11 起)
```

​	原子地比较 `obj` 所指向对象的内存的内容与 `expected` 所指向的内存的内容。若它们逐位相等，则以 `desired` 替换前者（进行读修改写操作）。否则，将 `obj` 所指向的实际内存内容加载到 `*expected` （进行加载操作）。

​	读修改写和加载操作的内存模型分别为 `succ` 和 `fail` 。 (1-2) 版本默认使用 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 。

​	函数的弱形式（ (2) 与 (4) ）允许虚假失败，即表现为如同 `*obj != *expected` ，即使它们相等。当比较并交换在循环中时，弱版本在某些平台上会生成更好的性能。在弱版本会要求循环而强版本不要求时，最好用强版本。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_compare_exchange)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj      | -    | 指向要测试及修改的原子对象的指针                             |
| -------- | ---- | ------------------------------------------------------------ |
| expected | -    | 指向期待在原子对象中找到的值的指针                           |
| desired  | -    | 要存储于原子对象的值，若它得到期待                           |
| succ     | -    | 读修改写操作的内存同步顺序，若比较成功。容许所有值。         |
| fail     | -    | 加载操作的内存同步顺序，若比较失败。不能为 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_acq_rel](https://zh.cppreference.com/w/c/atomic/memory_order) 且不能指定强于 `succ` 的顺序 |

**返回值**

​	比较结果：若 `*obj` 等于 `*expected` 则为 `true` ，否则 `false` 。

**注解**

​	`atomic_compare_exchange_*` 一族函数的行为表现为如同原子地执行下列代码：

```
if (memcmp(obj, expected, sizeof *obj) == 0) {
    memcpy(obj, &desired, sizeof *obj);
    return true
} else {
    memcpy(expected, obj, sizeof *obj);
    return false;
}
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 207 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 283-284 页）

**参阅**

| [atomic_exchange (C11)<br />atomic_exchange_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_exchange) | 将原子对象的值与一个值交换 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **atomic_compare_exchange_weak, atomic_compare_exchange_strong, atomic_compare_exchange_weak_explicit, atomic_compare_exchange_strong_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_compare_exchange)** |                                   |





### atomic_compare_exchange_weak_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange)

作用：若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_compare_exchange_strong( volatile A* obj,
                                      C* expected, C desired );// (1)(C11 起)
_Bool atomic_compare_exchange_weak( volatile A *obj, 
                                    C* expected, C desired );// (2)(C11 起)
_Bool atomic_compare_exchange_strong_explicit( volatile A* obj, 
                                               C* expected, C desired,
                                               memory_order succ, 

                                               memory_order fail );// (3)(C11 起)
_Bool atomic_compare_exchange_weak_explicit( volatile A *obj, 
                                             C* expected, C desired,
                                             memory_order succ, 

                                             memory_order fail );// (4)(C11 起)
```

​	原子地比较 `obj` 所指向对象的内存的内容与 `expected` 所指向的内存的内容。若它们逐位相等，则以 `desired` 替换前者（进行读修改写操作）。否则，将 `obj` 所指向的实际内存内容加载到 `*expected` （进行加载操作）。

​	读修改写和加载操作的内存模型分别为 `succ` 和 `fail` 。 (1-2) 版本默认使用 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 。

​	函数的弱形式（ (2) 与 (4) ）允许虚假失败，即表现为如同 `*obj != *expected` ，即使它们相等。当比较并交换在循环中时，弱版本在某些平台上会生成更好的性能。在弱版本会要求循环而强版本不要求时，最好用强版本。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_compare_exchange)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj      | -    | 指向要测试及修改的原子对象的指针                             |
| -------- | ---- | ------------------------------------------------------------ |
| expected | -    | 指向期待在原子对象中找到的值的指针                           |
| desired  | -    | 要存储于原子对象的值，若它得到期待                           |
| succ     | -    | 读修改写操作的内存同步顺序，若比较成功。容许所有值。         |
| fail     | -    | 加载操作的内存同步顺序，若比较失败。不能为 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_acq_rel](https://zh.cppreference.com/w/c/atomic/memory_order) 且不能指定强于 `succ` 的顺序 |

**返回值**

​	比较结果：若 `*obj` 等于 `*expected` 则为 `true` ，否则 `false` 。

**注解**

​	`atomic_compare_exchange_*` 一族函数的行为表现为如同原子地执行下列代码：

```
if (memcmp(obj, expected, sizeof *obj) == 0) {
    memcpy(obj, &desired, sizeof *obj);
    return true
} else {
    memcpy(expected, obj, sizeof *obj);
    return false;
}
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 207 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.4 The atomic_compare_exchange generic functions （第 283-284 页）

**参阅**

| [atomic_exchange (C11)<br />atomic_exchange_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_exchange) | 将原子对象的值与一个值交换 (函数) |
| ------------------------------------------------------------ | --------------------------------- |
| **atomic_compare_exchange_weak, atomic_compare_exchange_strong, atomic_compare_exchange_weak_explicit, atomic_compare_exchange_strong_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_compare_exchange)** |                                   |





### atomic_exchange

原址：[https://zh.cppreference.com/w/c/atomic/atomic_exchange](https://zh.cppreference.com/w/c/atomic/atomic_exchange)

作用：将原子对象的值与一个值交换   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_exchange( volatile A* obj, C desired );// (1)(C11 起)
C atomic_exchange_explicit( volatile A* obj, C desired, memory_order order );// (2)(C11 起)
```

​	原子地以 `desired` 替换 `obj` 所指向的对象的值，并返回 `obj` 先前所保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_exchange)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj     | -    | 指向要修改的原子对象的指针           |
| ------- | ---- | ------------------------------------ |
| desired | -    | 用以替换原子对象的值                 |
| order   | -    | 此操作的内存同步顺序标签：允许所有值 |

**返回值**

​	`obj` 所指向的原子对象先前所保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.3 The atomic_exchange generic functions （第 207 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.3 The atomic_exchange generic functions （第 283 页）

**参阅**

| [atomic_compare_exchange_strong (C11)<br />atomic_compare_exchange_strong_explicit (C11)<br />atomic_compare_exchange_weak<br />atomic_compare_exchange_weak_explicit<br />](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange) | 若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **atomic_exchange, atomic_exchange_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_exchange)** |                                                              |





### atomic_exchange_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_exchange](https://zh.cppreference.com/w/c/atomic/atomic_exchange)

作用：将原子对象的值与一个值交换   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_exchange( volatile A* obj, C desired );// (1)(C11 起)
C atomic_exchange_explicit( volatile A* obj, C desired, memory_order order );// (2)(C11 起)
```

​	原子地以 `desired` 替换 `obj` 所指向的对象的值，并返回 `obj` 先前所保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_exchange)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj     | -    | 指向要修改的原子对象的指针           |
| ------- | ---- | ------------------------------------ |
| desired | -    | 用以替换原子对象的值                 |
| order   | -    | 此操作的内存同步顺序标签：允许所有值 |

**返回值**

​	`obj` 所指向的原子对象先前所保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.3 The atomic_exchange generic functions （第 207 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.3 The atomic_exchange generic functions （第 283 页）

**参阅**

| [atomic_compare_exchange_strong (C11)<br />atomic_compare_exchange_strong_explicit (C11)<br />atomic_compare_exchange_weak<br />atomic_compare_exchange_weak_explicit<br />](https://zh.cppreference.com/w/c/atomic/atomic_compare_exchange) | 若原子对象的旧值为所期待的值则将之与一个值交换，否则读取该旧值 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| **atomic_exchange, atomic_exchange_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_exchange)** |                                                              |





### atomic_fetch_add

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_add](https://zh.cppreference.com/w/c/atomic/atomic_fetch_add)

作用：原子加法   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_add( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_add_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 的旧值的加法结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_add)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

​	对于有符号整数类型，定义算术为使用补码表示。无未定义结果。对于指针类型，结果可能是未定义地址，但运算不会另有未定义行为。

**参数**

| obj   | -    | 指向要修改的原子对象的指针       |
| ----- | ---- | -------------------------------- |
| arg   | -    | 要加到存储于原子对象中的值的值   |
| order | -    | 此操作的内存同步顺序：容许所有值 |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**示例**

```c
#include <stdio.h>
#include <threads.h>
#include <stdatomic.h>
 
atomic_int acnt;
int cnt;
 
int f(void* thr_data)
{
    for(int n = 0; n < 1000; ++n) {
        atomic_fetch_add_explicit(&acnt, 1, memory_order_relaxed); // 原子的
        ++cnt; // 未定义行为，实际上会失去一些更新
    }
    return 0;
}
 
int main(void)
{
    thrd_t thr[10];
    for(int n = 0; n < 10; ++n)
        thrd_create(&thr[n], f, NULL);
    for(int n = 0; n < 10; ++n)
        thrd_join(thr[n], NULL);
 
    printf("The atomic counter is %u\n", acnt);
    printf("The non-atomic counter is %u\n", cnt);
}
```

​	可能的输出：

```txt
The atomic counter is 10000
The non-atomic counter is 9511
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_sub (C11)<br />atomic_fetch_sub_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub) | 原子减法 (函数) |
| ------------------------------------------------------------ | --------------- |
| **atomic_fetch_add, atomic_fetch_add_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_add)** |                 |





### atomic_fetch_add_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_add](https://zh.cppreference.com/w/c/atomic/atomic_fetch_add)

作用：原子加法   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_add( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_add_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 的旧值的加法结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_add)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

​	对于有符号整数类型，定义算术为使用补码表示。无未定义结果。对于指针类型，结果可能是未定义地址，但运算不会另有未定义行为。

**参数**

| obj   | -    | 指向要修改的原子对象的指针       |
| ----- | ---- | -------------------------------- |
| arg   | -    | 要加到存储于原子对象中的值的值   |
| order | -    | 此操作的内存同步顺序：容许所有值 |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**示例**

```c
#include <stdio.h>
#include <threads.h>
#include <stdatomic.h>
 
atomic_int acnt;
int cnt;
 
int f(void* thr_data)
{
    for(int n = 0; n < 1000; ++n) {
        atomic_fetch_add_explicit(&acnt, 1, memory_order_relaxed); // 原子的
        ++cnt; // 未定义行为，实际上会失去一些更新
    }
    return 0;
}
 
int main(void)
{
    thrd_t thr[10];
    for(int n = 0; n < 10; ++n)
        thrd_create(&thr[n], f, NULL);
    for(int n = 0; n < 10; ++n)
        thrd_join(thr[n], NULL);
 
    printf("The atomic counter is %u\n", acnt);
    printf("The non-atomic counter is %u\n", cnt);
}
```

​	可能的输出：

```txt
The atomic counter is 10000
The non-atomic counter is 9511
```

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_sub (C11)<br />atomic_fetch_sub_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub) | 原子减法 (函数) |
| ------------------------------------------------------------ | --------------- |
| **atomic_fetch_add, atomic_fetch_add_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_add)** |                 |





### atomic_fetch_and

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_and](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and)

作用：原子逐位与（AND）  (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_and( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_and_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 的旧值逐位与的结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读-修改-写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_and)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针         |
| ----- | ---- | ---------------------------------- |
| arg   | -    | 要逐位与到存储于原子对象中的值的值 |
| order | -    | 此操作的内存同步顺序：容许所有值   |

**返回值**

​	`obj`所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_or (C11)<br />atomic_fetch_or_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or) | 原子逐位或（OR） (函数)    |
| ------------------------------------------------------------ | -------------------------- |
| [atomic_fetch_xor (C11)<br />atomic_fetch_xor_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor) | 原子逐位异或（XOR） (函数) |
| **atomic_fetch_and, atomic_fetch_and_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_and)** |                            |





### atomic_fetch_and_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_and](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and)

作用：原子逐位与（AND）  (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_and( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_and_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 的旧值逐位与的结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读-修改-写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_and)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针         |
| ----- | ---- | ---------------------------------- |
| arg   | -    | 要逐位与到存储于原子对象中的值的值 |
| order | -    | 此操作的内存同步顺序：容许所有值   |

**返回值**

​	`obj`所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_or (C11)<br />atomic_fetch_or_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or) | 原子逐位或（OR） (函数)    |
| ------------------------------------------------------------ | -------------------------- |
| [atomic_fetch_xor (C11)<br />atomic_fetch_xor_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor) | 原子逐位异或（XOR） (函数) |
| **atomic_fetch_and, atomic_fetch_and_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_and)** |                            |





### atomic_fetch_or

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_or](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or)

作用：原子逐位或（OR）  (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_or( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_or_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 旧值的逐位或结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_or)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针         |
| ----- | ---- | ---------------------------------- |
| arg   | -    | 要逐位或到存储于原子对象中的值的值 |
| order | -    | 此操作的内存同步顺序：容许所有值   |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_and (C11)<br />atomic_fetch_and_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and) | 原子逐位与（AND） (函数)   |
| ------------------------------------------------------------ | -------------------------- |
| [atomic_fetch_xor (C11)<br />atomic_fetch_xor_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor) | 原子逐位异或（XOR） (函数) |
| **atomic_fetch_or, atomic_fetch_or_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_or)** |                            |





### atomic_fetch_or_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_or](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or)

作用：原子逐位或（OR）  (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_or( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_or_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 旧值的逐位或结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_or)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针         |
| ----- | ---- | ---------------------------------- |
| arg   | -    | 要逐位或到存储于原子对象中的值的值 |
| order | -    | 此操作的内存同步顺序：容许所有值   |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_and (C11)<br />atomic_fetch_and_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and) | 原子逐位与（AND） (函数)   |
| ------------------------------------------------------------ | -------------------------- |
| [atomic_fetch_xor (C11)<br />atomic_fetch_xor_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor) | 原子逐位异或（XOR） (函数) |
| **atomic_fetch_or, atomic_fetch_or_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_or)** |                            |





### atomic_fetch_sub

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub](https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub)

作用：原子减法   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_sub( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_sub_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `*obj` 的旧值减去 `arg` 的结果原子地替换 `obj` 的所指向值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_sub)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

​	对于有符号整数类型，定义算术为使用补码表示。无未定义结果。对于指针类型，结果可能是未定义地址，但运算不会另有未定义行为。

**参数**

| obj   | -    | 指向要修改的原子对象的指针       |
| ----- | ---- | -------------------------------- |
| arg   | -    | 要从存储于原子对象中的值减去的值 |
| order | -    | 此操作的内存同步顺序：容许所有值 |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_add (C11)<br />atomic_fetch_add_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_add) | 原子加法 (函数) |
| ------------------------------------------------------------ | --------------- |
| **atomic_fetch_sub, atomic_fetch_sub_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_sub)** |                 |





### atomic_fetch_sub_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub](https://zh.cppreference.com/w/c/atomic/atomic_fetch_sub)

作用：原子减法   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_sub( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_sub_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `*obj` 的旧值减去 `arg` 的结果原子地替换 `obj` 的所指向值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_sub)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

​	对于有符号整数类型，定义算术为使用补码表示。无未定义结果。对于指针类型，结果可能是未定义地址，但运算不会另有未定义行为。

**参数**

| obj   | -    | 指向要修改的原子对象的指针       |
| ----- | ---- | -------------------------------- |
| arg   | -    | 要从存储于原子对象中的值减去的值 |
| order | -    | 此操作的内存同步顺序：容许所有值 |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_add (C11)<br />atomic_fetch_add_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_add) | 原子加法 (函数) |
| ------------------------------------------------------------ | --------------- |
| **atomic_fetch_sub, atomic_fetch_sub_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_sub)** |                 |





### atomic_fetch_xor

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor)

作用：原子逐位异或（XOR）  (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_xor( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_xor_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 的旧值逐位异或的结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_xor)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针           |
| ----- | ---- | ------------------------------------ |
| arg   | -    | 要逐位异或到存储于原子对象中的值的值 |
| order | -    | 此操作的内存同步顺序：容许所有值     |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_or (C11)<br />atomic_fetch_or_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or) | 原子逐位或（OR） (函数)  |
| ------------------------------------------------------------ | ------------------------ |
| [atomic_fetch_and (C11)<br />atomic_fetch_and_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and) | 原子逐位与（AND） (函数) |
| **atomic_fetch_xor, atomic_fetch_xor_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_xor)** |                          |





### atomic_fetch_xor_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor](https://zh.cppreference.com/w/c/atomic/atomic_fetch_xor)

作用：原子逐位异或（XOR）  (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_fetch_xor( volatile A* obj, M arg );// (1)(C11 起)
C atomic_fetch_xor_explicit( volatile A* obj, M arg, memory_order order );// (2)(C11 起)
```

​	以 `arg` 和 `*obj` 的旧值逐位异或的结果原子地替换 `obj` 所指向的值，并返回 `*obj` 先前保有的值。此操作是读修改写操作。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 若 `A` 为原子整数类型则 `M` 是对应于 `A` 的非原子类型，或若 `A` 为原子指针类型则 `M` 为 [ptrdiff_t](https://zh.cppreference.com/w/c/types/ptrdiff_t)。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_fetch_xor)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针           |
| ----- | ---- | ------------------------------------ |
| arg   | -    | 要逐位异或到存储于原子对象中的值的值 |
| order | -    | 此操作的内存同步顺序：容许所有值     |

**返回值**

​	`obj` 所指向的原子对象先前保有的值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 208 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.5 The atomic_fetch and modify generic functions （第 284-285 页）

**参阅**

| [atomic_fetch_or (C11)<br />atomic_fetch_or_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_or) | 原子逐位或（OR） (函数)  |
| ------------------------------------------------------------ | ------------------------ |
| [atomic_fetch_and (C11)<br />atomic_fetch_and_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_fetch_and) | 原子逐位与（AND） (函数) |
| **atomic_fetch_xor, atomic_fetch_xor_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_fetch_xor)** |                          |





### atomic_flag_clear

原址：[https://zh.cppreference.com/w/c/atomic/atomic_flag_clear](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear)

作用：设置 atomic_flag 为 false   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_flag_clear( volatile atomic_flag* obj );// (1)(C11 起)
void atomic_flag_clear_explicit( volatile atomic_flag* obj, memory_order order );// (2)(C11 起)
```

​	原子地更改 `obj` 所指向的 `atomic_flag` 状态为清除（ `false` ）。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本根据 `order` 排序内存访问。

​	参数为指向 volatile 原子标志的指针，以接受非 volatile 和 [volatile](https://zh.cppreference.com/w/c/language/volatile) （如内存映射 I/O ）的原子标志。

**参数**

| obj   | -    | 指向要修改的 `atomic_flag` 对象的指针 |
| ----- | ---- | ------------------------------------- |
| order | -    | 此操作所用的内存同步顺序：允许所有值  |

**返回值**

​	（无）

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.8.2 The atomic_flag_clear functions （第 209 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.8.2 The atomic_flag_clear functions （第 286 页）

**参阅**

| [atomic_flag_test_and_set (C11)<br />atomic_flag_test_and_set_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set) | 设置 `atomic_flag` 为 `true` 并返回旧值 (函数) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| **atomic_flag_clear, atomic_flag_clear_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_flag_clear)** |                                                |





### atomic_flag_clear_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_flag_clear](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear)

作用：设置 atomic_flag 为 false   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_flag_clear( volatile atomic_flag* obj );// (1)(C11 起)
void atomic_flag_clear_explicit( volatile atomic_flag* obj, memory_order order );// (2)(C11 起)
```

​	原子地更改 `obj` 所指向的 `atomic_flag` 状态为清除（ `false` ）。第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本根据 `order` 排序内存访问。

​	参数为指向 volatile 原子标志的指针，以接受非 volatile 和 [volatile](https://zh.cppreference.com/w/c/language/volatile) （如内存映射 I/O ）的原子标志。

**参数**

| obj   | -    | 指向要修改的 `atomic_flag` 对象的指针 |
| ----- | ---- | ------------------------------------- |
| order | -    | 此操作所用的内存同步顺序：允许所有值  |

**返回值**

​	（无）

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.8.2 The atomic_flag_clear functions （第 209 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.8.2 The atomic_flag_clear functions （第 286 页）

**参阅**

| [atomic_flag_test_and_set (C11)<br />atomic_flag_test_and_set_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set) | 设置 `atomic_flag` 为 `true` 并返回旧值 (函数) |
| ------------------------------------------------------------ | ---------------------------------------------- |
| **atomic_flag_clear, atomic_flag_clear_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_flag_clear)** |                                                |





### atomic_flag_test_and_set

原址：[https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set)

作用：设置 atomic_flag 为 true 并返回旧值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_flag_test_and_set( volatile atomic_flag* obj );// (1)(C11 起)
_Bool atomic_flag_test_and_set_explicit( volatile atomic_flag* obj, memory_order order );// (2)(C11 起)
```

​	原子地更改 `obj` 所指向的 `atomic_flag` 的状态为设置（ `true` ），并返回先前值。第一版本按 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按 `order` 排序内存访问。

​	参数是为指向 `volatile atomic_flag` 的指针，以接受非 volatile 和 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如映射到内存的 I/O ）的 `atomic_flag` 。

**参数**

| obj   | -    | 指向要修改的 `atomic_flag` 对象的指针 |
| ----- | ---- | ------------------------------------- |
| order | -    | 此操作所用的内存同步顺序：容许所有值  |

**返回值**

​	`obj` 所指向的 `atomic_flag` 的先前值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.8.1 The atomic_flag_test_and_set functions （第 209 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.8.1 The atomic_flag_test_and_set functions （第 285-286 页）

**参阅**

| [atomic_flag_clear (C11)<br />atomic_flag_clear_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear) | 设置 `atomic_flag` 为 `false` (函数) |
| ------------------------------------------------------------ | ------------------------------------ |
| **atomic_flag_test_and_set, atomic_flag_test_and_set_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_flag_test_and_set)** |                                      |





### atomic_flag_test_and_set_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set](https://zh.cppreference.com/w/c/atomic/atomic_flag_test_and_set)

作用：设置 atomic_flag 为 true 并返回旧值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_flag_test_and_set( volatile atomic_flag* obj );// (1)(C11 起)
_Bool atomic_flag_test_and_set_explicit( volatile atomic_flag* obj, memory_order order );// (2)(C11 起)
```

​	原子地更改 `obj` 所指向的 `atomic_flag` 的状态为设置（ `true` ），并返回先前值。第一版本按 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按 `order` 排序内存访问。

​	参数是为指向 `volatile atomic_flag` 的指针，以接受非 volatile 和 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如映射到内存的 I/O ）的 `atomic_flag` 。

**参数**

| obj   | -    | 指向要修改的 `atomic_flag` 对象的指针 |
| ----- | ---- | ------------------------------------- |
| order | -    | 此操作所用的内存同步顺序：容许所有值  |

**返回值**

​	`obj` 所指向的 `atomic_flag` 的先前值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.8.1 The atomic_flag_test_and_set functions （第 209 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.8.1 The atomic_flag_test_and_set functions （第 285-286 页）

**参阅**

| [atomic_flag_clear (C11)<br />atomic_flag_clear_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_flag_clear) | 设置 `atomic_flag` 为 `false` (函数) |
| ------------------------------------------------------------ | ------------------------------------ |
| **atomic_flag_test_and_set, atomic_flag_test_and_set_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_flag_test_and_set)** |                                      |





### atomic_init

原址：[https://zh.cppreference.com/w/c/atomic/atomic_init](https://zh.cppreference.com/w/c/atomic/atomic_init)

作用：初始化既存的原子对象   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_init( volatile A* obj, C desired );// (C11 起)
```

​	以值 `desired` 初始化默认构造的原子对象 `obj` 。此函数非原子：来自另一线程的共时访问，即使通过原子操作，亦为数据竞争。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_init)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj     | -    | 指向要初始化的原子对象的指针 |
| ------- | ---- | ---------------------------- |
| desired | -    | 用以初始化原子对象的值       |

**返回值**

​	（无）

**注解**

​	`atomic_init` 是初始化动态分配的原子对象的唯一方式。例如：

```
_Atomic int *p = malloc(sizeof(_Atomic int));
atomic_init(p, 42);
```

**引用**

- C23 标准（ISO/IEC 9899:2024）：

  - 7.17.2.2 The atomic_init generic function （第 TBD 页）

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.2.2 The atomic_init generic function （第 201 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.2.2 The atomic_init generic function （第 274-275 页）

**参阅**

| [ATOMIC_VAR_INIT (C11)<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_VAR_INIT) | 初始化新的原子对象 (宏函数) |
| ------------------------------------------------------------ | --------------------------- |
| **atomic_init** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_init)** |                             |





### atomic_is_lock_free

原址：[https://zh.cppreference.com/w/c/atomic/atomic_is_lock_free](https://zh.cppreference.com/w/c/atomic/atomic_is_lock_free)

作用：指示原子对象是否免锁   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
_Bool atomic_is_lock_free( const volatile A* obj );// (C11 起)
```

​	确定所有 `A` 类型对象（`obj`所指向对象的类型）上的原子操作是否为免锁。在任何给定的程序执行中，调用 `atomic_is_lock_free` 的结果对于所有同一类型的指针相同。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_is_lock_free)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj  | -    | 指向要调查的原子对象的指针 |
| ---- | ---- | -------------------------- |
|      |      |                            |

**返回值**

​	若所有 `A` 类型对象的原子操作为免锁，则为 `true` ，否则为 `false` 。

**示例**

```c
#include <stdio.h>
#include <stdatomic.h>
 
_Atomic struct A { int a[100]; } a;
_Atomic struct B { int x, y; } b;
int main(void)
{
    printf("_Atomic struct A is lock free? %s\n", 
            atomic_is_lock_free(&a) ? "true" : "false");
    printf("_Atomic struct B is lock free? %s\n", 
            atomic_is_lock_free(&b) ? "true" : "false");
}
```

​	可能的输出：

```txt
_Atomic struct A is lock free? false
_Atomic struct B is lock free? true
```

**缺陷报告**

​	下列更改行为的缺陷报告追溯地应用于以前出版的 C 标准。

| 缺陷报告                                                     | 应用于 | 出版时的行为       | 正确行为           |
| ------------------------------------------------------------ | ------ | ------------------ | ------------------ |
| [DR 465](https://www.open-std.org/jtc1/sc22/wg14/www/docs/n2396.htm#dr_465) | C11    | 此函数针对每个对象 | 此函数针对每个类型 |

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.5.1 The atomic_is_lock_free generic function （第 205 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.5.1 The atomic_is_lock_free generic function （第 280 页）

**参阅**

| [ATOMIC_BOOL_LOCK_FREE (C11)<br />ATOMIC_CHAR_LOCK_FREE (C11)<br />ATOMIC_CHAR16_T_LOCK_FREE<br />ATOMIC_CHAR32_T_LOCK_FREE<br />ATOMIC_WCHAR_T_LOCK_FREE<br />ATOMIC_SHORT_LOCK_FREE<br />ATOMIC_INT_LOCK_FREE<br />ATOMIC_LONG_LOCK_FREE<br />ATOMIC_LLONG_LOCK_FREE<br />ATOMIC_POINTER_LOCK_FREE<br />](https://zh.cppreference.com/w/c/atomic/ATOMIC_LOCK_FREE_consts) | 指示给定的原子类型为免锁 (宏常量) |
| ------------------------------------------------------------ | --------------------------------- |
| **atomic_is_lock_free** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_is_lock_free)** |                                   |





### atomic_load

原址：[https://zh.cppreference.com/w/c/atomic/atomic_load](https://zh.cppreference.com/w/c/atomic/atomic_load)

作用：从原子对象读取值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_load( const volatile A* obj );// (1)(C11 起)
C atomic_load_explicit( const volatile A* obj, memory_order order );// (2)(C11 起)
```

​	原子地加载并返回 `obj` 所指向的原子对象的当前值。该操作是原子读操作。

​	第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本根按照 `order` 排序内存访问。 `order` 必须是 [memory_order_relaxed](https://zh.cppreference.com/w/c/atomic/memory_order) 、 [memory_order_consume](https://zh.cppreference.com/w/c/atomic/memory_order) 、 [memory_order_acquire](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 之一。否则行为未定义。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_load)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要访问的原子对象的指针 |
| ----- | ---- | -------------------------- |
| order | -    | 此操作的内存同步顺序       |

**返回值**

​	`obj` 所指向原子对象的当前值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.2 The atomic_load generic functions （第 206 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.2 The atomic_load generic functions （第 282 页）

**参阅**

| [atomic_store (C11)<br />atomic_store_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_store) | 存储值到原子对象 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| **atomic_load, atomic_load_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_load)** |                         |





### atomic_load_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_load](https://zh.cppreference.com/w/c/atomic/atomic_load)

作用：从原子对象读取值   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
C atomic_load( const volatile A* obj );// (1)(C11 起)
C atomic_load_explicit( const volatile A* obj, memory_order order );// (2)(C11 起)
```

​	原子地加载并返回 `obj` 所指向的原子对象的当前值。该操作是原子读操作。

​	第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本根按照 `order` 排序内存访问。 `order` 必须是 [memory_order_relaxed](https://zh.cppreference.com/w/c/atomic/memory_order) 、 [memory_order_consume](https://zh.cppreference.com/w/c/atomic/memory_order) 、 [memory_order_acquire](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 之一。否则行为未定义。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_load)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要访问的原子对象的指针 |
| ----- | ---- | -------------------------- |
| order | -    | 此操作的内存同步顺序       |

**返回值**

​	`obj` 所指向原子对象的当前值。

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.2 The atomic_load generic functions （第 206 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.2 The atomic_load generic functions （第 282 页）

**参阅**

| [atomic_store (C11)<br />atomic_store_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_store) | 存储值到原子对象 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| **atomic_load, atomic_load_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_load)** |                         |





### atomic_signal_fence

原址：[https://zh.cppreference.com/w/c/atomic/atomic_signal_fence](https://zh.cppreference.com/w/c/atomic/atomic_signal_fence)

作用：线程与执行于同一线程的信号处理函数间的栅栏   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_signal_fence( memory_order order );// (C11 起)
```

​	在线程和同一线程上执行的信号处理函数之间，建立以 `order` 指示的非原子和宽松原子访问的内存同步顺序。这等价于 [atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) ，除了不为内存顺序产生 CPU 指令。只会以 `order` 指示抑制编译器重排指令。例如，拥有释放语义的栅栏阻止移到读或写到后继写入之后，而拥有获得语义的栅栏阻止移动读或写到前驱读取之前。

**参数**

| order | -    | 此栅栏执行的内存顺序 |
| ----- | ---- | -------------------- |
|       |      |                      |

**返回值**

​	（无）

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.4.2 The atomic_signal_fence function （第 204-205 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.4.2 The atomic_signal_fence function （第 279 页）

**参阅**

| [atomic_thread_fence (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence) | 通用的内存顺序依赖的栅栏同步原语 (函数) |
| ------------------------------------------------------------ | --------------------------------------- |
| **atomic_signal_fence** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_signal_fence)** |                                         |





### atomic_store

原址：[https://zh.cppreference.com/w/c/atomic/atomic_store](https://zh.cppreference.com/w/c/atomic/atomic_store)

作用：存储值到原子对象   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_store( volatile A* obj , C desired );// (1)(C11 起)
void atomic_store_explicit( volatile A* obj, C desired, memory_order order );// (2)(C11 起)
```

​	原子地以 `desired` 替换 `obj` 所指向的原子对象的值。此操作是原子写操作。

​	第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。 `order` 必须为 [memory_order_relaxed](https://zh.cppreference.com/w/c/atomic/memory_order) 、 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 之一。否则行为未定义。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_store)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针 |
| ----- | ---- | -------------------------- |
| order | -    | 用于此操作的内存同步顺序   |

**返回值**

​	（无）

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.1 The atomic_store generic functions （第 206 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.1 The atomic_store generic functions （第 282 页）

**参阅**

| [atomic_load (C11)<br />atomic_load_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_load) | 从原子对象读取值 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| **atomic_store, atomic_store_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_store)** |                         |





### atomic_store_explicit

原址：[https://zh.cppreference.com/w/c/atomic/atomic_store](https://zh.cppreference.com/w/c/atomic/atomic_store)

作用：存储值到原子对象   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_store( volatile A* obj , C desired );// (1)(C11 起)
void atomic_store_explicit( volatile A* obj, C desired, memory_order order );// (2)(C11 起)
```

​	原子地以 `desired` 替换 `obj` 所指向的原子对象的值。此操作是原子写操作。

​	第一版本按照 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 排序内存访问，第二版本按照 `order` 排序内存访问。 `order` 必须为 [memory_order_relaxed](https://zh.cppreference.com/w/c/atomic/memory_order) 、 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 或 [memory_order_seq_cst](https://zh.cppreference.com/w/c/atomic/memory_order) 之一。否则行为未定义。

​	这是为所有[原子对象类型](https://zh.cppreference.com/w/c/language/atomic) `A` 定义的[泛型函数](https://zh.cppreference.com/w/c/language/generic)。其实参为指向 volatile 原子类型的指针，以接受非 volatile 与 [volatile](https://zh.cppreference.com/w/c/language/volatile) （例如内存映射 I/O ）的原子对象，而在对 volatile 原子对象应用此操作时保留 volatile 语义。 `C` 为对应于 `A` 的非原子类型。

​	泛型函数的名字是宏还是声明有外部链接的标识符是未指定的。若为访问实际函数而压制宏定义（例如像 `(atomic_store)(...)` 这样加括号），或程序定义了拥有泛型函数名的外部标识符，则行为未定义。

**参数**

| obj   | -    | 指向要修改的原子对象的指针 |
| ----- | ---- | -------------------------- |
| order | -    | 用于此操作的内存同步顺序   |

**返回值**

​	（无）

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.7.1 The atomic_store generic functions （第 206 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.7.1 The atomic_store generic functions （第 282 页）

**参阅**

| [atomic_load (C11)<br />atomic_load_explicit (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_load) | 从原子对象读取值 (函数) |
| ------------------------------------------------------------ | ----------------------- |
| **atomic_store, atomic_store_explicit** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_store)** |                         |





### atomic_thread_fence

原址：[https://zh.cppreference.com/w/c/atomic/atomic_thread_fence](https://zh.cppreference.com/w/c/atomic/atomic_thread_fence)

作用：通用的内存顺序依赖的栅栏同步原语   (函数)

备注：
```c
// 在标头 <stdatomic.h> 定义
void atomic_thread_fence( memory_order order );// (C11 起)
```

​	按照 `order` 指示，建立非原子和宽松原子访问的的内存同步顺序，而不进行关联的原子操作。例如，线程 A 中先发生于 [memory_order_release](https://zh.cppreference.com/w/c/atomic/memory_order) 栅栏的所有非原子和宽松原子存储，将同步于与线程 B 中 [memory_order_acquire](https://zh.cppreference.com/w/c/atomic/memory_order) 栅栏之后的对同一位置的非原子和宽松原子加载。

**参数**

| order | -    | 此栅栏执行的内存顺序 |
| ----- | ---- | -------------------- |
|       |      |                      |

**返回值**

​	（无）

**引用**

- C17 标准（ISO/IEC 9899:2018）：

  - 7.17.4.1 The atomic_thread_fence function （第 204 页）

- C11 标准（ISO/IEC 9899:2011）：

  - 7.17.4.1 The atomic_thread_fence function （第 278-279 页）

**参阅**

| [atomic_signal_fence (C11)<br />](https://zh.cppreference.com/w/c/atomic/atomic_signal_fence) | 线程与执行于同一线程的信号处理函数间的栅栏 (函数) |
| ------------------------------------------------------------ | ------------------------------------------------- |
| **atomic_thread_fence** 的 **[C++ 文档](https://zh.cppreference.com/w/cpp/atomic/atomic_thread_fence)** |                                                   |






