# YOLO

## YOLO的训练集

## YOLO训练图片
### 训练标注图片的脚本
>本文件的该脚本保存在mytrain.py文件中
```
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





