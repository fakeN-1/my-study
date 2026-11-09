# YOLO

## YOLO的数据集
### 数据集的内容
- 数据集一般包含**训练集(train)**和**验证集(val)**,以及两个图片集的标签和命名文本.
- 测试模型效果的时候还会有测试集,测试集不参与训练
><img width="1020" height="433" alt="image" src="https://github.com/user-attachments/assets/1fa621ba-337b-4879-b25b-176abd1c110e" />

## YOLO的训练流程
### yolo训练的准备
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






