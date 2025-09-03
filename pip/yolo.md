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

> [down](https://universe.roboflow.com/laptrinhcsc-gvk8t/mask-9xaf0/dataset/1)

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