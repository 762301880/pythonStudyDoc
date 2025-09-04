# 资料

| 名称            | 地址                                                         |
| --------------- | ------------------------------------------------------------ |
| yolo-v8中文文档 | [link](https://docs.ultralytics.com/zh/models/yolov8/#performance-metrics) |
|                 |                                                              |



# yolo环境安装

> ultralytics(就是yolo这个包的叫法)

```python
pip install ultralytics
```

# 案例

## yoloV8实现口罩识别

**口罩数据集下载**

> [down](https://universe.roboflow.com/laptrinhcsc-gvk8t/mask-9xaf0)     
>
> [我的训练集下载-训练了50次]()

在你的数据集根目录下，新建一个 `data.yaml` 文件，内容大概这样：

```yaml
# data.yaml
train: C:/train/images
val: C:/valid/images
test: C:/test/images

nc: 2  # 类别数量（比如 2：with_mask / without_mask）
names: ['with_mask', 'without_mask']
```

> ⚠️ 注意：路径要改成你本机数据集的实际路径。
>  如果还有第三类（比如 *mask_incorrect*），就把 `nc: 3`，然后 `names: ['with_mask', 'without_mask', 'mask_incorrect']`。

**开始训练**

在命令行运行：

```bash
yolo detect train data=C:/data.yaml model=yolov8n.pt epochs=50 imgsz=640
```

参数解释：

- `data=C:/data.yaml` → 指定刚才写好的配置文件
- `model=yolov8n.pt` → 使用轻量级 YOLOv8n 预训练模型（你也可以换成 yolov8s.pt、yolov8m.pt 等）
- `epochs=50` → 训练 50 个 epoch（可以调大）
- `imgsz=640` → 输入图片大小（640×640，常用值）

**查看训练结果**

训练完成后会在 `runs/detect/train/` 目录下生成：

- `weights/best.pt`（最佳模型，用于推理）
- `results.png`（训练曲线）
- `confusion_matrix.png`（混淆矩阵）

**推理测试**

训练好以后可以用新模型进行检测：

```python
from ultralytics import YOLO
import cv2

# 加载训练好的模型
model = YOLO("runs/detect/train/weights/best.pt")

img = "test.jpg"  # 测试图片路径
results = model(img, show=True)  # show=True 会弹窗显示
```



# 本地训练

##  代码中训练

> 下载的数据集已经解压

```python
# =========================================================
# 1. 导入库
# =========================================================
from ultralytics import YOLO
import os

# =========================================================
# 2. 数据集路径
# =========================================================
yaml_path = r"C:\Users\铺先生技术研发中心\Downloads\mask.v1i.yolov8\data.yaml"  # 修改为你本地路径

if not os.path.exists(yaml_path):
    raise FileNotFoundError(f"❌ dataset.yaml 没找到: {yaml_path}")
print("✅ 找到数据集配置文件:", yaml_path)

# =========================================================
# 3. 设置模型保存目录（Windows路径）
# =========================================================
save_dir = r"C:\Users\铺先生技术研发中心\Downloads\mask.v1i.yolov8\yolo_weights"
os.makedirs(save_dir, exist_ok=True)  # 不存在则创建

# =========================================================
# 4. 开始训练
# =========================================================
model = YOLO("yolov8n.pt")  # 使用 nano 模型
model.train(
    data=yaml_path,
    epochs=50,
    imgsz=640,
    batch=16,
    save_period=5,
    project=save_dir,      # 保存训练结果目录
    name="train"           # 子目录名，会生成 save_dir\train\weights
)

# =========================================================
# 5. 保存 best.pt 到指定路径
# =========================================================
best_model_path = os.path.join(save_dir, "train", "weights", "best.pt")
if os.path.exists(best_model_path):
    print(f"✅ 训练完成，best.pt 在: {best_model_path}")
else:
    print("❌ 没找到 best.pt，请检查训练是否正常结束！")

```



#  云训练模型

## [Colab](https://colab.research.google.com/?utm_source=chatgpt.com#scrollTo=C1hZOXhYMH63)

**修改gpu加速**

>  在菜单栏中选择“修改 > 笔记本设置”，将硬件加速器改为 GPU。 重新连接后执行代码。

![image-20250903161232849](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/image-20250903161232849.png)



**GPU训练返回**

> **补充一下GPU真他妈快**
>
>  “`GPU_mem`” 列的数值（如`2.54G`、`2.71G`、`2.73G`等）可以看出，**GPU 已经在被使用了**。
>
> “`GPU_mem`” 这一列显示的是当前训练过程中 GPU 的内存使用量，有具体的数值就说明 GPU 正在为模型训练任务分配和使用内存资源，参与到了 YOLOv8 的训练计算中。

![image-20250903162130924](https://gitee.com/yaolliuyang/blogImages/raw/master/blogImages/image-20250903162130924.png)

###    YOLOv8 Colab 训练（定期保存权重）

```shell
# =========================================================
# 1. 安装 YOLOv8
# =========================================================
!pip install ultralytics

# =========================================================
# 2. 导入库
# =========================================================
from ultralytics import YOLO
from google.colab import files
import os, shutil

# =========================================================
# 3. 上传并自动解压数据集
# =========================================================
uploaded = files.upload()
zip_name = list(uploaded.keys())[0]

!rm -rf datasets/mydata
!mkdir -p datasets/mydata
!unzip -q "$zip_name" -d datasets/mydata

# =========================================================
# 4. 自动查找 dataset.yaml
# =========================================================
yaml_path = ""
for root, dirs, files_list in os.walk("datasets/mydata"):
    for f in files_list:
        if f.endswith(".yaml"):
            yaml_path = os.path.join(root, f)
            break
if yaml_path == "":
    raise FileNotFoundError("❌ 没找到 dataset.yaml，请检查数据集结构！")
print("✅ 找到数据集配置文件:", yaml_path)

# =========================================================
# 5. 开始训练（每隔5个epoch保存一次）
# ---------------------------------------------------------
# save_period=5 表示每 5 epoch 保存一次权重
# =========================================================
model = YOLO("yolov8n.pt")
model.train(
    data=yaml_path,
    epochs=50,
    imgsz=640,
    batch=16,
    save_period=5   # ✅ 新增参数：每5个epoch保存一次
)

# =========================================================
# 6. 下载最后的best.pt（你也可以手动下 5,10,15,...pt）
# =========================================================
best_model_path = "runs/detect/train/weights/best.pt"
files.download(best_model_path)
```

### 📂 保存结果

运行完后，在 Colab 的目录里会有：

```
runs/detect/train/weights/
 ├── best.pt         # 最优模型
 ├── last.pt         # 最后一轮模型
 ├── epoch5.pt
 ├── epoch10.pt
 ├── epoch15.pt
 └── ...
```

你可以提前下载 `epoch5.pt`、`epoch10.pt` 来测试，避免等太久。

### YOLOv8 支持 **断点续训**（继续训练）

只要你用之前的权重文件（`best.pt` / `last.pt` / `epochXX.pt`）作为起点，就能接着往下训练。

🔑 原理

- 如果你不指定 `weights`，默认会从头用 `yolov8n.pt` 预训练权重开始。
- 如果你指定 `weights="runs/detect/train/weights/last.pt"`，它会继续在上次的参数基础上训练。

 续训方法（Colab 示例）

```shell
from ultralytics import YOLO

# 加载上次的训练权重（例如 last.pt 或 best.pt）
model = YOLO("runs/detect/train/weights/last.pt")

# 继续训练 20 个 epoch
model.train(
    data="datasets/mydata/dataset.yaml",
    epochs=20,
    imgsz=640,
    batch=16,
    resume=True   # ✅ 关键参数：表示续训，而不是从头
)
```

`resume=True`：表示在 **保留优化器参数（学习率、动量等）** 的情况下继续训练。

如果你只是想基于权重重新训练（相当于“迁移学习”），可以用：

```
model = YOLO("runs/detect/train/weights/best.pt")
model.train(data="datasets/mydata/dataset.yaml", epochs=20, imgsz=640, batch=16)
```

这种情况会重设优化器，但保留模型参数。

# 标记数据工具

## labelImg

**安装**

```python
pip3 install labelImg
```

**启动**

```shell
C:\Users\铺先生技术研发中心>labelImg
```

#  数据集收集

> 蚊子 https://datasetninja.com/mosquito-alert-2023#download