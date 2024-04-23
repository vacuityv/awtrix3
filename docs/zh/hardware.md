# DIY 硬件

如果你想制作自己的 AWTRIX 3，以下是 Ulanzi 时钟的引脚布局
  

|ESP32 PIN | GPIO  | Usage or part                          |
|---|-------|-----------------------------------------------|
|6  | ADC6 / GPIO34    | Battery sensor (optional)                     |
|7  | ADC7 / GPIO35   | LDR (light) sensor (GL5516) (optional)          |
|8  | GPIO32    | Matrix                                      |
|11 | GPIO26    | Left button (optional)                               |
|12 | GPIO27    | Middle button (optional)                             |
|13 | GPIO14    | Right button  (optional)                              |
|23 | GPIO15    | Buzzer  (optional)                                    |
|33/36| 21 (SCL) /22(SDA)  | Temperature and Humidity Sensors (optional)     |
|37/30| 23(RX)/18(TX) | DFplayer (optional)     |

支持的传感器:
BME280
BMP280
HTU21df
SHT31


如果显示了无意义的字符，必须更改matrix类型：

在文件管理器中创建一个 dev.json 文件并写入以下内容:

```json
{
  "matrix": 2
}
```

更改matrix的值为0，1或者2
