+++
title = "<float.h>"
date = 2025-04-16T19:58:10+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 类型

## 宏

### DBL_DECIMAL_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	将 double 转换为带有至少 `DBL_DECIMAL_DIG` 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。分别至少定义为 10 ，或对于 IEEE float 为 9，对于 IEEE double 为 17（另见 C++ 对应物：[`max_digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/max_digits10)）







### DBL_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	在“文本 → double → 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 [`digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/digits10) 的详情）







### DBL_EPSILON

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	1.0 与 double 的下一个可表示值之差的绝对值







### DBL_HAS_SUBNORM <- 11+ 23 D

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	类型是否支持[非正规](https://en.wikipedia.org/wiki/Denormal_number)）数值：

`-1` – 不确定, 

`0` – 不支持, 

`1` – 支持









### DBL_MANT_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	long double 可表示且不损失精度的 `FLT_RADIX` 进制有效数字数位个数







### DBL_MAX

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	double 的最大有穷值







### DBL_MAX_10_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 long double 的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值







### DBL_MAX_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 double 的最大正整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的可表示有穷值







### DBL_MIN

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	double 的最小正规正数值







### DBL_MIN_10_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 long double 的最小负整数，使得 10 的该整数次方是该类型的正规值







### DBL_MIN_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 double 的最小负整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的正规值







### DBL_TRUE_MIN

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	double  的最小整数值







### DECIMAL_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	将 long double 转换为带有至少 `DECIMAL_DIG` 个数位的十进制数，再转换回 long double 为恒等转换：此为序列化/反序列化 long double 所需的十进制精度







### FLT_DECIMAL_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	将 float 转换为带有至少 `FLT_DECIMAL_DIG` 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。分别至少定义为 6，或对于 IEEE float 为 9，对于 IEEE double 为 17（另见 C++ 对应物：[`max_digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/max_digits10)）







### FLT_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	在“文本 → float→ 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 [`digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/digits10) 的详情）







### FLT_EPSILON

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	1.0 与 float的下一个可表示值之差的绝对值







### FLT_EVAL_METHOD

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	指定所有算术运算以什么精度执行







### FLT_HAS_SUBNORM <- 11+ 23 D

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	类型是否支持[非正规](https://en.wikipedia.org/wiki/Denormal_number)）数值：

`-1` – 不确定, 

`0` – 不支持, 

`1` – 支持







### FLT_MANT_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	float 可表示且不损失精度的 `FLT_RADIX` 进制有效数字数位个数







### FLT_MAX

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	float 的最大有穷值







### FLT_MAX_10_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 float的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值







### FLT_MAX_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 float的最大正整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的可表示有穷值







### FLT_MIN

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	float 的最小正规正数值







### FLT_MIN_10_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 float 的最小负整数，使得 10 的该整数次方是该类型的正规值







### FLT_MIN_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 float的最小负整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的正规值







### FLT_RADIX

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	全部三种浮点数类型的表示所用的基数（整数基）







### FLT_ROUNDS

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	浮点数算术的舍入模式







### FLT_TRUE_MIN

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	 float 的最小整数值







### LDBL_DECIMAL_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	将long double 转换为带有至少 `LDBL_DECIMAL_DIG` 个数位的十进制数，再转换回去为恒等转换：此为序列号/反序列化浮点数值所需的十进制精度。至少定义为 10，或对于 IEEE float 为 9，对于 IEEE double 为 17（另见 C++ 对应物：[`max_digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/max_digits10)）







### LDBL_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	在“文本 → long double → 文本”往返转换中保证被保留且不会印舍入或溢出而改变的十进制数位个数（参见 C++ 对应物 [`digits10`](https://zh.cppreference.com/w/cpp/types/numeric_limits/digits10) 的详情）







### LDBL_EPSILON

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	1.0 与  long double 的下一个可表示值之差的绝对值







### LDBL_HAS_SUBNORM <- 11+ 23 D

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	类型是否支持[非正规](https://en.wikipedia.org/wiki/Denormal_number)）数值：

`-1` – 不确定, 

`0` – 不支持, 

`1` – 支持





### LDBL_MANT_DIG

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	long double 可表示且不损失精度的 `FLT_RADIX` 进制有效数字数位个数







### LDBL_MAX

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	long double 的最大有穷值







### LDBL_MAX_10_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于long double 的最大正整数，使得 10 的该整数次方是该类型的可表示有穷值







### LDBL_MAX_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于long double 的最大正整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的可表示有穷值







### LDBL_MIN

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	long double 的最小正规正数值







### LDBL_MIN_10_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 long double 的最小负整数，使得 10 的该整数次方是该类型的正规值







### LDBL_MIN_EXP

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	对于 long double 的最小负整数，使得 `FLT_RADIX` 的该整数减一次方是该类型的正规值







### LDBL_TRUE_MIN

原址：[https://zh.cppreference.com/w/c/header/float](https://zh.cppreference.com/w/c/header/float)

```c

```

​	long double 的最小整数值







## 函数
