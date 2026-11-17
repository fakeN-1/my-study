# Fsatapi
- 是一个基于python的高性能web框架
>FastAPI 就是用 Python 写后端 API 接口的框架。
### 创建项目:
- 创建项目的时候需要先创建虚拟环境
> 目的是为了隔离项目的运行环境,避免依赖冲突,保持全局环境的干净和稳定.
### 如何运行FastAPI
1. 使用run
2. 使用命令行运行项目: uvicorn main:app --reload
- 其中加上--reload可以试试展示修改后的代码(修改代码,重启服务器)
><img width="762" height="275" alt="image" src="https://github.com/user-attachments/assets/8b1704b8-117b-444b-880a-a6f0c6e3eb72" />
- 这里面的main为文件名,app为FastAPI 的实例
在运行的时候打开一个本地的域名:http://127.0.0.1:8000
><img width="506" height="100" alt="image" src="https://github.com/user-attachments/assets/970243f6-f2ce-481d-9d18-6b9860699db7" />

-在这个域名后面加上/docs就可以打开一个交互式文档
><img width="951" height="432" alt="image" src="https://github.com/user-attachments/assets/a33f07ca-2892-4615-88cb-29de2a0ac5f0" />
# 路由
- 路由的作用就是:用户访问某个网址的时候,去决定运行哪段函数代码.
> FastAPI 的路由定义基于python的装饰器模式
```python
@app.get("/hello")
async def root():
  return {"message":"hello,FastAPI"}
```
- 其中@后面就是装饰器的内容,/hello是访问路径(请求路径)
- 当访问http://127.0.0.1:8000/hello,就可以获取函数中的结果.
><img width="435" height="111" alt="image" src="https://github.com/user-attachments/assets/583d1a5a-c5fb-46a7-b8ee-ad93a6216bb0" />
# 参数
- 参数就是客户端发送请求附带的额外信息.
- 常见参数"
1. 路径参数
2. 查询参数
3. 请求体参数
### 路径参数
```python
@ app.get("/book/{id}")
async def get_book(id: int):
    return {"id": id, "title": f"这是第{id}本书籍"}
```
- id出现在URL路径上
- id:int表示id的形参类型
><img width="421" height="126" alt="image" src="https://github.com/user-attachments/assets/c82f6a22-4826-4cec-a01c-3385388a1a56" />
-同样,在交互式文档也可以查看
><img width="1297" height="1185" alt="image" src="https://github.com/user-attachments/assets/a36f1f4d-44c9-423b-b719-b44a2be82cc9" />
*** 这里id的路径参数是必须要填写的 ***

- 路径参数位于URL路径的一部分
---
- ***复杂的路径参数注解: Path***
- path:允许为参数去声名额外的信息
> 参数的位置是函数的形参之后:
```python
@ app.get("/book/{id}")
async def get_book(id: int = Path(...,gt=0,lt=100,description="这里是书籍的id:")):
    return {"id": id, "title": f"这本书的名字是{id}"}
```
- id= int-Patt()就是复杂的参数注解的书写格式
> P需要大写,Path()中的形参有很多,比如:<img width="298" height="195" alt="image" src="https://github.com/user-attachments/assets/39bf13fe-ea70-4846-9db5-6865463751a7" />
- Path()能够对参数进行限制,比如min_lenght表示最短的字数限制.
``` python
@ app.get("/auther/{name}")
async def get_name(name: str=Path(...,min_length=1,max_length=20,description="这里是书籍的作者名字")):
    return {"作者":f"这本书的作者是{name}"}
```
> 以上就是限制的名字的字数, 其中:...表示必须填写. description表示的是注解.
---
### 查询参数
- 当声名的参数不是路径参数的时候,会自动把参数解释为查询参数
- 查询参数可以给形参的赋值
> 这个参数会出现的URL的?之后.
```python
# 查询参数,查询新闻 skip:记录跳过的数量.limit:返回的记录数值,固定值10
@ app.get("/news_list")
async def get_news_list(skip:int,limit : int=10):
    return {"skip":skip, "limit":limit}
```
><img width="1226" height="1045" alt="image" src="https://github.com/user-attachments/assets/3fdd88c1-f183-4bf3-be46-a82c56d1fae8" />

- 查询参数在URL的位置是:http://127.0.0.1:8000/news_list?skip=12&limit=10
> 在❓之后
*** 查询参数的复杂注解 Query ***
> 这个函数和之前的Path的参数写法十分相似.
```python
skip:int=Query(...,gt=0,lt=100,description="跳过的记录数"),
```












