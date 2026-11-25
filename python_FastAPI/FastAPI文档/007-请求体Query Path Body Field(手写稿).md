<img width="826" height="199" alt="image" src="https://github.com/user-attachments/assets/adbb65df-3f4d-45c9-b431-866699ba1e62" /># 多个请求体
实例:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None


class User(BaseModel):
    username: str
    full_name: str | None = None


@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Item, user: User):
    results = {"item_id": item_id, "item": item, "user": user}
    return results
```
- 也就是多个参数



# 请求体的单一值

```
from typing import Annotated

from fastapi import Body, FastAPI
from pydantic import BaseModel

app = FastAPI()


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None


class User(BaseModel):
    username: str
    full_name: str | None = None


@app.put("/items/{item_id}")
async def update_item(
    item_id: int, item: Item, user: User, importance: Annotated[int, Body()]
):
    results = {"item_id": item_id, "item": item, "user": user, "importance": importance}
    return results
```
- `Annotated[int, Body()`
- body 的用法和Query与Path相似.
<img width="917" height="340" alt="image" src="https://github.com/user-attachments/assets/3c20da34-282a-4726-a237-237ecd155149" />

-  Path：从 URL 路径中获取。
-  Query：从 URL 问号后面获取。
-  Body：从请求体中获取。
-  >  你希望用户把某个数据放在 HTTP 请求体（通常是 JSON）中发送，而不是放在 URL 里面时，就使用 Body()
   
# field
`from pydantic import Field`
- 与前面三个的用法一样
- 只不过field只用于pydantic声明的模型内部
- 和前三个的位置不一样
```python
from typing import Annotated

from fastapi import Body, FastAPI
from pydantic import BaseModel, Field

app = FastAPI()


class Item(BaseModel):
    name: str
    description: str | None = Field(
        default=None, title="The description of the item", max_length=300
    )
    price: float = Field(gt=0, description="The price must be greater than zero")
    tax: float | None = None


@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Annotated[Item, Body(embed=True)]):
    results = {"item_id": item_id, "item": item}
    return results
```
- ` description: str | None = Field(default=None, title="The description of the item", max_length=300)`
- 这里就是对description的校验.
- 注意:与从 fastapi 导入 Query，Path、Body 不同，要直接从 pydantic 导入 Field 。

##  Query，Path、Body, Field
- 这四个的工作方式和参数是相同的.
> <img width="826" height="199" alt="image" src="https://github.com/user-attachments/assets/c2095351-b701-4d47-8398-f22cf61db503" />

# 请求体-嵌套模型
- Pydantic 模型的每个属性都具有类型
- 因此可以进行嵌套
例子:
```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()


class Image(BaseModel):
    url: str
    name: str


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None
    tags: set[str] = set()
    image: Image | None = None


@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Item):
    results = {"item_id": item_id, "item": item}
    return results
```
注意:  `image: Image | None = None`
- 其中的image是一个单独的pydantic模型

输出的结果为:
>{
    "name": "Foo",
    "description": "The pretender",
    "price": 42.0,
    "tax": 3.2,
    "tags": ["rock", "metal", "bar"],
    "image": {
        "url": "http://example.com/baz.jpg",
        "name": "The Foo live"
    }
}


## 特殊的类型和校验
- 出了str,int,list这些普通的类型以外
- 还有一些特殊的类型
 比如:HttpUrl:
```python
from fastapi import FastAPI
from pydantic import BaseModel, HttpUrl

app = FastAPI()


class Image(BaseModel):
    url: HttpUrl
    name: str


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None
    tags: set[str] = set()
    image: Image | None = None


@app.put("/items/{item_id}")
async def update_item(item_id: int, item: Item):
    results = {"item_id": item_id, "item": item}
    return results
```
这个HttpUrl需要使用pydantic导入
- 他的含义是记录`"http://example.com/baz.jpg"`类似这样的网址

## 深度嵌套
- 也可以任意去定义更加深度的模型:
```python
from fastapi import FastAPI
from pydantic import BaseModel, HttpUrl

app = FastAPI()


class Image(BaseModel):
    url: HttpUrl
    name: str


class Item(BaseModel):
    name: str
    description: str | None = None
    price: float
    tax: float | None = None
    tags: set[str] = set()
    images: list[Image] | None = None


class Offer(BaseModel):
    name: str
    description: str | None = None
    price: float
    items: list[Item]


@app.post("/offers/")
async def create_offer(offer: Offer):
    return offer
```
这个例子就嵌套了三层

### 纯列表请求体
`async def create_multiple_images(images: list[Image]):`
使用` list[Image}`能够让最后输出的images变成一个列表
Image只是一个模型的名称

### 任意dict构成的请求体
实例:
```python
from fastapi import FastAPI

app = FastAPI()


@app.post("/index-weights/")
async def create_index_weights(weights: dict[int, float]):
    return weights
```
这里的`dict[int, float`
- 表示字典的结构
- 类似于 int:float
- 也就是key值为int,Value值为float
> weights: dict[int, float] = {
    1: 0.5,
    2: 0.8,
    3: 1.2
}

























   
