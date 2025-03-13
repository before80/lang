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
> ```sh
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
> ```sh
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
> ```sh
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
> ​	Gin 的路由匹配采用 **Radix Tree**，相比传统线性匹配（O(m)），它可以更快地匹配 URL 路由，适用于高并发场景。
>
> **Gin 的路由存储示例**
>
> ​	假设注册以下路由：
>
> ```sh
> /users
> /users/:id
> /users/:id/profile
> /articles/:category/:id
> ```
>
> **Radix Tree 存储结构：**
>
> ```sh
>       /
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
> **4. 总结**
>
> - **Radix Tree 通过合并前缀减少存储空间，提高匹配效率。**
> - **Gin 使用 Radix Tree 来优化 URL 路由匹配，提升查询速度。**
> - **查询时间复杂度通常为 `O(k)`，相比于传统 `O(m)` 线性遍历方式更高效。**

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

​	

```sh
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/user/john/talking                                                                           
john is /talking
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/user/john
<a href="/user/john/">Moved Permanently</a>.

PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/user
404 page not found
```



| 特性         | 冒号语法 `:param`      | 通配符语法 `*param`      |
| ------------ | ---------------------- | ------------------------ |
| **匹配范围** | 单个路径段（不含斜杠） | 剩余所有路径（可含斜杠） |
| **位置限制** | 可出现在路径中间       | 必须位于路由末尾         |
| **参数内容** | 纯字符串（无 `/`）     | 可包含 `/` 的路径字符串  |

### 路由到静态资源



| **方式**            | **方法**                                | **描述**                              | **示例**                                                     |
| ------------------- | --------------------------------------- | ------------------------------------- | ------------------------------------------------------------ |
| 内置方法 - 目录     | `router.Static(prefix, root)`           | 服务目录下所有文件，通过前缀 URL 访问 | `router.Static("/static", "./public")`                       |
| 内置方法 - 文件系统 | `router.StaticFS(prefix, fs)`           | 服务自定义文件系统，通过前缀 URL 访问 | `router.StaticFS("/more_static", http.Dir("my_file_system"))` |
| 内置方法 - 单文件   | `router.StaticFile(url, filepath)`      | 服务单个文件，映射到特定 URL          | `router.StaticFile("/favicon.ico", "./resources/favicon.ico")` |
| 第三方库            | `github.com/gin-contrib/static`         | 提供中间件，支持目录索引、嵌入文件等  | `r.Use(static.Serve("/", static.LocalFile("/tmp", true)))`   |
| 手动处理            | `c.File(filepath)` 或 `http.FileServer` | 自定义处理静态文件请求                | `r.Any("/*path", func(c *gin.Context) { c.File("./public/" + c.Param("path")) })` |

#### router.Static方法

​	将指定目录下的静态文件映射到路由前缀。

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

​	当访问 `/static/css/style.css` 会返回 `./public/css/style.css`（存在该文件的情况）。若文件不存在，则返回`404 page not found`。

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

​	Gin 框架中的 **路由分组** 是一种将具有相同前缀、中间件或功能的路由统一`管理的机制`，能显著提升代码可维护性和扩展性。

#### **路由分组的核心作用**

1. **统一前缀管理**
   为多个路由设置共享的 URL 前缀（如 `/api/v1`），避免重复定义。
2. **中间件共享**
   在分组层级应用中间件（如身份验证、日志），减少冗余代码。
3. **模块化开发**
   将不同业务模块的路由拆分到独立文件，降低耦合度。

#### 用法

##### 基本用法

```go
package main

import (
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()

	// 创建 `/api` 分组
	api := r.Group("/api")
	{
		api.GET("/ping", func(c *gin.Context) {
			c.JSON(200, gin.H{"message": "pong"})
		})

		api.GET("/hello", func(c *gin.Context) {
			c.JSON(200, gin.H{"message": "Hello API"})
		})
	}

	// 启动服务器
	r.Run(":8080")
}
```

- `curl http://localhost:8080/api/ping`返回：`{"message": "pong"}`

##### 嵌套分组

```go
func main() {
	r := gin.Default()

	// `api` 分组
	api := r.Group("/api")
	{
		api.GET("/status", func(c *gin.Context) {
			c.JSON(200, gin.H{"status": "ok"})
		})

		// `api/v1` 子分组
		v1 := api.Group("/v1")
		{
			v1.GET("/users", func(c *gin.Context) {
				c.JSON(200, gin.H{"users": []string{"Alice", "Bob"}})
			})

			v1.GET("/posts", func(c *gin.Context) {
				c.JSON(200, gin.H{"posts": []string{"Post 1", "Post 2"}})
			})
		}
	}

	r.Run(":8080")
}
```

```sh
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/api/ping
{"message":"pong"}
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/api/status
{"status":"ok"}
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/api/v1/users
{"users":["Alice","Bob"]}
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/api/v1/posts
{"posts":["Post 1","Post 2"]}
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/api/v1/nothing
404 page not found
```



##### 为路由分组添加中间件

```go
func AuthMiddleware() gin.HandlerFunc {
	return func(c *gin.Context) {
		token := c.GetHeader("Authorization")
		if token != "valid-token" {
			c.JSON(401, gin.H{"error": "Unauthorized"})
			c.Abort()
			return
		}
		c.Next() // 继续处理请求
	}
}

func main() {
	r := gin.Default()

	// `admin` 组，应用 `AuthMiddleware`
	admin := r.Group("/admin")
	admin.Use(AuthMiddleware()) 
	{
		admin.GET("/dashboard", func(c *gin.Context) {
			c.JSON(200, gin.H{"dashboard": "Welcome Admin!"})
		})
	}

	r.Run(":8080")
}
```

- `curl -H "Authorization: invalid-token" http://localhost:8080/admin/dashboard` 返回：`{"error": "Unauthorized"}`
- `curl -H "Authorization: valid-token" http://localhost:8080/admin/dashboard` 返回：`{"dashboard": "Welcome Admin!"}`

### 路由冲突时gin怎么选择路由？

| 路由类型         | 示例            | 优先级 | 匹配范围             |
| ---------------- | --------------- | ------ | -------------------- |
| **静态路由**     | `/user/profile` | 最高   | 精确匹配             |
| **路径参数路由** | `/user/:id`     | 次高   | 单段动态值（非空）   |
| **通配符路由**   | `/user/*action` | 最低   | 多段动态值（可为空） |

## 请求信息

### 获取请求信息

#### 基本请求信息

```go
c.Request.Method      // 请求方法（GET、POST、PUT、DELETE 等）
c.Request.URL.Path    // 请求路径（如 `/api/user/1`）
c.Request.Proto       // HTTP 版本（如 `HTTP/1.1`）
c.Request.Host        // 请求主机（如 `example.com[:端口]`）
c.Request.RequestURI  // 完整 URI（如 `/api/user?id=1`）
c.Request.RemoteAddr  // 客户端 IP 和端口（如 `192.168.1.100:54321`）
```

#### 请求参数

##### 查询参数



##### 路径参数/路由变量

​	如果定义了 **路由参数/路由变量**，可以用 `Param()` 获取：

```go
r := gin.Default()
r.GET("/user/:name/*action", func(c *gin.Context) {
    name := c.Param("name")
    action := c.Param("action")
    c.String(200, name+" is "+action)
})
r.Run(":8080")
```

```sh
PS D:\GoPrjs2\ginDemo> curl http://localhost:8080/user/john/talking
john is /talking
```



##### 表单参数

| 方法                                  | 适用场景                            | 说明                                |
| ------------------------------------- | ----------------------------------- | ----------------------------------- |
| `c.PostForm("key")`                   | `application/x-www-form-urlencoded` | 获取单个表单参数                    |
| `c.DefaultPostForm("key", "default")` | `application/x-www-form-urlencoded` | 获取表单参数，支持默认值            |
| `c.PostFormMap("key")`                | `application/x-www-form-urlencoded` | 以 `map[string]string` 形式获取参数 |
| `c.MultipartForm()`                   | `multipart/form-data`               | 处理复杂表单和文件上传              |

###### `c.PostForm()`和 `DefaultPostForm` - 获取 `application/x-www-form-urlencoded` 表单参数

​	当表单 `Content-Type` 为 `application/x-www-form-urlencoded` 时，使用 `c.PostForm("参数名")` 获取参数。

```go
package main

import (
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()

	r.POST("/form", func(c *gin.Context) {
		// 获取单个表单参数
		username := c.PostForm("username")
		password := c.PostForm("password")

		// 获取带默认值的参数（如果参数不存在，则返回默认值）
		role := c.DefaultPostForm("role", "user")

		c.JSON(200, gin.H{
			"username": username,
			"password": password,
			"role":     role,
		})
	})

	r.Run(":8080")
}
```

```sh
curl -X POST "http://localhost:8080/form" -d "username=admin&password=123456"
```

> ​	`-X` 的作用是指定 HTTP 请求方法，比如 `GET`、`POST`、`PUT`、`DELETE` 等，是`--header`的简写。它允许你明确指定 HTTP 请求的类型，而不是默认的 `GET` 请求。
>
> ​	`-d` 的作用是 **指定发送的数据**，是`--data`的简写。通常，这些数据会以表单数据（`application/x-www-form-urlencoded`）或 JSON 格式发送，具体取决于请求的 `Content-Type` 头。
>
> >发送表单数据（`application/x-www-form-urlencoded`）
> >
> >```sh
> >curl -X POST "http://example.com/api" -d "username=admin&password=123456"
> >```
> >
> >发送 JSON 数据（`application/json`）
> >
> >```sh
> >curl -X POST "http://example.com/api" \
> >     -H "Content-Type: application/json" \
> >     -d '{"username": "admin", "password": "123456"}'
> >```
> > `-H`用于指定请求头，是`--header`的简写。


返回：

```json
{
  "username": "admin",
  "password": "123456",
  "role": "user"
}
```

###### c.PostFormMap()` - 获取 `map[string]string

​	如果表单参数有多个值，可以用 `c.PostFormMap()` 获取。

```go
package main

import (
	"github.com/gin-gonic/gin"
	"log"
)

func main() {
	r := gin.Default()

	r.POST("/form-map", func(c *gin.Context) {
		// 获取表单数据（map[string]string）
		formData := c.PostFormMap("user")

		// 输出数据
		log.Println("Form Data:", formData)

		// 返回 JSON 响应
		c.JSON(200, gin.H{
			"user": formData,
		})
	})

	r.Run(":8080")
}

```

```sh
curl -X POST "http://localhost:8080/form-map" -d "user[name]=admin&user[email]=admin@example.com&user[password]=123456"
```

​	返回：

```json
{
  "user": {
    "name": "admin",
    "email": "admin@example.com",
    "password": "123456"
  }
}
```



###### `c.MultipartForm()` - 处理 `multipart/form-data`（包括文件上传）

​	`c.MultipartForm()` 用于处理 `multipart/form-data` 类型的请求，通常用于处理文件上传。它返回一个 `*multipart.Form` 类型，可以通过 `Form` 获取表单字段，通过 `File` 获取上传的文件。

```go
package main

import (
	"fmt"
	"github.com/gin-gonic/gin"
	"log"
)

func main() {
	r := gin.Default()

	r.POST("/upload", func(c *gin.Context) {
		// 获取表单字段
		description := c.DefaultPostForm("description", "No description")

		// 获取 multipart/form-data 中的所有文件
		form, err := c.MultipartForm()
		if err != nil {
			c.JSON(400, gin.H{"error": "multipart form parsing error"})
			return
		}

		// 获取文件列表
		files := form.File["file"]

		// 保存每个文件
		for _, file := range files {
			// 保存文件到本地
			dst := fmt.Sprintf("./uploads/%s", file.Filename)
			if err := c.SaveUploadedFile(file, dst); err != nil {
				c.JSON(500, gin.H{"error": "file upload error"})
				return
			}
			log.Println("File saved to:", dst)
		}

		// 返回响应
		c.JSON(200, gin.H{
			"description": description,
			"file_count":  len(files),
		})
	})

	r.Run(":8080")
}
```

> **提示**
>
> ​	若`./uploads`目录不存在，`gin`也会帮你自动创建出来，其权限位为`0750`。

```sh
curl -X POST "http://localhost:8080/upload" -F "description=file description" -F "file=@/path/to/your/file"

curl -X POST "http://localhost:8080/upload" -F "description=Protocol Picture" -F "file=@D:\Downloads\protocol.png"
```

> ​	`curl -F`（或 `curl --form`）用于 **发送 `multipart/form-data` 请求**，这是表单提交中常用的内容类型，尤其用于上传文件。它允许你发送一个包含表单字段和文件的请求。
>
> ​	语法如下：
>
> ```sh
> curl -F "<field_name>=<field_value>" <URL>
> ```
>
> - `<field_name>`：表单字段的名称。
>
> - `<field_value>`：字段的值。如果字段是文件，使用 `@<file_path>` 来指定文件路径。

#### Cookie



#### 请求头

```go
c.GetHeader("User-Agent") // 获取单个请求头
c.Request.Header          // 获取所有请求头（map[string][]string）
c.Request.Header.Get("Content-Type") // 获取特定请求头
c.Request.Header.Values("Accept") // 获取多值请求头
```

```go
package main

import (
	"fmt"
	"github.com/gin-gonic/gin"
)

func main() {
	r := gin.Default()

	r.Any("/headers", func(c *gin.Context) {
		// 获取单个请求头（User-Agent）
		userAgent := c.GetHeader("User-Agent")

		// 获取所有请求头（map[string][]string）
		allHeaders := c.Request.Header

		// 获取特定请求头（Content-Type）
		contentType := c.Request.Header.Get("Content-Type")

		// 获取多值请求头（Accept）
		acceptValues := c.Request.Header.Values("Accept")

		// 输出所有信息
		c.JSON(200, gin.H{
			"User-Agent":   userAgent,
			"All-Headers":  allHeaders,
			"Content-Type": contentType,
			"Accept":       acceptValues,
		})

		// 在服务器终端打印
		fmt.Printf("User-Agent:%v\n", userAgent)
		fmt.Printf("All-Headers:%v\n", allHeaders)
		fmt.Printf("Content-Type:%v\n", contentType)
		fmt.Printf("Accept: %v\n", acceptValues)
	})

	r.Run(":8080") // 运行服务器
}
```

​	返回类似以下结果：

```json
{
  "Accept": [
    "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7"
  ],
  "All-Headers": {
    "Accept": [
      "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7"
    ],
    "Accept-Encoding": [
      "gzip, deflate, br, zstd"
    ],
    "Accept-Language": [
      "zh-CN,zh;q=0.9"
    ],
    "Connection": [
      "keep-alive"
    ],
    "Sec-Ch-Ua": [
      "\"Chromium\";v=\"134\", \"Not:A-Brand\";v=\"24\", \"Google Chrome\";v=\"134\""
    ],
    "Sec-Ch-Ua-Mobile": [
      "?0"
    ],
    "Sec-Ch-Ua-Platform": [
      "\"Windows\""
    ],
    "Sec-Fetch-Dest": [
      "document"
    ],
    "Sec-Fetch-Mode": [
      "navigate"
    ],
    "Sec-Fetch-Site": [
      "none"
    ],
    "Sec-Fetch-User": [
      "?1"
    ],
    "Upgrade-Insecure-Requests": [
      "1"
    ],
    "User-Agent": [
      "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36"
    ]
  },
  "Content-Type": "",
  "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/134.0.0.0 Safari/537.36"
}
```



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

