# IO Hub 接口和引脚分配

开发板连接器编号以 `hardware/reference/SCH_CH32V307VCT6-R1.pdf` 为准。`J3-30` 表示开发板 J3 的第 30 脚。

| 丝印 | GH 引脚定义 | MCU 引脚 | 开发板连接器 | 配置 |
| --- | --- | --- | --- | --- |
| UART1 | 1:GND, 2:+5V, 3:TX, 4:RX | PA9 TX, PA10 RX | J4-35, J4-37 | 默认 USART1 |
| UART2 | 1:GND, 2:+5V, 3:TX, 4:RX | PA2 TX, PA3 RX | J3-30, J3-32 | 默认 USART2 |
| I2C1 | 1:GND, 2:3V3, 3:SCL, 4:SDA | PB8 SCL, PB9 SDA | J4-25, J4-23 | I2C1 重映射 |
| I2C2 | 1:GND, 2:3V3, 3:SCL, 4:SDA | PB10 SCL, PB11 SDA | J4-1, J4-3 | 默认 I2C2 |
| CAN1 | 1:GND, 2:+5V, 3:CANH, 4:CANL | PD0 RX, PD1 TX | J4-39, J4-38 | CAN1 全重映射，外接收发器 |
| SPI1 | 1:GND, 2:3V3, 3:SCK, 4:MISO, 5:MOSI, 6:CS | PA5, PA6, PA7, PA4 | J3-36, J4-29, J4-31, J3-34 | 默认 SPI1 |
| PWM | 1:GND, 2:V_SERVO, 3:PWM1, 4:PWM2, 5:PWM3, 6:PWM4 | PD12, PD13, PD14, PD15 | J4-54, J4-53, J4-52, J4-51 | TIM4 全重映射 |
| ADC1 | 1:GND, 2:3V3, 3:ADC | PA0 | J3-26 | ADC_IN0 |
| ADC2 | 1:GND, 2:3V3, 3:ADC | PA1 | J3-28 | ADC_IN1 |
| GPIO | 1:GND, 2:3V3, 3:GPIO1, 4:GPIO2, 5:GPIO3, 6:GPIO4 | PE8, PE9, PE10, PE11 | J3-43, J3-44, J3-45, J3-46 | 通用扩展 |

## 后续可选扩展

- UART3 和 I2C2 共用 PB10/PB11，应使用 0 欧姆电阻或焊盘跳线二选一。
- UART4：PC10 TX (J4-42)、PC11 RX (J4-41)。
- UART5：PC12 TX (J4-40)、PD2 RX (J4-36)。
- CAN2：PB12 RX (J4-15)、PB13 TX (J4-9)，需独立 CAN 收发器。
- 建议将其余不确定用途 GPIO 以多芯 GH 扩展口引出，而不是每脚单独占用一个插座。

## 电气规则

1. I2C 仅保留一组可选的 4.7 kOhm 上拉到 3V3。
2. CAN 总线末端才接入可选 120 Ohm 终端电阻。
3. UART、I2C、SPI 信号均为 3.3 V 逻辑。
4. 外部执行器使用独立 BEC 为 V_SERVO 供电，并与 Hub 共地。
