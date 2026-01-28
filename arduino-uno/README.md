# Arduino Uno

Arduino Uno 是最受欢迎的 Arduino 开发板，基于 ATmega328P 微控制器。它拥有 14 个数字输入/输出引脚（其中 6 个可用作 PWM 输出）、6 个模拟输入、一个 16 MHz 石英晶体、一个 USB 连接、一个电源插孔、一个 ICSP 接头和一个复位按钮。

## 技术规格

| 参数 | 值 |
|------|-----|
| 微控制器 | ATmega328P |
| 工作电压 | 5V |
| 输入电压（推荐） | 7-12V |
| 输入电压（极限） | 6-20V |
| 数字 I/O 引脚 | 14 个（其中 6 个 PWM 输出） |
| PWM 数字 I/O 引脚 | 6 个 |
| 模拟输入引脚 | 6 个 |
| 每个 I/O 引脚的直流电流 | 20 mA |
| 3.3V 引脚的直流电流 | 50 mA |
| Flash 存储器 | 32 KB（其中 0.5 KB 用于引导加载程序） |
| SRAM | 2 KB |
| EEPROM | 1 KB |
| 时钟速度 | 16 MHz |
| LED_BUILTIN | 13 |
| 长度 | 68.6 mm |
| 宽度 | 53.4 mm |
| 重量 | 25 g |

## 引脚说明

### 数字引脚

- **D0-D1**：串口通信引脚（RX/TX）
- **D2-D13**：数字输入/输出引脚
- **D3, D5, D6, D9, D10, D11**：支持 PWM 输出（~标记）

### 模拟引脚

- **A0-A5**：模拟输入引脚，可读取 0-5V 的电压值

### 电源引脚

- **5V**：5V 电源输出
- **3.3V**：3.3V 电源输出
- **GND**：地线
- **VIN**：外部电源输入（7-12V）

### 通信接口

- **Serial (UART)**：D0 (RX) 和 D1 (TX)
- **I2C (TWI)**：A4 (SDA) 和 A5 (SCL)
- **SPI**：D10 (SS), D11 (MOSI), D12 (MISO), D13 (SCK)

## 使用示例

### 点亮 LED

```cpp
void setup() {
  pinMode(13, OUTPUT);
}

void loop() {
  digitalWrite(13, HIGH);
  delay(1000);
  digitalWrite(13, LOW);
  delay(1000);
}
```

### 读取模拟输入

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(A0);
  Serial.println(sensorValue);
  delay(100);
}
```

### 控制舵机

```cpp
#include <Servo.h>

Servo myservo;

void setup() {
  myservo.attach(9);
}

void loop() {
  myservo.write(0);
  delay(1000);
  myservo.write(90);
  delay(1000);
  myservo.write(180);
  delay(1000);
}
```

## 常见问题

### Q: 如何给 Arduino Uno 供电？

A: 有三种方式：
1. 通过 USB 线连接电脑（5V）
2. 通过 DC 电源插孔（7-12V 推荐）
3. 通过 VIN 引脚（7-12V 推荐）

### Q: 为什么上传代码时出现错误？

A: 请检查：
1. 是否选择了正确的开发板和端口
2. USB 线是否连接正常
3. 是否安装了正确的驱动程序
4. D0 和 D1 引脚是否被占用（这两个引脚用于串口通信）

### Q: 如何使用外部中断？

A: Arduino Uno 有两个外部中断引脚：
- D2 (INT0)
- D3 (INT1)

使用 `attachInterrupt()` 函数来设置中断处理函数。

### Q: PWM 输出的频率是多少？

A: Arduino Uno 的 PWM 频率约为 490 Hz（D3 和 D11 约为 980 Hz）。

## 参考资料

- [Arduino 官方文档](https://www.arduino.cc/en/Main/ArduinoBoardUno)
- [ATmega328P 数据手册](https://ww1.microchip.com/downloads/en/DeviceDoc/Atmel-7810-Automotive-Microcontrollers-ATmega328P_Datasheet.pdf)
- [Arduino 语言参考](https://www.arduino.cc/reference/en/)

## 许可证

MIT License
