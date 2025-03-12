+++
title = "gin"
date = 2025-03-12T12:59:19+08:00
weight = 1
type = "docs"
description = ""
isCJKLanguage = true
draft = false

+++

## 是什么？

​	[Gin](https://github.com/gin-gonic/gin) 是一个用Go语言编写的`Web框架`，以高性能和简洁著称，类似于 Martini，但性能更高。

​	[httprouter](https://github.com/julienschmidt/httprouter) 采用 **Radix Tree（基数树）** 进行高效的路由匹配，其查找复杂度趋近于 **O(k)**（k 为 URL 片段数），相比于传统的 O(m) 线性遍历匹配更高效。Gin 基于 `net/http`并借鉴了 `httprouter` 的路由设计，自行实现了高性能的路由匹配机制，同时通过高效的 JSON 解析、零内存拷贝优化、减少 GC 压力等方式，进一步提升了整体性能，使其在高并发场景下具有优异表现。`Gin`和`httprouter`本质上都是通过减少路由查找的时间复杂度来实现的。

​	此外，Gin 还提供了诸如中间件支持、渲染、数据绑定与校验等功能，使其适用于快速开发`RESTful API`和高性能Web服务。这种设计使得 Gin 在保持高性能的同时，扩展性更强。

> URL 片段数
>
> 假设有如下几个 URL 路由规则：
>
> ```sh
> /users/:id
> /users/:id/profile
> /articles/:category/:id
> ```
>
> 如果匹配 `"/users/123/profile"`，那么 **片段数（k）** 是：
>
> - `"users"` → **第 1 段**
> - `"123"` → **第 2 段**（动态参数 `:id`）
> - `"profile"` → **第 3 段**
>
> 所以，`k = 3`。
>
> ​	**片段数（k）** 指 URL 通过 `/` 分割后的部分数量。

> **Radix Tree（基数树）简介**
>
> ​	**Radix Tree（基数树）**，又称 **压缩前缀树（Compressed Prefix Tree）**，是一种 **改进的 Trie（字典树）数据结构**，用于高效存储和检索字符串数据。它通过合并公共前缀路径，减少节点数量，从而提高查询效率和节省存储空间。
>
> ------
>
> **1. Radix Tree 的基本特点**
>
> - **基于前缀匹配**：存储时会合并具有相同前缀的路径，从而减少树的深度。
> - **减少节点数量**：相比于普通的 Trie（每个字符一个节点），Radix Tree **一个节点可以存储多个字符**，从而减少冗余。
> - **适用于高效字符串查找**：如 **路由匹配**、**IP 路由表**、**字符串存储**（如 DNS、自动补全）等应用场景。
> - **查询时间复杂度通常趋近于 `O(k)`**（k 为查询字符串的片段数或字符数，取决于具体实现）。
>
> ------
>
> **2. 普通 Trie vs. Radix Tree 对比**
>
> **示例数据集（存储以下 URL 路由）：**
>
> ```markdown
> /user
> /user/profile
> /user/settings
> /useful
> ```
>
> **（1）普通 Trie 结构**
>
> 普通的 Trie（前缀树）会逐字符存储：
>
> ```markdown
>       /
>       ├── u
>       │   ├── s
>       │   │   ├── e
>       │   │   │   ├── r
>       │   │   │   │   ├── / (终结)
>       │   │   │   │   ├── p
>       │   │   │   │   │   ├── r
>       │   │   │   │   │   ├── o
>       │   │   │   │   │   ├── f
>       │   │   │   │   │   ├── i
>       │   │   │   │   │   ├── l
>       │   │   │   │   │   ├── e (终结)
>       │   │   │   │   ├── s
>       │   │   │   │   │   ├── e
>       │   │   │   │   │   ├── t
>       │   │   │   │   │   ├── t
>       │   │   │   │   │   ├── i
>       │   │   │   │   │   ├── n
>       │   │   │   │   │   ├── g
>       │   │   │   │   │   ├── s (终结)
>       │   │   │   ├── f
>       │   │   │   ├── u
>       │   │   │   ├── l (终结)
> ```
>
> - **问题**：每个字符都独占一个节点，存储效率低，路径过长。
>
> ------
>
> **（2）Radix Tree 结构**
>
> Radix Tree 通过 **合并公共前缀**，减少节点数：
>
> ```markdown
> 	  /
>       ├── user
>       │   ├── / (终结)
>       │   ├── profile (终结)
>       │   ├── settings (终结)
>       ├── useful (终结)
> ```
>
> - 优势：
>   - **减少节点数量**，`/user` 直接作为一个节点，不需要按字符存储。
>   - **加快查询速度**，不需要逐字符遍历，只需按前缀片段匹配。
>
> ------
>
> **3. 为什么 Gin 使用 Radix Tree？**
>
> Gin 的路由匹配采用 **Radix Tree**，相比传统线性匹配（O(m)），它可以更快地匹配 URL 路由，适用于高并发场景。
>
> **Gin 的路由存储示例**
>
> ​	假设注册以下路由：
>
> ```
> bash复制代码/users
> /users/:id
> /users/:id/profile
> /articles/:category/:id
> ```
>
> **Radix Tree 存储结构：**
>
> ```
> bash复制代码      /
>       ├── users
>       │   ├── / (终结)
>       │   ├── :id
>       │   │   ├── /profile (终结)
>       ├── articles
>       │   ├── :category
>       │   │   ├── :id (终结)
> ```
>
> - 查询 `/users/123/profile`：
>   1. 从根 `/` 开始匹配 `users`。
>   2. 进入 `:id` 节点（匹配 `123`）。
>   3. 进入 `/profile` 节点，成功匹配。
>
> ------
>
> ## **4. 总结**
>
> - **Radix Tree 通过合并前缀减少存储空间，提高匹配效率。**
> - **Gin 使用 Radix Tree 来优化 URL 路由匹配，提升查询速度。**
> - **查询时间复杂度通常为 `O(k)`，相比于传统 O(m) 线性遍历方式更高效。**

## 有什么用？

​	Gin 主要用于：

- **构建 Web 应用**：支持 HTTP 路由、静态文件托管和模板渲染。
- **构建 RESTful API**：轻量级、性能优越，适用于微服务架构。
- **高效处理请求**：提供高性能的 JSON 解析、数据绑定、日志记录和错误处理机制。
- **中间件支持**：支持用户自定义中间件，如身份验证、日志、跨域等。

## 创建gin实例化对象

​	Gin 提供两种方式创建实例化对象：

1. `gin.Default()`：创建一个默认的路由引擎，包含 `Logger` 和 `Recovery` 中间件。
2. `gin.New()`：创建一个不包含任何默认中间件的路由引擎。

```go

```



## 路由

​	在 Gin 框架中，**路由（Routing）** 是指 **将客户端的 HTTP 请求路径（URL）与相应的处理函数（Handler）进行映射**，从而实现不同的请求逻辑。

### 定义路由

#### （1）基于 HTTP 方法定义路由

​	Gin 提供了 **常见的 HTTP 方法**（`GET`、`POST`、`PUT`、`DELETE`、`PATCH`、`HEAD`、`OPTIONS` ）等7个（除了`TRACE`和`CONNECT`），用于定义路由，每个方法都对应 `gin.Engine` 的一个方法：

```go
package main

import "github.com/gin-gonic/gin"

func main() {
    r := gin.Default()

    r.GET("/get", func(c *gin.Context) {
        c.String(200, "GET Request")
    })

    r.POST("/post", func(c *gin.Context) {
        c.String(200, "POST Request")
    })

    r.PUT("/put", func(c *gin.Context) {
        c.String(200, "PUT Request")
    })

    r.DELETE("/delete", func(c *gin.Context) {
        c.String(200, "DELETE Request")
    })

    r.PATCH("/patch", func(c *gin.Context) {
        c.String(200, "PATCH Request")
    })

    r.HEAD("/head", func(c *gin.Context) {
        c.String(200, "HEAD Request")
    })

    r.OPTIONS("/options", func(c *gin.Context) {
        c.String(200, "OPTIONS Request")
    })

    r.Run() // 监听 0.0.0.0:8080
}
```

**特点：**

- **最常用的方式**，直接通过 `HTTP方法` 定义路由，适用于大多数 API 设计场景。

#### （2）使用 `Any()` 处理所有 HTTP 方法

​	`Any()` 方法可以让 **同一路由支持所有的 HTTP 请求方法**（`GET`、`POST`、`PUT`、`DELETE`、`PATCH`、`HEAD`、`OPTIONS` 等）。

```go
r.Any("/any", func(c *gin.Context) {
    c.String(200, "This is an Any Route, HTTP Method: %s", c.Request.Method)
})
```

特点：

- **适用于调试**，如果你想让一个路径对所有请求方式都生效，可以使用 `Any()` 。
- **不建议用于生产 API 设计**，通常应按具体的 HTTP 方法区分业务逻辑

#### （3）使用 `NoRoute()` 处理未匹配的路由

​	当客户端访问 **未定义的路由** 时，Gin 提供 `NoRoute()` 方法用于**自定义 404 处理逻辑**。

```go
r.NoRoute(func(c *gin.Context) {
    c.JSON(404, gin.H{
        "message": "Route Not Found",
    })
})
```

**特点：**

- **适用于全局 404 处理**，增强 API 友好性。

### 定义路由变量

（1）冒号语法（如 `/user/:id`）捕获单个路径段；

（2）通配符语法（如 `/user/:name/*action`）捕获剩余路径（包含`*`前面的`/`）。

```go
r.v("/user/:id", func(c *gin.Context) { 
    id := c.Param("id"); 
    c.String(200, "User ID: " + id) 
})

```

​	当访问 `/user/123` 时，`:id` 捕获 `123`，并可通过 `c.Param("id")` 获取对应值。

```go
r.GET("/user/:name/*action", func(c *gin.Context) { 
    name := c.Param("name"); 
    action := c.Param("action"); 
    c.String(200, name + " is " + action) 
})
```

​	当访问 `/user/john/send` 时，`name` 为 `john`，`action` 为 `/send`，输出 `john is /send`"。

​	当访问 `/user/john` 时，`name` 为 `john`，`action` 为空字符串，输出 `john is` 。

​	当访问 `/user/john/send/hello` 时，`name` 为 `john`，`action` 为`/send/hello`，输出 `john is /send/hello`。

### 路由到静态资源

#### router.Static方法

```go
func (group *RouterGroup) Static(relativePath, root string) IRoutes {
	return group.StaticFS(relativePath, Dir(root, false))
}
```



```go
func main() {
    r := gin.Default()
    r.Static("/static", "./public")
    r.Run(":8080")
}
```

​	将 `./public` 目录下的文件通过 `/static` 路径提供。

​	例如，访问 `/static/css/style.css` 会返回 `./public/css/style.css`。

​	如果文件不存在，则返回`404 page not found`。

#### router.StaticFS方法

​	

```go
// StaticFS works just like `Static()` but a custom `http.FileSystem` can be used instead.
// Gin by default uses: gin.Dir()
func (group *RouterGroup) StaticFS(relativePath string, fs http.FileSystem) IRoutes {
	if strings.Contains(relativePath, ":") || strings.Contains(relativePath, "*") {
		panic("URL parameters can not be used when serving a static folder")
	}
	handler := group.createStaticHandler(relativePath, fs)
	urlPattern := path.Join(relativePath, "/*filepath")

	// Register GET and HEAD handlers
	group.GET(urlPattern, handler)
	group.HEAD(urlPattern, handler)
	return group.returnObj()
}
```







### 路由分组

## 请求信息

### 获取请求信息

#### 请求的HTTP方法

#### 请求的路径

#### 请求携带的Cookie

#### 请求头

#### 请求参数

##### GET请求参数



##### 表单请求参数



##### 查询参数参数



#### 表单上传的文件

#### 转换获取到的数据到指定类型的变量中



### 设置请求信息



## 响应数据

### 响应方式

### 重定向

#### HTTP重定向

#### 路由重定向

## 中间件

### 中间件的类型

### 中间件的定义

