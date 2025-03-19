+++
title = "Bind form-data request with custom struct"
date = 2025-03-18T17:00:30+08:00
weight = 20
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://gin-gonic.com/docs/examples/bind-form-data-request-with-custom-struct/](https://gin-gonic.com/docs/examples/bind-form-data-request-with-custom-struct/)

## 源码

```go
package main

import "github.com/gin-gonic/gin"

type StructA struct {
	FieldA string `form:"field_a"`
}

type StructB struct {
	NestedStruct StructA
	FieldB       string `form:"field_b"`
}

type StructC struct {
	NestedStructPointer *StructA
	FieldC              string `form:"field_c"`
}

type StructD struct {
	NestedAnonyStruct struct {
		FieldX string `form:"field_x"`
	}
	FieldD string `form:"field_d"`
}

func GetDataB(c *gin.Context) {
	var b StructB
	c.Bind(&b)
	c.JSON(200, gin.H{
		"a": b.NestedStruct,
		"b": b.FieldB,
	})
}

func GetDataC(c *gin.Context) {
	var b StructC
	c.Bind(&b)
	c.JSON(200, gin.H{
		"a": b.NestedStructPointer,
		"c": b.FieldC,
	})
}

func GetDataD(c *gin.Context) {
	var b StructD
	_ = c.Bind(&b)
	c.JSON(200, gin.H{
		"x": b.NestedAnonyStruct,
		"d": b.FieldD,
	})
}

func main() {
	r := gin.Default()
	r.GET("/getb", GetDataB)
	r.GET("/getc", GetDataC)
	r.GET("/getd", GetDataD)

	r.Run()
}
```



## 测试

```powershell
PS D:\GoPrjs2\ginOfficeExamples> curl "http://localhost:8080/getb?field_a=hello&field_b=world"
{"a":{"FieldA":"hello"},"b":"world"}
PS D:\GoPrjs2\ginOfficeExamples> curl "http://localhost:8080/getc?field_a=hello&field_c=world"
{"a":{"FieldA":"hello"},"c":"world"}
PS D:\GoPrjs2\ginOfficeExamples> curl "http://localhost:8080/getd?field_x=hello&field_d=world"
{"d":"world","x":{"FieldX":"hello"}}
PS D:\GoPrjs2\ginOfficeExamples> curl "http://localhost:8080/getd?field_x=hello&field_d=world" -i
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Date: Tue, 18 Mar 2025 09:08:44 GMT
Content-Length: 36

{"d":"world","x":{"FieldX":"hello"}}

```

