# FastAPI基础
- 一个简单的FsatAPI类似于:
```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
async def root():
    return {"message": "Hello World"}
```
- 这样的代码一般会被保存在main.py文件夹中,那么使用以下代码就可以启动Fsatapi.
> vicorn app.main:app --reload
- 网页的输出结果为:
><img width="345" height="110" alt="image" src="https://github.com/user-attachments/assets/336343b1-cb97-42ee-b249-062308d48da0" />
也可以在路径中加入docs,比如:***http://127.0.0.1:8000/docs***去打开官方的文档
> <img width="725" height="343" alt="image" src="https://github.com/user-attachments/assets/ddc00434-4e2c-4e55-aea6-e7c362d00911" />
这个界面可以更加直观的看到运行的实时操作.

## 路径
- 路径也就是URL的最后面部分,比如:
>http://127.0.0.1:8000/docs
这个URL 的路径就是:
>/docs

## 操作
常见操作:
- POST : 创建数据
- GET : 读取数据
- PUT : 更新数据
- DELETE : 删除数据
比如:
- 代码*** @app.get("/") ***
> 就是请求URL 中的路径为/的地址,使用get操作.这里的***@***部分又叫做装饰器.

