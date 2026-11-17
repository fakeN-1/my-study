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
- 其中@后面就是装饰器的内容,/hello是访问
- 当访问http://127.0.0.1:8000/hello,就可以获取函数中的结果.
><img width="435" height="111" alt="image" src="https://github.com/user-attachments/assets/583d1a5a-c5fb-46a7-b8ee-ad93a6216bb0" />

# 请求和响应
- 从客户端通过HTTP接口到应用端,最后再返回到客户端
















