# Tool Calling:工具调用
## Tool和Tool Calling 的区别
- Tool是工具本身
- Tool calling是模型请求使用这个工具的过程
> 天气查询的时候>>>Tool：天气查询功能，接收城市名并返回天气。
Tool calling：模型判断需要查天气，于是发出“调用天气工具，参数为上海”的请求。

## 应用程序
- 链接用户和LLM,Tool的工具
- 用户>应用程序>LLM>应用程序>Tool>LLM>应用程序>用户
><img width="1236" height="617" alt="image" src="https://github.com/user-attachments/assets/644186af-265a-4ea3-8430-b208bd0f2e4e" />
---
><img width="1202" height="442" alt="image" src="https://github.com/user-attachments/assets/22db0ca1-8ecd-4ff3-8449-637036630db0" />

## Function Calling
- 与Tool calling有轻微不同,Tool Calling更倾向于使用**工具**.而Function Calling更加强调使用**函数**.















