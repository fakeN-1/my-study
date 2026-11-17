## 1. FastAPI 是什么？

FastAPI 是一个用 Python 编写后端 API 的 Web 框架。客户端通过 HTTP 发送请求，FastAPI 根据**请求方法和路径**找到对应的 Python 函数，读取并校验输入，再把函数的结果作为 HTTP 响应返回。

## 2. 创建并运行项目

新建项目时，建议给项目创建独立的虚拟环境 `.venv`。这样每个项目可以安装自己需要的依赖版本，减少项目之间的版本冲突。

在项目目录中启动服务：

```powershell
python -m uvicorn main:app --reload
```

- `main`：Python 模块名，对应 `main.py`，不用写 `.py`。
- `app`：文件中通过 `app = FastAPI()` 创建的实例。
- `--reload`：开发时使用。保存代码后，Uvicorn 检测到文件变化会自动重启应用。

启动后，`127.0.0.1:8000` 是本地服务地址。打开 `http://127.0.0.1:8000/docs`，就能在 Swagger 交互式文档中测试接口。

## 3. 路由：哪个请求交给哪个函数？

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/hello")
async def hello():
    return {"message": "Hello, FastAPI!"}
```

`@app.get("/hello")` 是一个装饰器，它把 **`GET /hello`** 绑定到 `hello()`。用浏览器访问 `http://127.0.0.1:8000/hello` 时，浏览器发出 GET 请求，FastAPI 执行这个函数，并把返回的 Python 字典转成 JSON。

注意：路由同时看**方法**和**路径**。`GET /hello` 和 `POST /hello` 可以交给不同的函数。

## 4. 三种常见参数：客户端把数据放在哪里？

| 参数 | 数据在哪里？ | 例子 | 常见用途 | 补充校验 |
|---|---|---|---|---|
| 路径参数 | URL 的路径里 | `/book/12` 中的 `12` | 指定要操作哪本书 | `Path()` |
| 查询参数 | URL 的 `?` 后面 | `?skip=12&limit=10` | 筛选、排序、分页 | `Query()` |
| 请求体参数 | HTTP 请求正文里 | `{"username": "张三", "password": "demo12345"}` | 提交注册表单、创建或更新数据 | `BaseModel` 定义结构，`Field()` 校验字段 |

以下代码可以按顺序接在上面的 `main.py` 后面。

### 路径参数：我要哪一个？

```python
from fastapi import Path

@app.get("/book/{book_id}")
async def get_book(
    book_id: int = Path(..., gt=0, lt=100, description="书籍编号"),
):
    return {"id": book_id, "title": f"这是第 {book_id} 本书"}

@app.get("/author/{name}")
async def get_author(
    name: str = Path(..., min_length=1, max_length=20, description="作者姓名"),
):
    return {"作者": name}
```

- `/book/{book_id}` 中的 `{book_id}` 要和函数参数同名。访问 `/book/12` 时，FastAPI 会把 `12` 解析为整数，再传给函数。路径参数是必填的。
- `gt=0, lt=100` 表示数值大于 0 且小于 100，因此这里允许 **1～99**。`ge` 和 `le` 则包含边界。
- 字符串长度用 `min_length`、`max_length`。`max_length=20` 包含 20；如果要求**小于 20 个字符**，写 `max_length=19`。

### 查询参数：我要怎么查？

```python
from fastapi import Query

@app.get("/news_list")
async def get_news_list(
    skip: int = Query(..., ge=0, lt=100, description="跳过的记录数"),
    limit: int = Query(10, ge=1, le=100, description="最多返回的记录数"),
):
    return {"skip": skip, "limit": limit}
```

访问 `/news_list?skip=12&limit=10` 时，`?` 表示查询参数开始，`&` 分隔多个参数。

- `skip` 和 `limit` 没有出现在路径模板里，而且都是 `int`，在这个例子里会作为查询参数读取。简单写法是 `skip: int` 和 `limit: int = 10`，需要范围校验和文档描述时再加 `Query()`。
- `skip` 必填，允许 `0`，因为从第一条开始查时不需要跳过记录。
- `limit` 的 `10` 是**默认值**。省略它就用 10；传入 `limit=5` 就用 5。
- 这个练习只是把参数返回给你看，真正的分页还需要用它们去取数据。

### 请求体参数：我要提交什么数据？

```python
from pydantic import BaseModel, Field

class RegisterRequest(BaseModel):
    username: str = Field(..., min_length=1, max_length=20, description="用户名")
    password: str = Field(..., min_length=8, description="密码")

@app.post("/register")
async def register(user: RegisterRequest):
    return {"username": user.username}
```

在 `/docs` 里给 `POST /register` 提交：

```json
{
  "username": "张三",
  "password": "demo12345"
}
```

- `BaseModel` 定义 JSON 里有哪些字段、字段是什么类型；`Field()` 为单个字段添加校验规则和文档描述。这里两个字段都用 `...` 表示必填，密码没有默认值。
- 查询通常用 `GET`，注册通常用 `POST`。这段代码只演示接收和校验数据，还没有保存用户；响应只返回用户名，不回传密码。
- 请求体的数据不会出现在 URL 里，但**放进请求体不等于加密**。实际传输敏感信息时应使用 HTTPS。

## 5. 在 `/docs` 里验证结果

点 **Try it out → Execute** 后，重点看这几项：

- **Curl**：在终端重发同一个请求的命令。
- **Server response → Code**：实际状态码，例如 `200` 表示请求成功，`422` 通常表示输入没通过校验。
- **Response body**：接口实际返回的数据。**Example Value** 只是文档示例。
- **Response headers**：服务器随结果发回的说明，例如 `content-type: application/json` 表示正文是 JSON。

复习时可以试三次：访问 `/book/0`，看编号为什么校验失败；访问 `/news_list?skip=0`，看 `limit` 是否自动取 `10`；提交注册请求时删掉 `password`，看错误信息如何指出缺失字段。
