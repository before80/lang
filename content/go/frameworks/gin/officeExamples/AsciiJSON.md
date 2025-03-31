+++
title = "AsciiJSON"
date = 2025-03-18T17:00:10+08:00
weight = 10
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

> 原文：[https://gin-gonic.com/docs/examples/ascii-json/](https://gin-gonic.com/docs/examples/ascii-json/)

## 源码

```go
package main

import (
	"github.com/gin-gonic/gin"
	"net/http"
)

func main() {
	r := gin.Default()

	r.GET("/someJSON", func(c *gin.Context) {
		data := map[string]interface{}{
			"lang": "GO语言",
			"tag":  "<br>",
		}

		// will output : {"lang":"GO\u8bed\u8a00","tag":"\u003cbr\u003e"}
		c.AsciiJSON(http.StatusOK, data)
	})

	// Listen and serve on 0.0.0.0:8080
	r.Run(":8080")
}
```



## 测试

```powershell
PS D:\GoPrjs2\ginOfficeExamples> curl http://localhost:8080/someJSON
{"lang":"GO\u8bed\u8a00","tag":"\u003cbr\u003e"}
PS D:\GoPrjs2\ginOfficeExamples> curl http://localhost:8080/someJSON -i
HTTP/1.1 200 OK
Content-Type: application/json
Date: Tue, 18 Mar 2025 08:26:08 GMT
Content-Length: 48

{"lang":"GO\u8bed\u8a00","tag":"\u003cbr\u003e"}
```

