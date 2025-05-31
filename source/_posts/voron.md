---
title: "voron组装与调试"
highlight_shrink: false
tags:
  - voron
categories: voron
description: 添加大量外挂标签样式。
top_img: "https://pixpro.coul.top/i/2025/04/22/609208.webp"
cover: "https://pixpro.coul.top/i/2025/04/22/609208.webp"
swiper_index: 6
abbrlink: voron

date: 2025-4-21 15:55:44
comments:
copyright: true
copyright_author: 
copyright_author_href: 
copyright_url: 
katex:
ai: 
---


# Voron 组装与调试指南

## 一、材料准备

### （一）硬件材料

  1. **Voron 套件**
     * 主框架：铝型材构成的坚固框架。
     * 床体：玻璃床板或碳纤维床板等。
     * 热端：加热块、喷嘴、热敏电阻等。
     * 冷端：散热器和风扇。
     * 加热床：提供加热平台。
     * 进丝系统：进丝电机、皮带轮、轴承等。
     * 风扇系统：层冷却风扇。
     * 电气系统：电源、控制板、线缆、连接器等。

  2. **工具**
     * 螺丝刀套装、扳手、游标卡尺、水平仪、胶带、热胶枪（可选）。

### （二）软件准备

  1. **3D 打印软件**
     * 切片软件：Cura、PrusaSlicer 等。
     * 打印机主机软件（可选）：OctoPrint。

  2. **调试软件**
     * 串口终端软件：Serial。

## 二、组装过程

### （一）框架组装

  1. **安装主框架铝型材**
     * 按设计图纸拼接铝型材成主框架，用螺丝和角件连接。

  2. **安装床体和加热床**
     * 固定加热床到床体上，连接电极引线。
     * 安装床体到主框架上，通过滑轨或轴承连接。

  3. **安装热端和冷端**
     * 安装热端组件到打印头安装板上，连接热敏电阻和加热块电极。
     * 安装冷端散热器和风扇，连接风扇电源线。

  4. **安装进丝系统**
     * 安装进丝电机到电机座上，安装皮带轮到电机轴上。
     * 连接 filament 皮带，安装轴承和导向部件。

  5. **安装风扇系统（层冷风扇）**
     * 安装层冷风扇到打印头附近，调整风扇角度和位置。
     * 连接风扇电源线。

### （二）电气系统安装

  1. **安装电源**
     * 固定电源到主框架，连接输入线和输出线到控制板。

  2. **安装控制板**
     * 固定控制板到框架，连接各部件连接线到控制板接口。

  3. **布线**
     * 整理和固定线缆，避免干涉。

### （三）其他部件安装

  1. **安装保护罩和外壳（可选）**
     * 固定保护罩和外壳到主框架上。

## 三、调试过程

### （一）电源和控制系统调试

  1. **检查连接**
     * 检查电气连接是否牢固。

  2. **初次通电**
     * 接通电源，观察电源指示灯。

  3. **测试控制系统**
     * 使用串口终端软件连接控制板，发送命令测试。

### （二）机械部件调试

  1. **测试床体运动**
     * 发送 G - code 命令测试床体升降。

  2. **测试打印头运动**
     * 发送 G - code 命令测试打印头在 X、Y 轴运动。

  3. **测试进丝系统**
     * 发送命令测试进丝是否顺畅。

### （三）温度调试

  1. **设置热端温度**
     * 发送命令加热热端，观察温度是否稳定。

  2. **设置加热床温度**
     * 发送命令加热床体，检查温度是否均匀。

### （四）打印调试

  1. **校准打印尺寸**
     * 打印校准模型，测量尺寸偏差，调整参数和机械部件。

  2. **优化打印参数**
     * 调整打印速度、冷却风扇转速、支撑结构等参数。

  3. **监控打印过程**
     * 使用软件或观察打印机运行情况，监控打印状态。

## 四、常见问题及解决方法

### （一）打印不粘床

  1. **原因**
     * 床体温度设置不当。
     * 打印材料表面处理不当。
     * 打印头高度不合适。

  2. **解决方法**
     * 调整床体温度。
     * 清洁床体表面。
     * 校准打印头高度。

### （二）打印层错位

  1. **原因**
     * 机械部件松动。
     * 皮带张紧度不合适。
     * 电机电流不足。

  2. **解决方法**
     * 检查并拧紧螺丝。
     * 调整皮带张紧度。
     * 调整电机电流。

### （三）堵塞问题

  1. **原因**
     * filament 质量问题。
     * 热端温度设置不当。
     * 进丝系统问题。

  2. **解决方法**
     * 检查 filament 质量。
     * 调整热端温度。
     * 检查和维护进丝系统。



## 步进电机检查
要验证每个步进电机是否正常工作，请在终端中发送以下命令：
```bash
STEPPER_BUZZ STEPPER=stepper_x
# STEPPER_BUZZ 命令将使指定的步进电机向正方向移动一毫米，然后返回起始位置。它将进行十次这样的振荡。我们将在稍后再次验证方向，理想情况下，所有电机在测试结束时都将正常运行。请参见下面的列表，以了解每个命令的预期运动。
```
**注意，如果您难以判断电机的旋转方向，请在滑轮上添加一个小标记。顺时针和逆时针是从上往下看 X 轴和 Y 轴电机时的方向。**
以下是如何针对不同型号的 Voron 3D 打印机测试各电机运动的步骤：

核心原理
使用 Klipper 固件的 STEPPER_BUZZ 命令，默认会让电机先正向移动一小段距离，再反向返回原点，用于快速验证电机接线和方向是否正常。
# Voron 系列 3D 打印机电机测试指南

通过 Klipper 的 `STEPPER_BUZZ` 命令验证电机方向和运动逻辑。

---

## 测试命令与期望动作

### 1. Voron 0
```bash
STEPPER_BUZZ STEPPER=stepper_x   # 顺时针→逆时针（X轴）
STEPPER_BUZZ STEPPER=stepper_y   # 顺时针→逆时针（Y轴）
STEPPER_BUZZ STEPPER=stepper_z   # 床先下降→上升（Z轴）
STEPPER_BUZZ STEPPER=extruder    # 仅测试转动（方向后续校准）
```

### 2. Voron 1 (Legacy)
```bash
STEPPER_BUZZ STEPPER=stepper_x   # 顺时针→逆时针（X轴）
STEPPER_BUZZ STEPPER=stepper_y   # 顺时针→逆时针（Y轴）
STEPPER_BUZZ STEPPER=stepper_z   # 左侧床下降→上升
STEPPER_BUZZ STEPPER=stepper_z1  # 右侧床下降→上升
STEPPER_BUZZ STEPPER=extruder    # 仅测试转动
```

### 3. Trident
```bash
STEPPER_BUZZ STEPPER=stepper_x   # 顺时针→逆时针（X轴）
STEPPER_BUZZ STEPPER=stepper_y   # 顺时针→逆时针（Y轴）
STEPPER_BUZZ STEPPER=stepper_z   # 前左侧床角下降→上升
STEPPER_BUZZ STEPPER=stepper_z1  # 后侧床角下降→上升
STEPPER_BUZZ STEPPER=stepper_z2  # 前右侧床角下降→上升
STEPPER_BUZZ STEPPER=extruder    # 仅测试转动
```

### 4. Voron V2
```bash
STEPPER_BUZZ STEPPER=stepper_x   # 顺时针→逆时针（X轴）
STEPPER_BUZZ STEPPER=stepper_y   # 顺时针→逆时针（Y轴）
STEPPER_BUZZ STEPPER=stepper_z   # 前左龙门架上升→下降
STEPPER_BUZZ STEPPER=stepper_z1  # 后左龙门架上升→下降
STEPPER_BUZZ STEPPER=stepper_z2  # 后右龙门架上升→下降
STEPPER_BUZZ STEPPER=stepper_z3  # 前右龙门架上升→下降
STEPPER_BUZZ STEPPER=extruder    # 仅测试转动
```

### 5. Switchwire
```bash
STEPPER_BUZZ STEPPER=stepper_x   # 逆时针→顺时针（X轴）
STEPPER_BUZZ STEPPER=stepper_y   # 床前移→后移（Y轴）
STEPPER_BUZZ STEPPER=stepper_z   # 逆时针→顺时针（Z轴）
STEPPER_BUZZ STEPPER=extruder    # 仅测试转动
```

注意事项
安全准备

✅ 确保电机通电，机械结构无碰撞风险

🔄 若已归位，建议禁用软限位：M211 S0

方向修正

若方向相反，修改 printer.cfg 中对应电机的 dir_pin（例如添加 ! 反转信号）：

```ini
[stepper_x]
dir_pin: !PB5  # 添加 ! 符号反转方向
```
**如果您发现电机不工作，请检查连接和电源。如果一切正常，请检查您的配置文件中的步进电机设置。**