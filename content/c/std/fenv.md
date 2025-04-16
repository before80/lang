+++
title = "<fenv.h>"
date = 2025-04-16T17:37:26+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型

## 宏

### FE_ALL_EXCEPT

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

```c
#define FE_ALL_EXCEPT  FE_DIVBYZERO | FE_INEXACT | \
                       FE_INVALID | FE_OVERFLOW |  \
                       FE_UNDERFLOW // (C99 起)
```

​	所有受支持浮点数异常的逐位或

​	参见：[FE_DIVBYZERO](#FE_DIVBYZERO)


### FE_DEC_DOWNWARD

原址：

```c
// 仅当实现定义了 __STDC_IEC_60559_DFP__：
#define FE_DEC_DOWNWARD            /* 由实现定义 */
```




### FE_DEC_TONEAREST

原址：

```c
// 仅当实现定义了 __STDC_IEC_60559_DFP__：
#define FE_DEC_TOWARDZERO          /* 由实现定义 */
```




### FE_DEC_TONEARESTFROMZERO

原址：

```c
// 仅当实现定义了 __STDC_IEC_60559_DFP__：
#define FE_DEC_TONEARESTFROMZERO   /* 由实现定义 */
```




### FE_DEC_TOWARDZERO

原址：

```c
// 仅当实现定义了 __STDC_IEC_60559_DFP__：
#define FE_DEC_TOWARDZERO          /* 由实现定义 */
```




### FE_DEC_UPWARD

原址：

```c
// 仅当实现定义了 __STDC_IEC_60559_DFP__：
#define FE_DEC_UPWARD              /* 由实现定义 */
```




### FE_DFL_ENV

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_DFL_ENV](https://zh.cppreference.com/w/c/numeric/fenv/FE_DFL_ENV)

```c
#define FE_DFL_ENV  /* 由实现定义 */ // (C99 起)
```

​	宏常量 **`FE_DFL_ENV`** 展开成 `const fenv_t*` 类型表达式，指向默认浮点数环境，即在程序启动时加载的浮点数环境的完整副本。

​	实现可以支持以 `FE_` 后随大写字母开始，且拥有 `const fenv_t*` 类型的附加宏。

**示例**



```c
#include <stdio.h>
#include <fenv.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    printf("\n");
}
 
void show_fe_rounding_method(void)
{
    printf("current rounding method:    ");
    switch (fegetround()) {
           case FE_TONEAREST:  printf ("FE_TONEAREST");  break;
           case FE_DOWNWARD:   printf ("FE_DOWNWARD");   break;
           case FE_UPWARD:     printf ("FE_UPWARD");     break;
           case FE_TOWARDZERO: printf ("FE_TOWARDZERO"); break;
           default:            printf ("unknown");
    };
    printf("\n");
}
 
void show_fe_environment(void)
{
    show_fe_exceptions();
    show_fe_rounding_method();
} 
 
int main(void)
{
    printf("On startup:\n");
    show_fe_environment();
 
    // 更改环境
    fesetround(FE_DOWNWARD);     // 更改舍入模式
    feraiseexcept(FE_INVALID);   // 引发异常
    printf("\nBefore restoration:\n");
    show_fe_environment();
 
    fesetenv(FE_DFL_ENV);    // 恢复
    printf("\nAfter restoring default environment:\n");
    show_fe_environment();
}
```

​	输出：

```txt
On startup:
current exceptions raised:  none
current rounding method:    FE_TONEAREST
 
Before restoration:
current exceptions raised:  FE_INVALID
current rounding method:    FE_DOWNWARD
 
After restoring default environment:
current exceptions raised:  none
current rounding method:    FE_TONEAREST
```


### FE_DFL_MODE

原址：

```c
```




### FE_DIVBYZERO

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

```c
#define FE_DIVBYZERO    /* 由实现定义的二的幂 */ // (C99 起)
```

​	出现于之前浮点数运算的极点错误

​	所有这些宏常量（除了 **FE_ALL_EXCEPT**）都展开成二的不同次幂的整数常量表达式，唯一地鉴别所有受支持浮点数异常。每个宏仅若受支持才得到定义。

​	宏常量 **FE_ALL_EXCEPT** 展开成所有其他 `FE_*` 的逐位或，且始终有定义，若实现不支持浮点数异常，则为零。

| 常量            | 解释                                           |
| --------------- | ---------------------------------------------- |
| `FE_DIVBYZERO`  | 出现于之前浮点数运算的极点错误                 |
| `FE_INEXACT`    | 不准确结果：必须舍入以存储之前浮点数运算的结果 |
| `FE_INVALID`    | 出现于之前浮点数运算的定义域错误               |
| `FE_OVERFLOW`   | 之前浮点数运算的结果过大而无法表示             |
| `FE_UNDERFLOW`  | 之前浮点数运算的结果为有精度损失的非正规值     |
| `FE_ALL_EXCEPT` | 所有受支持浮点数异常的逐位或                   |

​	实现可于 `<fenv.h>` 定义附加宏常量以鉴别附加浮点数异常。所有这种常量都以 `FE_` 后随至少一个大写字母开始。

​	更多细节见 [`<ath_errhandlin>`](https://zh.cppreference.com/w/c/numeric/math/math_errhandling)。

**示例**



```c
#include <stdio.h>
#include <math.h>
#include <float.h>
#include <fenv.h>
 
#pragma STDC FENV_ACCESS ON
void show_fe_exceptions(void)
{
    printf("exceptions raised:");
    if(fetestexcept(FE_DIVBYZERO)) printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))   printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))   printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))  printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW)) printf(" FE_UNDERFLOW");
    feclearexcept(FE_ALL_EXCEPT);
    printf("\n");
}
 
int main(void)
{
    printf("MATH_ERREXCEPT is %s\n",
           math_errhandling & MATH_ERREXCEPT ? "set" : "not set");
 
    printf("0.0/0.0 = %f\n", 0.0/0.0);
    show_fe_exceptions();
 
    printf("1.0/0.0 = %f\n", 1.0/0.0);
    show_fe_exceptions();
 
    printf("1.0/10.0 = %f\n", 1.0/10.0);
    show_fe_exceptions();
 
    printf("sqrt(-1) = %f\n", sqrt(-1));
    show_fe_exceptions();
 
    printf("DBL_MAX*2.0 = %f\n", DBL_MAX*2.0);
    show_fe_exceptions();
 
    printf("nextafter(DBL_MIN/pow(2.0,52),0.0) = %.1f\n",
                      nextafter(DBL_MIN/pow(2.0,52),0.0));
    show_fe_exceptions();
}
```

​	可能的输出：

```txt
MATH_ERREXCEPT is set
0.0/0.0 = nan
exceptions raised: FE_INVALID
1.0/0.0 = inf
exceptions raised: FE_DIVBYZERO
1.0/10.0 = 0.100000
exceptions raised: FE_INEXACT
sqrt(-1) = -nan
exceptions raised: FE_INVALID
DBL_MAX*2.0 = inf
exceptions raised: FE_INEXACT FE_OVERFLOW
nextafter(DBL_MIN/pow(2.0,52),0.0) = 0.0
exceptions raised: FE_INEXACT FE_UNDERFLOW
```


### FE_DOWNWARD

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_round](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)

```c
#define FE_DOWNWARD     /* 由实现定义 */ // (C99 起)
```

​	每个这种宏常量都展开成非负常量表达式，可被 [fesetround](https://zh.cppreference.com/w/c/numeric/fenv/feround) 或 [fegetround](https://zh.cppreference.com/w/c/numeric/fenv/feround) 用于指示受支持的浮点数舍入模式之一。实现可于 `<fenv.h>` 定义另外的舍入模式常量，它应以 `FE_` 后随至少一个大写字母开始。每个宏仅若受支持才得到定义。

| 常量            | 解释                 |
| --------------- | -------------------- |
| `FE_DOWNWARD`   | 向负无穷大舍入       |
| `FE_TONEAREST`  | 向最接近可表示值舍入 |
| `FE_TOWARDZERO` | 向零舍入             |
| `FE_UPWARD`     | 向正无穷大舍入       |

​	实现可支持另外的舍入模式。

​	当前舍入模式影响下列结果：

- 常量表达式以外的浮点数算术运算符结果

```c
double x = 1;
x/10; // 0.09999999999999999167332731531132594682276248931884765625
   // 或 0.1000000000000000055511151231257827021181583404541015625
```

- 标准库[数学函数](https://zh.cppreference.com/w/c/numeric/math)的返回值

```
sqrt(2); // 1.41421356237309492343001693370752036571502685546875
      // 或 1.4142135623730951454746218587388284504413604736328125
```

- 浮点数到浮点数的隐式转换及转换类型

```c
double d = 1 + DBL_EPSILON;
float f = d; //  1.00000000000000000000000
           // 或 1.00000011920928955078125
```

- 字符串转换，如 [strtod](https://zh.cppreference.com/w/c/string/byte/strtof) 或 [printf](https://zh.cppreference.com/w/c/io/fprintf)

```
strtof("0.1", NULL); // 0.0999999940395355224609375
                  // 或 0.100000001490116119384765625
```

- 库舍入函数 [nearbyint](https://zh.cppreference.com/w/c/numeric/math/nearbyint)、[rint](https://zh.cppreference.com/w/c/numeric/math/rint)、[lrint](https://zh.cppreference.com/w/c/numeric/math/rint)

```
lrint(2.1); // 2 或 3
```

​	当前舍入模式**不**影响：

- 浮点数到整数的隐式转换或转型（始终向零）
- 编译时执行的常量表达式中浮点数算术运算符的结果（始终向最接近）
- 库函数 [round](https://zh.cppreference.com/w/c/numeric/math/round)、[lround](https://zh.cppreference.com/w/c/numeric/math/round)、[llround](https://zh.cppreference.com/w/c/numeric/math/round)、[ceil](https://zh.cppreference.com/w/c/numeric/math/ceil)、[floor](https://zh.cppreference.com/w/c/numeric/math/floor)、[trunc](https://zh.cppreference.com/w/c/numeric/math/trunc)

​	同任何[浮点数环境](https://zh.cppreference.com/w/c/numeric/fenv)功能一样，仅当设置了 `#pragma STDC FENV_ACCESS ON` 才保证舍入。

​	不支持此语用的编译器可能提供它们自己的方式来支持当前舍入模式。例如 Clang 和 GCC 的选项 `-frounding-math` 就用于禁用可能改变对舍入敏感的代码的优化。

**示例**



```c
#include <stdio.h>
#include <stdlib.h>
#include <fenv.h>
#include <math.h>
int main()
{
#pragma STDC FENV_ACCESS ON
    fesetround(FE_DOWNWARD);
    puts("rounding down: ");
    printf("           pi = %.22f\n", acosf(-1));
    printf("strtof(\"1.1\") = %.22f\n", strtof("1.1", NULL));
    printf("    rint(2.1) = %.22f\n\n", rintf(2.1));
    fesetround(FE_UPWARD);
    puts("rounding up: ");
    printf("           pi = %.22f\n", acosf(-1));
    printf("strtof(\"1.1\") = %.22f\n", strtof("1.1", NULL));
    printf("    rint(2.1) = %.22f\n", rintf(2.1));
}
```

​	输出：

```txt
rounding down: 
           pi = 3.1415925025939941406250
strtof("1.1") = 1.0999999046325683593750
    rint(2.1) = 2.0000000000000000000000
 
rounding up: 
           pi = 3.1415927410125732421875
strtof("1.1") = 1.1000000238418579101563
    rint(2.1) = 3.0000000000000000000000
```


### FE_INEXACT

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

```c
#define FE_INEXACT      /* 由实现定义的二的幂 */ // (C99 起)
```

​	不准确结果：必须舍入以存储之前浮点数运算的结果

​	参见：[FE_DIVBYZERO](#FE_DIVBYZERO)


### FE_INVALID

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

```c
#define FE_INVALID      /* 由实现定义的二的幂 */ // (C99 起)
```

​	出现于之前浮点数运算的定义域错误

​	参见：[FE_DIVBYZERO](#FE_DIVBYZERO)


### FE_OVERFLOW

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

```c
#define FE_OVERFLOW     /* 由实现定义的二的幂 */ // (C99 起)
```

​	之前浮点数运算的结果过大而无法表示

​	参见：[FE_DIVBYZERO](#FE_DIVBYZERO)


### FE_SNANS_ALWAYS_SIGNAL

原址：

```c
#define FE_SNANS_ALWAYS_SIGNAL /* 由实现定义 */
```




### FE_TONEAREST

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_round](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)

```c
#define FE_TONEAREST    /* 由实现定义 */ // (C99 起)
```

​	参见：[FE_DOWNWARD](#FE_DOWNWARD)


### FE_TONEARESTFROMZERO

原址：

```c
```




### FE_TOWARDZERO

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_round](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)

```c
#define FE_TOWARDZERO   /* 由实现定义 */ // (C99 起)
```

​	参见：[FE_DOWNWARD](#FE_DOWNWARD)


### FE_UNDERFLOW

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)

```c
#define FE_UNDERFLOW    /* 由实现定义的二的幂 */ // (C99 起)
```

​	之前浮点数运算的结果为有精度损失的非正规值

​	参见：[FE_DIVBYZERO](#FE_DIVBYZERO)


### FE_UPWARD

原址：[https://zh.cppreference.com/w/c/numeric/fenv/FE_round](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)

```c
#define FE_UPWARD       /* 由实现定义 */ // (C99 起)
```

​	参见：[FE_DOWNWARD](#FE_DOWNWARD)


### __STDC_VERSION_FENV_H__

原址：

```c
#define __STDC_VERSION_FENV_H__ 202311L
```




### femode_t

原址：

```c
```




### fenv_t

原址：

```c
```




### fexcept_t

原址：

```c
```




## 函数
### fe_dec_getround

原址：

```c
```




### fe_dec_setround

原址：

```c
```




### feclearexcept

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feclearexcept](https://zh.cppreference.com/w/c/numeric/fenv/feclearexcept)

```c
int feclearexcept( int excepts ); // (C99 起)
```

​	尝试清除列于位掩码实参 `excepts` 的浮点数异常，该实参值为[浮点数异常宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)的逐位或。

**参数**

| excepts | -    | 列出欲清除的异常标志的位掩码 |
| ------- | ---- | ---------------------------- |

**返回值**

​	若成功清除所有指明的异常，或若 `excepts` 为零则返回 0。错误时返回非零。

**示例**



```c
#include <fenv.h>
#include <stdio.h>
#include <math.h>
#include <float.h>
 
/*
 * 可能的 hypot 实现，它会活用许多高级浮点数特性。
 */
double hypot_demo(double a, double b) {
  const int range_problem = FE_OVERFLOW | FE_UNDERFLOW;
  feclearexcept(range_problem);
  // 尝试快速算法
  double result = sqrt(a * a + b * b);
  if (!fetestexcept(range_problem))  // 未上溢或下溢
    return result;                   // 返回结果
  // 做更多复杂计算以避免上溢或下溢
  int a_exponent,b_exponent;
  frexp(a, &a_exponent);
  frexp(b, &b_exponent);
 
  if (a_exponent - b_exponent > DBL_MAX_EXP)
    return fabs(a) + fabs(b);        // 我们可以忽略小值
  // 缩放以令 fabs(a) 接近1
  double a_scaled = scalbn(a, -a_exponent);
  double b_scaled = scalbn(b, -a_exponent);
  // 现在上溢和下溢是不可能的
  result = sqrt(a_scaled * a_scaled + b_scaled * b_scaled);
  // 撤销缩放
  return scalbn(result, a_exponent);
}
 
int main(void)
{
  // 通常情况选择较快的路线
  printf("hypot(%f, %f) = %f\n", 3.0, 4.0, hypot_demo(3.0, 4.0));
  // 极限情形会选择较慢但更准确的路线
  printf("hypot(%e, %e) = %e\n", DBL_MAX / 2.0, 
                                DBL_MAX / 2.0, 
                                hypot_demo(DBL_MAX / 2.0, DBL_MAX / 2.0));
 
  return 0;
}
```

​	输出：

```txt
hypot(3.000000, 4.000000) = 5.000000
hypot(8.988466e+307, 8.988466e+307) = 1.271161e+308
```




### fegetenv

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feenv](https://zh.cppreference.com/w/c/numeric/fenv/feenv)

```c
int fegetenv( fenv_t* envp ); // (1)	(C99 起)
int fesetenv( const fenv_t* envp ); // (2)	(C99 起)
```

​	1) 试图存储浮点数环境的状态于 `envp` 所指向的对象。

​	2) 试图从 `envp` 所指向的对象建立浮点数环境状态。对象的值必须是以先前调用 [feholdexcept](https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept) 或 `fegetenv` 获得值或是浮点数宏常量。若 `envp` 中设置了任何浮点数状态标志，则环境中标志变为被设置（然后可用 [fetestexcept](https://zh.cppreference.com/w/c/numeric/fenv/fetestexcept) 测试），但不引发对应的浮点数异常（执行持续而不中断）。

**参数**

| envp | -    | 指向 fenv_t 类型对象的指针，该对象保有浮点数环境的状态 |
| ---- | ---- | ------------------------------------------------------ |

**返回值**

​	成功时返回 0，否则返回非零。

**示例**



```c
#include <stdio.h>
#include <math.h>
#include <fenv.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    printf("\n");
}
 
void show_fe_rounding_method(void)
{
    printf("current rounding method:    ");
    switch (fegetround()) {
           case FE_TONEAREST:  printf ("FE_TONEAREST");  break;
           case FE_DOWNWARD:   printf ("FE_DOWNWARD");   break;
           case FE_UPWARD:     printf ("FE_UPWARD");     break;
           case FE_TOWARDZERO: printf ("FE_TOWARDZERO"); break;
           default:            printf ("unknown");
    };
    printf("\n");
}
 
void show_fe_environment(void)
{
    show_fe_exceptions();
    show_fe_rounding_method();
}    
 
int main(void)
{
    fenv_t curr_env;
    int rtn;
 
    /* 显示默认环境。 */
    show_fe_environment();
    printf("\n");
 
    /* 在默认环境下做一些计算。 */
    printf("+11.5 -> %+4.1f\n", rint(+11.5)); /* 两整数的中央值 */
    printf("+12.5 -> %+4.1f\n", rint(+12.5)); /* 两整数的中央值 */
    show_fe_environment();
    printf("\n");
 
    /* 保存当前环境。 */
    rtn = fegetenv(&curr_env);
 
    /* 以新舍入方法进行一些计算。 */
    feclearexcept(FE_ALL_EXCEPT);
    fesetround(FE_DOWNWARD);
    printf("1.0/0.0 = %f\n", 1.0/0.0);
    printf("+11.5 -> %+4.1f\n", rint(+11.5));
    printf("+12.5 -> %+4.1f\n", rint(+12.5));
    show_fe_environment();
    printf("\n");
 
    /* 恢复先前环境。 */
    rtn = fesetenv(&curr_env);
    show_fe_environment();
 
    return 0;
}
```

​	输出：

```txt
current exceptions raised: none
current rounding method:   FE_TONEAREST
 
+11.5 -> +12.0
+12.5 -> +12.0
current exceptions raised: FE_INEXACT
current rounding method:   FE_TONEAREST
 
1.0/0.0 = inf
+11.5 -> +11.0
+12.5 -> +12.0
current exceptions raised: FE_DIVBYZERO FE_INEXACT
current rounding method:   FE_DOWNWARD
 
current exceptions raised: FE_INEXACT
current rounding method:   FE_TONEAREST
```


### fegetexceptflag

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag](https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag)

```c
int fegetexceptflag( fexcept_t* flagp, int excepts ); // (1)	(C99 起)
int fesetexceptflag( const fexcept_t* flagp, int excepts ); // (2)	(C99 起)
```

​	1） 试图获得列于位掩码实参 `excepts` 的浮点数异常标志的完整内容，它是[浮点数异常宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)的逐位或。

​	2）试图从 `flagp` 复制列于 `excepts` 的浮点数异常标志到浮点数环境。不引发任何异常，只修改标志。

​	浮点数异常标志的完整内容不必是指示是否引发或清除异常的布尔值。例如，它可以是结构体，包含布尔状态和触发了异常的代码地址。这些函数获得所有这种内容，并以实现定义格式于 `flagp` 获得/存储它。

**参数**

| flagp   | -    | 指向将要存储或读取标志位置的 fexcept_t 对象的指针 |
| ------- | ---- | ------------------------------------------------- |
| excepts | -    | 列出要获取/设置的异常的位掩码                     |

**返回值**

​	成功时返回 0，否则返回非零。

**示例**



```c
#include <stdio.h>
#include <fenv.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    printf("\n");
}
 
int main(void)
{
    fexcept_t excepts;
 
    /* 设置“当前”异常标志集合。 */
    feraiseexcept(FE_INVALID);
    show_fe_exceptions();
 
    /* 保存当前异常标志。 */
    fegetexceptflag(&excepts,FE_ALL_EXCEPT);
 
    /* 临时引发两个其他异常。 */
    feclearexcept(FE_ALL_EXCEPT);
    feraiseexcept(FE_OVERFLOW | FE_INEXACT);
    show_fe_exceptions();
 
    /* 恢复先前的异常标志。 */
    fesetexceptflag(&excepts,FE_ALL_EXCEPT);
    show_fe_exceptions();
 
    return 0;
}
```

​	输出：

```txt
current exceptions raised: FE_INVALID
current exceptions raised: FE_INEXACT FE_OVERFLOW
current exceptions raised: FE_INVALID
```




### fegetmode

原址：

```c
```




### fegetround

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feround](https://zh.cppreference.com/w/c/numeric/fenv/feround)

```c
int fesetround( int round ); // (1)	(C99 起)
int fegetround(void); // (2)	(C99 起)
```

1）试图建立等于实参 [round](http://zh.cppreference.com/w/c/numeric/math/round) 的浮点数舍入方向，期待实参为[浮点数舍入宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)之一。

2）返回对应当前舍入方向的[浮点数舍入宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)。

**参数**

| round | -    | 舍入方向，[浮点数舍入宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)之一 |
| ----- | ---- | ------------------------------------------------------------ |

**返回值**

​	1) 成功时为 0，否则为非零。

​	2) 描述当前舍入方向的[浮点数舍入宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_round)，或若不能确定方向则为负值

**注意**

​	当前舍入方向反映最近的 `fesetround` 的效果，亦能以 [FLT_ROUNDS](https://zh.cppreference.com/w/c/types/limits/FLT_ROUNDS) 查询。

**示例**



```c
#include <stdio.h>
#include <math.h>
#include <fenv.h>
 
#pragma STDC FENV_ACCESS ON
void show_fe_current_rounding_method(void)
{
    printf("current rounding method:  ");
    switch (fegetround())
    {
           case FE_TONEAREST:  printf ("FE_TONEAREST");  break;
           case FE_DOWNWARD:   printf ("FE_DOWNWARD");   break;
           case FE_UPWARD:     printf ("FE_UPWARD");     break;
           case FE_TOWARDZERO: printf ("FE_TOWARDZERO"); break;
           default:            printf ("unknown");
    };
    printf("\n");
}
 
int main(void)
{
    /* 默认舍入方法 */
    show_fe_current_rounding_method();
    printf("+11.5 -> %+4.1f\n", rint(+11.5)); /* 两整数的中央值 */
    printf("+12.5 -> %+4.1f\n", rint(+12.5)); /* 两整数的中央值 */
 
    /* 保存舍入方法。 */
    int curr_method = fegetround();
 
    /* 临时更改当前舍入方法。 */
    fesetround(FE_DOWNWARD);
    show_fe_current_rounding_method();
    printf("+11.5 -> %+4.1f\n", rint(+11.5));
    printf("+12.5 -> %+4.1f\n", rint(+12.5));
 
    /* 恢复舍入方法。 */
    fesetround(curr_method);
    show_fe_current_rounding_method(); 
 
    return 0;
}
```

​	可能的输出：

```txt
current rounding method:  FE_TONEAREST
+11.5 -> +12.0
+12.5 -> +12.0
current rounding method:  FE_DOWNWARD
+11.5 -> +11.0
+12.5 -> +12.0
current rounding method:  FE_TONEAREST
```


### feholdexcept

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept](https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept)

```c
int feholdexcept( fenv_t* envp ); // (C99 起)
```

​	首先，保存当前浮点数环境到 `envp` 所指向的对象（类似 [fegetenv](https://zh.cppreference.com/w/c/numeric/fenv/feenv)），然后清除所有浮点数状态标志，再安装不停止模式：未来的浮点数异常将不中断执行（不会陷落），直至以 [feupdateenv](https://zh.cppreference.com/w/c/numeric/fenv/feupdateenv) 或 [fesetenv](https://zh.cppreference.com/w/c/numeric/fenv/feenv) 还原浮点数状态。

​	此函数可用于必须从调用方隐藏它可能引发的浮点数异常的子程序的起始。若只是必须抑制某些异常而必须报告其他，则通常在清除不想要的异常后，通过调用 [feupdateenv](https://zh.cppreference.com/w/c/numeric/fenv/feupdateenv) 结束不停止模式。

**参数**

| envp | -    | 指向 fenv_t 类型对象的指针，将存储浮点数环境于其中 |
| ---- | ---- | -------------------------------------------------- |

**返回值**

​	成功时返回 0，否则返回非零。

**示例**



```c
#include <stdio.h>
#include <fenv.h>
#include <float.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    printf("\n");
}
 
double x2 (double x)   /* 乘二 */
{
    fenv_t curr_excepts;
 
    /* 保存并清除当前浮点数异常。 */
    feholdexcept(&curr_excepts);
 
    /* 引发不准确和上溢异常。 */
    printf("In x2():  x = %f\n", x=x*2.0);
    show_fe_exceptions();
    feclearexcept(FE_INEXACT);   /* 从调用方隐藏不准确异常 */
 
    /* 将调用方的异常（FE_INVALID）并入剩下的 x2 的异常（FE_OVERFLOW）。 */
    feupdateenv(&curr_excepts);
    return x;
}
 
int main(void)
{    
    feclearexcept(FE_ALL_EXCEPT);
    feraiseexcept(FE_INVALID);   /* 一些有非法实参的计算 */
    show_fe_exceptions();
    printf("x2(DBL_MAX) = %f\n", x2(DBL_MAX));
    show_fe_exceptions();
 
    return 0;
}
```

​	输出：

```txt
current exceptions raised:  FE_INVALID
In x2():  x = inf
current exceptions raised:  FE_INEXACT FE_OVERFLOW
x2(DBL_MAX) = inf
current exceptions raised:  FE_INVALID FE_OVERFLOW
```


### feraiseexcept

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feraiseexcept](https://zh.cppreference.com/w/c/numeric/fenv/feraiseexcept)

```c
int feraiseexcept( int excepts ); // (C99 起)
```

​	尝试引发所有列于 `excepts`（[浮点数异常宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)的逐位或）的浮点数异常。若异常之一为 [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 或 [FE_UNDERFLOW](http://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)，则此函数可以额外引发 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)。异常的引发顺序未指定，除了 [FE_OVERFLOW](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 和 [FE_UNDERFLOW](http://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 一定先于 [FE_INEXACT](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions) 引发。

**参数**

| excepts | -    | 列出所有要引发的异常标志的位掩码 |
| ------- | ---- | -------------------------------- |

**返回值**

​	若引发了所有列出的异常，则返回 0，否则返回非零值。

**示例**



```c
#include <stdio.h>
#include <fenv.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    feclearexcept(FE_ALL_EXCEPT);
    printf("\n");
}
 
double some_computation(void)
{
    /* 计算达到引发上溢的状态。 */
    int r = feraiseexcept(FE_OVERFLOW | FE_INEXACT);
    printf("feraiseexcept() %s\n", (r?"fails":"succeeds"));
    return 0.0;
}
 
int main(void)
{
    some_computation();
    show_fe_exceptions();
 
    return 0;
}
```

​	输出：

```txt
feraiseexcept() succeeds
current exceptions raised:  FE_INEXACT FE_OVERFLOW
```




### fesetenv

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feenv](https://zh.cppreference.com/w/c/numeric/fenv/feenv)

```c
int fegetenv( fenv_t* envp ); // (1)	(C99 起)
int fesetenv( const fenv_t* envp ); // (2)	(C99 起)
```

参见：[fegetenv](#fegetenv)


### fesetexcept

原址：

```c
```




### fesetexceptflag

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag](https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag)

```c
int fegetexceptflag( fexcept_t* flagp, int excepts ); // (1)	(C99 起)
int fesetexceptflag( const fexcept_t* flagp, int excepts ); // (2)	(C99 起)
```

参见：[fegetexceptflag](#fegetexceptflag)







### fesetmode

原址：

```c
```




### fesetround

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feround](https://zh.cppreference.com/w/c/numeric/fenv/feround)

```c
int fesetround( int round ); // (1)	(C99 起)
int fegetround(void); // (2)	(C99 起)
```

参见：[fegetround](#fegetround)


### fetestexcept

原址：[https://zh.cppreference.com/w/c/numeric/fenv/fetestexcept](https://zh.cppreference.com/w/c/numeric/fenv/fetestexcept)

```c
int fetestexcept( int excepts ); // (C99 起)
```

​	确定当前设置了哪个指定的浮点数异常子集。参数 `excepts` 是[浮点数异常宏](https://zh.cppreference.com/w/c/numeric/fenv/FE_exceptions)的逐位或。

**参数**

| excepts | -    | 列出待测试异常标志的位掩码 |
| ------- | ---- | -------------------------- |

**返回值**

​	包含于 `excepts` 而且对应于当前设置的浮点数异常中的浮点数异常宏的逐位或。

**示例**



```c
#include <stdio.h>
#include <math.h>
#include <fenv.h>
#include <float.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    printf("\n");
}
 
int main(void)
{
    /* 显示默认浮点数标志集合。 */
    show_fe_exceptions();
 
    /* 进行一些引发浮点数异常的计算。 */
    printf("1.0/0.0     = %f\n", 1.0/0.0);        /* FE_DIVBYZERO            */
    printf("1.0/10.0    = %f\n", 1.0/10.0);       /* FE_INEXACT              */
    printf("sqrt(-1)    = %f\n", sqrt(-1));       /* FE_INVALID              */
    printf("DBL_MAX*2.0 = %f\n", DBL_MAX*2.0);    /* FE_INEXACT FE_OVERFLOW  */
    printf("nextafter(DBL_MIN/pow(2.0,52),0.0) = %.1f\n",
           nextafter(DBL_MIN/pow(2.0,52),0.0));   /* FE_INEXACT FE_UNDERFLOW */
    show_fe_exceptions();
 
    return 0;
}
```

​	输出：

```txt
current exceptions raised:  none
1.0/0.0     = inf
1.0/10.0    = 0.100000
sqrt(-1)    = -nan
DBL_MAX*2.0 = inf
nextafter(DBL_MIN/pow(2.0,52),0.0) = 0.0
current exceptions raised:  FE_DIVBYZERO FE_INEXACT FE_INVALID FE_OVERFLOW FE_UNDERFLOW
```




### fetestexceptflag

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag](https://zh.cppreference.com/w/c/numeric/fenv/feexceptflag)

```c
int fegetexceptflag( fexcept_t* flagp, int excepts ); // (1)	(C99 起)
int fesetexceptflag( const fexcept_t* flagp, int excepts ); // (2)	(C99 起)
```

参见：[fegetexceptflag](#fegetexceptflag)


### feupdateenv

原址：[https://zh.cppreference.com/w/c/numeric/fenv/feupdateenv](https://zh.cppreference.com/w/c/numeric/fenv/feupdateenv)

```c
int feupdateenv( const fenv_t* envp ); // (C99 起)

```

​	首先，记住当前引发的浮点数异常，然后从 `envp` 所指向的对象恢复浮点数环境（类似 [fesetenv](https://zh.cppreference.com/w/c/numeric/fenv/feenv)），再引发保存的浮点数异常。

此函数可用于结束先前调用 [feholdexcept](https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept) 建立的不停止模式。

**参数**

| envp | -    | 指向 fenv_t 类型对象的指针，对象为之前到 [feholdexcept](https://zh.cppreference.com/w/c/numeric/fenv/feholdexcept) 或 `fegetenv` 的调用所设，或等于 [FE_DFL_ENV](https://zh.cppreference.com/w/c/numeric/fenv/FE_DFL_ENV) |
| ---- | ---- | ------------------------------------------------------------ |

**返回值**

​	成功时为 0，否则为非零。

**示例**



```c
#include <stdio.h>
#include <fenv.h>
#include <float.h>
 
#pragma STDC FENV_ACCESS ON
 
void show_fe_exceptions(void)
{
    printf("current exceptions raised: ");
    if(fetestexcept(FE_DIVBYZERO))     printf(" FE_DIVBYZERO");
    if(fetestexcept(FE_INEXACT))       printf(" FE_INEXACT");
    if(fetestexcept(FE_INVALID))       printf(" FE_INVALID");
    if(fetestexcept(FE_OVERFLOW))      printf(" FE_OVERFLOW");
    if(fetestexcept(FE_UNDERFLOW))     printf(" FE_UNDERFLOW");
    if(fetestexcept(FE_ALL_EXCEPT)==0) printf(" none");
    printf("\n");
}
 
double x2 (double x)   /* 乘二 */
{
    fenv_t curr_excepts;
 
    /* 保存并清理当前浮点数环境。 */
    feholdexcept(&curr_excepts);
 
    /* 引发不准确和溢出异常。 */
    printf("In x2():  x = %f\n", x=x*2.0);
    show_fe_exceptions();
    feclearexcept(FE_INEXACT);   /* 从调用方隐藏不准确异常 */
 
    /* 将调用方的异常（FE_INVALID）并入        */
    /* 剩下的x2的异常（FE_OVERFLOW）。 */
    feupdateenv(&curr_excepts);
    return x;
}
 
int main(void)
{    
    feclearexcept(FE_ALL_EXCEPT);
    feraiseexcept(FE_INVALID);   /* 一些带有非法参数的计算 */
    show_fe_exceptions();
    printf("x2(DBL_MAX) = %f\n", x2(DBL_MAX));
    show_fe_exceptions();
 
    return 0;
}
```

输出：

```txt
current exceptions raised:  FE_INVALID
In x2():  x = inf
current exceptions raised:  FE_INEXACT FE_OVERFLOW
x2(DBL_MAX) = inf
current exceptions raised:  FE_INVALID FE_OVERFLOW
```

