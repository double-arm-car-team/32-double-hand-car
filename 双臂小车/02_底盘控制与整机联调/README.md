# 02｜底盘控制与整机联调

**负责人：haimichenha**

本模块是 STM32 底盘、四轮/麦轮驱动、总线舵机、蓝牙遥控和 Nano 串口联调的工程入口。固件源码保留在仓库根目录，以维持 Keil 工程的相对路径。

## 固件入口与相关模块

| 位置 | 用途 |
| --- | --- |
| [Src/main_bluetooth_car_arm.c](../../Src/main_bluetooth_car_arm.c) | 双臂小车蓝牙控制与总线舵机动作组入口；文件头注明蓝牙 USART3 与总线舵机 UART4 的测试配置。 |
| [Hardware/app_bluetooth_motor_test.c](../../Hardware/app_bluetooth_motor_test.c) | 蓝牙电机控制逻辑。 |
| [Hardware/app_servo_test.c](../../Hardware/app_servo_test.c) | 总线舵机动作与命令处理。 |
| [Hardware/app_nano_uart_test.c](../../Hardware/app_nano_uart_test.c) | STM32 与 Nano 的 UART 联调接口。 |
| [硬件接口与引脚台账](../docs/硬件接口与引脚台账.md) | 引脚、串口与模式冲突的记录。 |

不同 `main_*.c` 对应不同测试目标；编译或烧录前只选择一个入口，并检查其外设初始化与当前接线一致。

## 硬件与验收资料

| 文件 | 说明 |
| --- | --- |
| [小车 PCB 原理图展示](hardware/小车pcb原理图展示.pdf) | 已归档的 PCB 原理图展示；具体接线仍以实物和选定固件入口为准。 |
| [四电机测试照片](evidence/小车四电机测试第一.jpeg) | 驱动器、电机和线束已接入测试工装的阶段记录。 |
| [整车接线完成照片](evidence/小车接线完成第二.jpeg) | 整车主要接线完成后的联调状态。 |
| [教师验收视频](evidence/小车验收视频.mp4) | 540×960、30 fps、约 41.63 s 的教师验收实物记录。 |

照片和视频用于记录阶段状态；四轮方向、闭环质量、成功率和精度等结论仍需对应测试日志或验收判据。
