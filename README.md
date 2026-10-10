# CH32V307EVT 载板式 IO Hub

为 WCH CH32V307VCT6-R1 评估板设计的载板式 IO Hub。它通过开发板的 J3/J4 排针，将常用外设整理为 GH1.25 接口，便于像飞控一样连接传感器、数传、CAN 节点和执行器。

## 第一版接口规划

| 接口 | GH1.25 | MCU 引脚 |
| --- | --- | --- |
| UART1 | 4P | PA9 TX, PA10 RX |
| UART2 | 4P | PA2 TX, PA3 RX |
| I2C1 | 4P | PB8 SCL, PB9 SDA |
| I2C2 | 4P | PB10 SCL, PB11 SDA |
| CAN1 | 4P | PD0 RX, PD1 TX, 外接 CAN 收发器 |
| SPI1 | 6P | PA4 NSS, PA5 SCK, PA6 MISO, PA7 MOSI |
| PWM | 6P | PD12, PD13, PD14, PD15 |
| ADC1 / ADC2 | 3P x 2 | PA0, PA1 |
| GPIO | 6P | PE8, PE9, PE10, PE11 |

详见 [接口和引脚分配](docs/io-pin-plan.md)。

## 重要限制

- GPIO 电平为 3.3 V。不得将 5 V 直接接到 MCU 信号脚。
- CANH/CANL 必须经过 CAN 收发器，不能直接连接 PD0/PD1。
- PWM 接口的舵机电源应来自外部 BEC；不能依赖开发板 USB 5 V。
- PA13/PA14、PA11/PA12、PB6/PB7、PC6-PC9 预留给板载调试、USB 和以太网功能。

## 目录

- `hardware/reference/`：原始 CH32V307VCT6-R1 原理图 PDF。
- `docs/`：接口定义与引脚分配。

硬件原理图与 PCB 文件将在后续加入。
