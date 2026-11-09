# YOLO

## YOLO的数据集
### 数据集的内容
- 数据集一般包含**训练集(train)**和**验证集(val)**,以及两个图片集的标签和命名文本.
- 测试模型效果的时候还会有测试集,测试集不参与训练
><img width="1020" height="433" alt="image" src="https://github.com/user-attachments/assets/1fa621ba-337b-4879-b25b-176abd1c110e" />

## YOLO的训练准备
- 一个包含完整数据集的文件夹.
- 数据的配置文件**.yaml**格式,用于告诉yolo训练脚本数据集的位置.
- 一个用于训练的python脚本(本工程中命名为matrain.py)
> <img width="1050" height="424" alt="image" src="https://github.com/user-attachments/assets/ffb16b59-9e81-4401-9f3f-0f60434947b4" />


## YOLO训练图片的方式
### 训练标注图片的脚本
>本文件的该脚本保存在mytrain.py文件中
``` python
from ultralytics import YOLO
if __name__=="__main__":
    model=YOLO(r"yolo11n.pt")
    model.train(
        data=r"D:\yolo_v8.3\ultralytics\cfg\datasets\Pet.yaml",
        epochs=80,#训练10轮
        imgsz=640,#图片的最长边
        batch=18,#分批次训练
        cache=False,#=raw在图片尺寸大的时候可以提高训练速度
        workers=1,
        project="runs/detect",
        name="yolo_11n",
        # val=False,这段是选择是否验证
    )
```
### 训练后的文件
- 训练后的文件一般保存在runs/....文件中,脚本中的name为子文件的命名.
- 训练后输出一些训练效果的文件,以及一个best.pt的训练模型.
><img width="1065" height="547" alt="image" src="https://github.com/user-attachments/assets/412905d3-f505-4d41-8d5e-2a03f791d9ec" />

## yaml文件的制作
- 之前提到的第二步是制作yaml格式的文件,用于告诉脚本训练集的位置.
> 脚本的格式:
><img width="1065" height="647" alt="image" src="https://github.com/user-attachments/assets/40854991-75c0-4cc5-af96-cfbc43e2fe14" />
>最简化:
> <img width="649" height="292" alt="image" src="https://github.com/user-attachments/assets/478f6f49-583f-493b-b678-46372cd27662" />

- 其中path是数据集的文件位置.
- train是数据集中训练集的相对位置.
- val是数据集中验证集的相对位置.
- text是数据集测试集的相对位置.(有时候不需要)
- name需要和数据集中的命名位置相同.

## 标签文件
### 标签文件是什么
- 标签文件位于label文件夹的位置和images相互对应
- 简单来说标签就是记录目标位置的数据
> <img width="710" height="442" alt="image" src="https://github.com/user-attachments/assets/3098cecf-688b-4708-a2bc-1c3b065daa3b" />
---
<img width="1040" height="420" alt="image" src="https://github.com/user-attachments/assets/4cd46a11-880d-4be4-8745-a0e76d6fe6dc" />
> 这是属于yolo格式的标签,有这样格式的标签才能够训练图片.
### 如何制作标签文件
- 最简单的方法就是使用**labelimg**人工标注
- 以下就是一些重点的部分:
> <img width="1106" height="107" alt="image" src="https://github.com/user-attachments/assets/64928450-451d-4a42-b8af-5863df18be20" />
- 这两行代码分别代表,切换为labelimg环境
- 打开labelimg,并且告诉文件的位置**输入依次为:images txt labels的位置**









