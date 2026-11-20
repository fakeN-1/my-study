# ORM学习
> ORM是一种操作数据库的编程思想(面向对象),SQLAlchemy 是 Python 中实现这种思想的工具之一,
---
>FastAPI 负责提供 API，SQLAlchemy 负责在 Python 中操作数据库，MySQL / SQLite 等数据库负责真正存储数据。
# 使用aqlalchemy
### 第一步骤:ORM中的sql 的安装
> 安装两个第三方库 1.sqlalchemy[asyncio]  2.aiomysql
### 第二步骤:建库建表
1.创建数据库引擎:
> create_async_engine
from sqlalchemy.ext.asyncio import 
2.定义模型类
> 


