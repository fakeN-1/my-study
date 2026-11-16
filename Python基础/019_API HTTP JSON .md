# API（应用程序编程接口）

## 1. 实际调用 API：ipify

[ipify 官网](https://www.ipify.org/)：提供查询当前公网 IP 地址的 API 服务。

- 通过终端调用，可以获得自己的公网 IP 地址。

```bash
curl "https://api.ipify.org?format=json"
```

返回结果：

```json
{"ip":"43.203.246.10"}
```

**请求分析：**
- URL：`https://api.ipify.org`
- Method：GET（默认请求方法）
- Parameters：`format=json`
- Response：JSON 格式的公网 IP 数据。

以上就是一次完整的 API 调用，包含发送请求和接收响应两个过程。

---

## 2. 什么是 API？

- Application Programming Interface —— 应用程序编程接口。
- 简单来说，API 就是程序之间进行交互的接口。
- 它规定了调用方可以使用什么功能、需要提供什么参数，以及能够获得什么结果。

例如：
- 前端调用后端 API，获取用户信息。
- Python 调用 DeepSeek API，获取 AI 回复。
- 一个后端服务调用另一个服务，获取天气数据。

> API 这个入口并不关心功能具体使用什么语言或者方式实现，只关心调用规则和返回结果。

## 3. 什么是 HTTP？

HTTP（HyperText Transfer Protocol）—— 超文本传输协议。

- HTTP 是一种应用层通信协议。
- 规定客户端和服务器之间如何发送请求、接收响应。
- 前后端通常通过 HTTP 协议进行数据交换。

### HTTP 的两个核心过程

1. Request（请求）：客户端向服务器发送请求。
2. Response（响应）：服务器处理请求后返回结果。

### 常见 HTTP 请求方法

| 方法 | 作用 |
|---|---|
| GET | 获取数据 |
| POST | 提交数据 |
| PUT | 完整更新数据 |
| PATCH | 部分更新数据 |
| DELETE | 删除数据 |

记忆：
- GET = 获取
- POST = 提交

### HTTP 状态码

| 状态码 | 含义 |
|---|---|
| 200 | 请求成功 |
| 201 | 创建成功 |
| 400 | 请求参数错误 |
| 401 | 未授权 |
| 403 | 禁止访问 |
| 404 | 资源不存在 |
| 500 | 服务器内部错误 |

记忆：
- 2XX：请求成功
- 3XX：重定向
- 4XX：客户端错误
- 5XX：服务器错误

## 4. 什么是 JSON？

JSON（JavaScript Object Notation）—— 一种轻量级的数据交换格式。

作用：让不同编程语言之间能够按照统一格式交换数据。

例如：

```json
{
    "name": "Yui",
    "age": 22,
    "message": "你好"
}
```

- JavaScript 可以解析 JSON。
- Python 可以解析 JSON。
- 前后端可以通过 JSON 交换数据。

注意：JSON 是数据格式，不是编程语言，也不是 HTTP 协议。

## 5. 调用 API 需要什么？

一次常见的 HTTP API 请求可以包含：

1. URL：请求地址，确定调用哪个接口。
2. Method：请求方法，例如 GET、POST。
3. Headers：请求头，传递数据类型、身份认证等信息。
4. Parameters：查询参数，向接口传递额外条件。
5. Body：请求正文，通常用于 POST 等请求，传递具体数据。

注意：不同 API 的要求不同，不是每次请求都必须包含以上所有内容。

## 6. 前后端通过 API 连接的流程

以 AI 聊天网页为例：

1. 用户在网页中输入内容，点击发送。
2. 前端（HTML / CSS / JavaScript）收集用户输入。
3. 前端使用 fetch / axios 发起 HTTP 请求。
4. 后端 API（Python / FastAPI）接收请求。
5. 后端进行参数校验和业务逻辑处理。
6. 后端根据需要调用数据库或第三方 API（例如 DeepSeek）。
7. 后端将处理结果封装成 JSON，通过 HTTP 响应返回。
8. 前端解析返回的数据，并将结果渲染到网页上。
<img width="1672" height="941" alt="07705c9d-291e-48c9-98b0-9c6d62c57633" src="https://github.com/user-attachments/assets/fef76aba-7e9e-40ed-aabc-cf485e8d066f" />

**核心数据流：**

用户操作 → 前端收集数据 → API 请求（HTTP）→ 后端处理 → 数据库 / 第三方服务 → 返回 JSON → 前端渲染结果

## 7. 三个核心概念的区别

| 概念 | 主要作用 |
|---|---|
| API | 规定程序之间如何调用功能 |
| HTTP | 规定客户端与服务器如何通信 |
| JSON | 规定数据如何组织和交换 |

记忆：

API 是接口，HTTP 是通信规则，JSON 是数据格式。
