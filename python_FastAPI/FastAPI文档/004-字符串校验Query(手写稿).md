# 校验
- 简单来说就是给参数添加的限制
- 参数满足限制条件就能够正常输出
- 不满足则会输出`422`报错

## 导入 Query 和 Anitated
依次导入:
- `from typing import Annotated`
- `from fastapi import FastAPI, Query`

完整使用代码展示:
```python
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[str | None, Query(max_length=50)] = None):
    results = {"items": [{"item_id": "Foo"}, {"item_id": "Bar"}]}
    if q:
        results.update({"q": q})
    return results
```

分析 : `async def read_items(q: Annotated[str | None, Query(max_length=50)] = None):`
- 这里Annotated的使用方法:`Annotated[数据类型, 附加信息]`
- Query()中里面的括号中填写限制条件,代码中表示字数不超过50字
- 最后的`=None`表示默认数值为None

### 多个数值
```
from typing import Annotated

from fastapi import FastAPI, Query

app = FastAPI()


@app.get("/items/")
async def read_items(q: Annotated[list[str] | None, Query()] = None):
    query_items = {"q": q}
    return query_items
```
- 在`Annotated[数据类型, 附加信息]`
- 里面的数据类型可以填写列表
- 也可以直接填写list

# 注释
`q: Annotated[
        str | None,
        Query(
            title="Query string",
            description="Query string for the items to search in the database that have a good match",
            min_length=3,
        ),
    ] = None,`
同样可以像这样填写注释.
