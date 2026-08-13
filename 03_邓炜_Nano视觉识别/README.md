# 03｜邓炜｜Nano 视觉识别与模型训练

**负责人：邓炜（邓处）——Nano 视觉识别与模型训练**；**帧率优化联调：haimichenha**

本模块保存邓炜完成的 Nano 视觉识别、模型训练相关代码入口和阶段截图。检测工程位于本模块的 `yolov5/`；其中 YOLOv5 上游基础代码、许可证和第三方文件必须保留其原有来源说明，团队提交应明确区分训练产生的模型/配置、自研脚本和上游文件。

## 代码入口

| 位置 | 用途 |
| --- | --- |
| [yolov5/detect_ultra.py](yolov5/detect_ultra.py) | **本项目保留的 FP32 检测入口**：加载 `yolov5n_fp32_320.engine`，以 320×320 输入完成检测与显示。 |
| [yolov5/nano_uart_link_test.py](yolov5/nano_uart_link_test.py) | Nano/Jetson 与 STM32 的 UART5 PING、ECHO、VISION 联调脚本。 |
| [yolov5/train.py](yolov5/train.py) | YOLOv5 模型训练入口；训练参数、数据集与结果应随实验记录保存。 |
| [yolov5/my.yaml](yolov5/my.yaml) | 本地数据/类别配置。 |

## 本项目运行配置

- **确认使用：**YOLOv5 + TensorRT FP32 检测链路；对应保留入口为 `detect_ultra.py`。
- **模型与输入：**`yolov5n_fp32_320.engine`，320×320；脚本中输入、输出主机缓冲区均为 `float32`。
- **保留边界：**目录中同时存有 FP16 引擎和试验脚本，例如 `detect_fast.py`。它们是阶段性对比材料，**不是本项目最终运行配置**，不得据此把项目写成 FP16 或混合精度部署。
- [运行配置与证据说明](运行配置与证据说明.md)记录代码依据、性能结论的取证条件和后续补充方式。

## 阶段性视觉证据

| 文件 | 画面信息 | 证据边界 |
| --- | --- | --- |
| [Nano 检测截图](evidence/nano视觉.jpg) | 画面中有两个目标框，显示 `object 0.85`、`object 0.90`。 | 支持一次检测界面输出；不等于完整数据集指标。 |
| [小车地面站显示](evidence/小车地面站显示.jpeg) | 整机测试环境中的视觉画面、目标框和 FPS 显示。 | FPS 仅为该时刻界面值，性能结论需附运行命令、模型、分辨率和日志。 |
