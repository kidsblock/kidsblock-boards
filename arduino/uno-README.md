# Arduino UNO 开发板

## 基本信息

- **名称**：UNO 开发板
- **制造商**：keyestudio
- **芯片**：ATmega328P
- **工作频率**：16MHz
- **工作电压**：5V
- **闪存**：32KB
- **SRAM**：2KB
- **EEPROM**：1KB

## 产品描述

经典的 Arduino 入门开发板，拥有 14 个数字引脚和 6 个模拟输入，非常适合初学者学习电子编程。

## 引脚配置

### 数字引脚
- 数字引脚：D0-D13（共 14 个）
- PWM 引脚：D3, D5, D6, D9, D10, D11
- 中断引脚：D2, D3

### 模拟引脚
- 模拟输入：A0-A5（共 6 个）

### 通信接口
- **I2C**：SDA (A4/D18), SCL (A5/D19)
- **SPI**：MOSI (D11), MISO (D12), SCK (D13), SS (D10)
- **UART**：RX (D0), TX (D1)

### 内置 LED
- 引脚 D13 连接内置 LED

## USB 设备 ID

| Vendor ID | Product ID | 说明 |
|-----------|------------|------|
| 2341      | 0043       | Arduino 官方 |
| 2341      | 0001       | Arduino 官方（旧版） |
| 2A03      | 0043       | Arduino 兼容板 |
| 1A86      | 7523       | CH340 串口芯片 |

## 编程配置

- **FQBN**：arduino:avr:uno
- **波特率**：115200
- **上传波特率**：115200
- **支持语言**：C++（Arduino）

## 安装要求

### 核心库
- **包名**：arduino:avr
- **版本**：1.8.6
- **大小**：5.0 MB

### 工具链
1. **avr-gcc**
   - 版本：7.3.0-atmel3.6.1-arduino7
   - 大小：34-52 MB（根据平台）

2. **avrdude**
   - 版本：6.3.0-arduino17
   - 大小：0.5-0.6 MB（根据平台）

### 推荐库
- Servo (1.2.0) - 舵机控制库

## 使用方法

### 在 KidsBlock 中使用

1. 打开 KidsBlock
2. 点击"选择硬件"
3. 选择"Arduino UNO 开发板"
4. 系统会自动下载所需的核心库和工具链
5. 连接开发板到电脑
6. 开始编程和上传代码

### 手动安装（高级用户）

```bash
# 安装 Arduino CLI
# 参考：https://arduino.github.io/arduino-cli/

# 安装核心库
arduino-cli core install arduino:avr@1.8.6

# 安装推荐库
arduino-cli lib install Servo@1.2.0

# 编译示例代码
arduino-cli compile --fqbn arduino:avr:uno sketch.ino

# 上传代码
arduino-cli upload -p /dev/ttyUSB0 --fqbn arduino:avr:uno sketch.ino
```

## 相关链接

- [官方 Wiki](https://wiki.keyestudio.com/Ks0001_keyestudio_UNO_R3_BOARD)
- [Arduino 官方文档](https://www.arduino.cc/en/Main/ArduinoBoardUno)
- [ATmega328P 数据手册](https://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf)

## 常见问题

### Q: 上传代码时提示"端口被占用"？
A: 确保没有其他程序（如串口监视器）正在使用该端口。

### Q: 无法识别开发板？
A: 检查 USB 线是否正常，尝试更换 USB 端口，或安装 CH340 驱动程序。

### Q: 代码上传失败？
A: 检查开发板型号是否选择正确，确认 FQBN 为 `arduino:avr:uno`。

---

**版本**：1.0.0  
**最后更新**：2026-01-28
