# Cookie
定义 Cookie 参数与定义 Query 和 Path 参数一样。
- 导入 `from fastapi import Cookie`
实例:
```python
from typing import Annotated

from fastapi import Cookie, FastAPI

app = FastAPI()


@app.get("/items/")
async def read_items(ads_id: Annotated[str | None, Cookie()] = None):
    return {"ads_id": ads_id}
```
