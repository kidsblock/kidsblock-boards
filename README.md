# KidsBlock Boards

开发板配置和引脚定义仓库，为 KidsBlock 提供所有支持的开发板配置。

## 📋 仓库说明

本仓库存储所有开发板的硬件配置、引脚定义、产品图片和安装配置。每个开发板一个独立目录，包含完整的配置文件和元数据。

## 📁 目录结构

```
kidsblock-boards/
├── README.md                    # 本文件
├── LICENSE                      # MIT 许可证
├── arduino/                     # Arduino 系列开发板
│   ├── uno-board.json          # UNO 开发板配置
│   ├── uno-pins.json           # UNO 引脚定义
│   ├── uno-install.json        # UNO 安装配置
│   ├── uno-README.md           # UNO 使用说明
│   ├── arduino-uno.jpg         # UNO 产品图片
│   ├── mega-board.json
│   ├── nano-board.json
│   └── leonardo-board.json
├── esp32/                       # ESP32 系列开发板
│   ├── esp32-board.json
│   ├── esp32-pins.json
│   ├── esp32-install.json
│   └── esp32.jpg
├── esp8266/                     # ESP8266 系列开发板
│   ├── esp8266-board.json
│   └── esp8266.jpg
├── microbit/                    # Micro:bit 系列
│   ├── microbit-v2-board.json
│   └── microbit-v1-board.json
└── pico/                        # Raspberry Pi Pico 系列
    ├── pico-board.json
    └── pico-w-board.json
```

## 🎯 支持的开发板

### Arduino 系列
- **Arduino UNO** - 经典入门开发板（ATmega328P）
- **Arduino Mega 2560** - 大型项目开发板（ATmega2560）
- **Arduino Nano** - 小型开发板（ATmega328P）
- **Arduino Leonardo** - USB 原生支持（ATmega32U4）

### ESP32 系列
- **ESP32 Dev** - WiFi + 蓝牙开发板
- **ESP32-S3** - 新一代 ESP32 开发板

### ESP8266 系列
- **ESP8266** - WiFi 开发板

### Micro:bit 系列
- **Micro:bit V2** - BBC Micro:bit 第二代
- **Micro:bit V1** - BBC Micro:bit 第一代

### Raspberry Pi Pico 系列
- **Raspberry Pi Pico** - RP2040 开发板
- **Raspberry Pi Pico W** - 带 WiFi 的 RP2040 开发板

## 📝 配置文件说明

每个开发板目录包含以下文件：

### 1. `{board}-board.json` - 开发板基本信息

```json
{
  "id": "arduino-uno",
  "name": "UNO 开发板",
  "manufacturer": "keyestudio",
  "description": "经典的 Arduino 入门开发板",
  "chip": "ATmega328P",
  "frequency": "16MHz",
  "voltage": "5V",
  "fqbn": "arduino:avr:uno",
  "usb": {
    "ids": [
      { "vendorId": "2341", "productId": "0043" }
    ]
  },
  "baudRate": 115200,
  "programming": {
    "languages": ["C++"],
    "modes": ["upload"]
  },
  "image": "arduino-uno.jpg",
  "helpUrl": "https://wiki.keyestudio.com/...",
  "tags": ["arduino", "beginner", "popular"]
}
```

### 2. `{board}-pins.json` - 引脚定义

```json
{
  "digital": [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13],
  "analog": ["A0", "A1", "A2", "A3", "A4", "A5"],
  "pwm": [3, 5, 6, 9, 10, 11],
  "interrupt": [2, 3],
  "i2c": { "sda": 18, "scl": 19 },
  "spi": { "mosi": 11, "miso": 12, "sck": 13, "ss": 10 },
  "serial": { "rx": 0, "tx": 1 },
  "builtin_led": 13
}
```

### 3. `{board}-install.json` - 安装配置

```json
{
  "core": {
    "package": "arduino:avr",
    "version": "1.8.6",
    "downloadUrl": "https://downloads.arduino.cc/cores/avr-1.8.6.tar.bz2",
    "size": "5.0 MB"
  },
  "tools": [
    {
      "name": "avr-gcc",
      "version": "7.3.0-atmel3.6.1-arduino7",
      "platforms": {
        "windows-x64": { "url": "...", "size": "52 MB" },
        "macos-x64": { "url": "...", "size": "35 MB" },
        "linux-x64": { "url": "...", "size": "34 MB" }
      }
    }
  ],
  "libraries": [
    { "name": "Servo", "version": "1.2.0" }
  ]
}
```

### 4. `{board}-README.md` - 使用说明

详细的开发板使用文档，包括引脚配置、编程方法、常见问题等。

### 5. `{board}.jpg` - 产品图片

开发板的高清产品图片，用于在 KidsBlock 界面中显示。

## 🚀 使用方法

### 在 KidsBlock 中使用

1. 用户在 KidsBlock 中选择开发板
2. KidsBlock 从本仓库下载对应的配置文件
3. 解析 `install.json` 获取需要下载的核心库和工具链
4. 调用 Arduino CLI 或直接下载资源到本地缓存
5. 更新工具箱显示对应的引脚积木

### 通过 CDN 访问

使用 jsDelivr CDN 加速访问：

```
https://cdn.jsdelivr.net/gh/your-username/kidsblock-boards@main/arduino/uno-board.json
```

### 直接从 GitHub 访问

```
https://raw.githubusercontent.com/your-username/kidsblock-boards/main/arduino/uno-board.json
```

## 🔧 开发指南

### 添加新开发板

1. 在对应的分类目录下创建配置文件
2. 准备开发板产品图片（推荐尺寸：800x600px）
3. 编写 `board.json`、`pins.json`、`install.json`
4. 编写 `README.md` 使用说明
5. 提交 Pull Request

### 配置文件模板

参考 `arduino/uno-*.json` 作为模板，根据实际开发板修改。

### 图片要求

- 格式：JPG 或 PNG
- 尺寸：推荐 800x600px
- 大小：< 500 KB
- 背景：纯白色或透明

## 📊 仓库统计

| 分类 | 开发板数量 | 总大小 |
|------|-----------|--------|
| Arduino | 4 | ~1.3 MB |
| ESP32 | 2 | ~400 KB |
| ESP8266 | 1 | ~40 KB |
| Micro:bit | 2 | 待添加 |
| Pico | 2 | 待添加 |
| **总计** | **11** | **~2 MB** |

## 🤝 贡献指南

欢迎贡献新的开发板配置！请遵循以下步骤：

1. Fork 本仓库
2. 创建新分支 (`git checkout -b add-new-board`)
3. 添加开发板配置文件
4. 提交更改 (`git commit -m 'Add XXX board configuration'`)
5. 推送到分支 (`git push origin add-new-board`)
6. 创建 Pull Request

## 📄 许可证

本项目采用 MIT 许可证。详见 [LICENSE](LICENSE) 文件。

## 🔗 相关链接

- [KidsBlock 主仓库](https://github.com/your-username/kidsblock)
- [KidsBlock Resource 仓库](https://github.com/your-username/kidsblock-resource)
- [KidsBlock Tools 仓库](https://github.com/your-username/kidsblock-tools)
- [Arduino CLI 文档](https://arduino.github.io/arduino-cli/)

## 📞 联系我们

如有问题或建议，请提交 Issue 或联系我们。

---

**版本**：1.0.0  
**最后更新**：2026-01-28  
**维护者**：KidsBlock Team
