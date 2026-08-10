# 03｜邓炜｜Nano 视觉识别

**负责人：邓炜（邓处）**；**帧率优化联调：haimichenha**

本模块保存 Nano 视觉识别的代码入口和阶段截图。检测工程位于本模块的 `yolov5/`；其中 YOLOv5 上游基础代码、许可证和第三方文件必须保留其原有来源说明，团队提交应明确区分自研配置、模型、脚本和上游文件。

## 代码入口

| 位置 | 用途 |
| --- | --- |
| [yolov5/nano_uart_link_test.py](yolov5/nano_uart_link_test.py) | Nano/Jetson 与 STM32 的 UART5 PING、ECHO、VISION 联调脚本。 |
| [yolov5/detect_fast.py](yolov5/detect_fast.py) | 本地检测流程入口之一。 |
| [yolov5/my.yaml](yolov5/my.yaml) | 本地数据/类别配置。 |

## 阶段性视觉证据

| 文件 | 画面信息 | 证据边界 |
| --- | --- | --- |
| [Nano 检测截图](evidence/nano视觉.jpg) | 画面中有两个目标框，显示 `object 0.85`、`object 0.90`。 | 支持一次检测界面输出；不等于完整数据集指标。 |
| [小车地面站显示](evidence/小车地面站显示.jpeg) | 整机测试环境中的视觉画面、目标框和 FPS 显示。 | FPS 仅为该时刻界面值，性能结论需附运行命令、模型、分辨率和日志。 |
