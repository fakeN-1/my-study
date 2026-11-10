# 数据的储存
### 数据容器
- 是一种可以容纳多份的数据类型(容器),每一个元素,都可以是单独的任意属性.
> list:列表
> str:字符串
>tuple:元组
> set:集合
> dict:字典
---
### 列表list
- 列表可以一次性存储多个数据.
- 定义:列表名称[元素1,元素2,元素3....]
- 特点:可以存储不同的元素,元素有序,可以重复,可以修改.
><img width="565" height="219" alt="image" src="https://github.com/user-attachments/assets/2546aff3-3a09-4477-b018-5b1d5bbc0448" />

> 可以使用** s[1:] **表述输出第二个数及其之后的全部元素

><img width="460" height="130" alt="image" src="https://github.com/user-attachments/assets/1634b127-7904-4e56-80a7-ba01efd502b2" />

>获取元素的属性为:list

##### 列表的修改
- 修改:s[]
- 删除:关键字del s[]
- 遍历:for item in s :代表把s中的元素遍历给item

###### 列表的切片
- s[开始索引:结束索引:步长],比如s[1:2:2]
> <img width="697" height="148" alt="image" src="https://github.com/user-attachments/assets/c6a1ddf7-fe21-4290-9e7a-dc48d75b7a64" />

###### 列表的常见方法
- 列表内置的常见方法,可以直接调用,使用** s. **调用
> <img width="953" height="268" alt="image" src="https://github.com/user-attachments/assets/fa4d39af-d77b-4c69-a68b-4847c179b031" />
- .sppend(10086):追加元素
- .insert(1,10086):插入元素
- .remove(10086):移除第一个匹配值
- .pop(1):删除索引位置元素
- .sort():对列表进行排序
- .reverse():反转元素

##### 列表案例
- 将用户输入的10个数字，存储到一个列表中，并将列表中的数字进行排序，
><img width="541" height="182" alt="image" src="https://github.com/user-attachments/assets/db812eb0-e16a-4d82-9146-cdd49dfc06fa" />

- 合并两个列表中的元素，并对合并的结果进行去重处理(去除列表中的重复元素)。
><img width="629" height="202" alt="image" src="https://github.com/user-attachments/assets/dfeda6a0-69dd-489e-b448-1628853ec227" />
-set:去除重复元素.


><img width="701" height="155" alt="image" src="https://github.com/user-attachments/assets/d340971b-cf77-400d-8c67-3e32758f1246" />


















