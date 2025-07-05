
---

```yaml
nav: Development
group:
  title: Examples
  order: 3
title: Simple Example
order: 5
toc: content
```

---

## Create Article Feature

Now that your development environment is set up, you can get started.

In go-admin, you only need to focus on your business logic. You don't have to worry about the foundational functions, project scaffolding, permission management, or UI choices. It’s all handled — so you can focus purely on writing code.

The project structure was explained earlier, so we won’t repeat it here.

---

## Writing the First API Endpoint

Create a file named `article.go` in the `apis` directory:

```go
package apis

import (
 "github.com/gin-gonic/gin"
 "go-admin/common/apis"
)

type Article struct {
 apis.Api
}

// GetArticleList - Fetches the article list
func (e Article) GetArticleList(c *gin.Context) {
 err := e.MakeContext(c).Errors
 if err != nil {
  e.Logger.Error(err)
  return
 }
 e.OK("hello world!", "success")
}
```

This is the simplest API endpoint in go-admin.
To see it in action, we need to map a URL to this endpoint — that’s where the router comes in.

Here’s the project directory structure:

```bash
go-admin
  app
    admin
      apis
      models
      router
      service
        dto
```

Inside `go-admin/app/admin/router/article.go`, add the following code:

```go
package router

import (
 "go-admin/app/admin/apis"

 "github.com/gin-gonic/gin"
 jwt "github.com/go-admin-team/go-admin-core/sdk/pkg/jwtauth"
)

func init() {
 routerCheckRole = append(routerCheckRole, registerArticleRouter)
}

// Authenticated routes
func registerArticleRouter(v1 *gin.RouterGroup, authMiddleware *jwt.GinJWTMiddleware) {
 api := apis.Article{}
 r := v1.Group("")
 {
  r.GET("/articleList", api.GetArticleList)
 }
}
```

Now that the API endpoint is registered in the router, run the following command to verify that everything works:

```bash
go build

./go-admin server -c=config/settings.dev.yml
```

Visit [http://localhost:8000/api/v1/articleList](http://localhost:8000/api/v1/articleList) in your browser, and you should see the following response:

```json
{
  "requestId": "4085aca9-1ea2-4088-8e26-8ba0bc4e8bdb",
  "code": 200,
  "msg": "success",
  "data": "hello world!"
}
```

This response is exactly what you defined in the interface.

---

### Router Registration Types

Common HTTP methods used for registering routes are: `GET`, `POST`, `PUT`, `DELETE`, etc.

Each route requires two parameters: `path` and `handler(s)`. Let’s understand what these mean.

#### path

`path` is a URL matching rule (somewhat like a regex). When go-admin receives a request, it checks registered routes in order until it finds a match.

These rules do not match GET/POST query parameters or domains.
For example, a request to [http://www.zhangwj.com/articleList](http://www.zhangwj.com/articleList) will attempt to match `articleList`.
A request to [http://www.zhangwj.com/articleList?page=3](http://www.zhangwj.com/articleList?page=3) will **still** match `articleList`.

`path` can also accept dynamic parameters. For example:
`r.GET("/articleList/:id", apis.GetArticleList)`
This will match `/articleList/:id`, where `:id` can be any string, number, etc. You can even apply constraints — but that’s beyond the scope here.

---
