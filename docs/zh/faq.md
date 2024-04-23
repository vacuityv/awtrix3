# 常见问题解答 (FAQ)

欢迎来到常见问题解答部分。在这里，你将找到我收到的一些最常见问题的答案。如果 你没有找到想要的信息，请不要犹豫，加入[discord server](https://discord.gg/cyBCpdx)询问。

### 目录
- [常见问题](#general-questions)
  - [我可以独立运行 AWTRIX 3 吗？](#q-can-i-run-awtrix3-standalone)
  - [我可以使用除了 8x32 之外的其他LED灯尺寸吗？](#q-can-i-use-different-matrix-sizes-other-than-8x32)
  - [在给我的 Ulanzi 时钟刷写固件时出现错误](#q-why-am-i-getting-an-error-while-flashing-my-ulanzi-clock-with-the-awtrix-web-flasher)
  - [不小心更改了 DoNotTouch.json](#q-what-should-i-do-if-i-accidentally-touched-the-donottouchjson-file-in-awtrix-web-file-manager)
  - [自建的 AWTRIX 显示无意义的字符](#q-my-self-built-awtrix-device-is-displaying-meaningless-characters-on-the-matrix-what-should-i-do)
  - [构建自己的 AWTRIX 应该使用哪个固件？](#q-i-want-to-build-my-own-awtrix-which-firmware-should-i-use)
  - [Ulanzi TC001 温度传感器报了高温](#q-why-does-the-ulanzi-tc001-temperature-sensor-report-a-high-temperature)
  - [左上角或左下角的 LED 闪烁](#q-i-have-a-blinking-led-on-the-top-left--bottom-left-corner-what-does-it-mean)


### 常见问题
#### Q: 我可以独立运行 AWTRIX 3 吗？
A: 不可以，AWTRIX 是作为您智能家居系统的配件而设计的。它只能显示通过API发送的信息。

#### Q: 我可以使用除了 8x32 之外的其他LED灯尺寸吗？
A: 目前 AWTRIX 仅对 Ulanzi Pixelclock 进行了优化，该时钟仅支持 32x8 像素的LED灯大小。目前不支持其他尺寸。

#### Q: 为什么我在使用 AWTRIX Web Flasher 给我的 Ulanzi 时钟刷新固件时出现错误？
A: 如果在刷固件过程中遇到错误，我建议您尝试使用不同的 USB 线和 USB 端口。一些用户在使用设备原厂数据线刷固件时出现了问题。

#### Q: 如果我不小心在 AWTRIX 网页文件管理器中更改了 DoNotTouch.json 文件，我该怎么办？
A: `DoNotTouch.json` 文件包含了以下设置:

- 静态 IP 配置
- MQTT 配置
- Homeassistant 发现
- NTP 服务器 / 时区
- HTTP 授权密码

如果您不小心修改了这个文件，您应该在文件管理器中将其删除，并重新启动您的 AWTRIX 设备。该文件将会自动重新创建，重新创建后你需要重新配置上述的设置。

#### Q: 我的自制 AWTRIX 显示无意义的字符。我该怎么办？
A: 如果显示了无意义的字符，需要更改matrix类型。

用文件管理器在根目录下创建一个名字为`dev.json`的文件. matrix类型有三个可选值:
- 0
- 1
- 2
> 默认值是 0, 所以你可以试试 1 或者 2

`dev.json` 文件内容示例：
```json
{
  "matrix": "2"
}
```

更改后重启设备

#### Q: 我想构建自己的 AWTRIX，应该使用哪个固件？
A: 请根据你自己实际情况选择以下适合的固件：

#### 固件1: [Ulanzi TC001 and Custom Builds Flasher](https://blueforcer.github.io/awtrix3/#/flasher?id=ulanzi-tc001-and-custom-builds-flasher)
- **固件兼容性**: 该固件与Ulanzi TC001和使用ESP32-WROOM板的定制AWTRIX设备兼容，包括ESP32 D1 Mini。
- **引脚排列指南**: 请确保您按照特定的引脚排列来进行自定义构建，以确保该固件能够正确工作。引脚排列指南可在以下位置找到：: [AWTRIX 3 硬件指南](https://blueforcer.github.io/awtrix3/#/hardware)


#### 固件2: [Awtrix 2.0 Controller Upgrade (with ESP32 D1 Mini)](https://blueforcer.github.io/awtrix3/#/flasher?id=awtrix-20-controller-upgrade-with-esp32-d1-mini)
- **固件用途**: 该固件专门设计用于升级旧的AWTRIX 2.0。原来的AWTRIX 2.0是用Wemos D1 mini (ESP8266)构建的，AWTRIX 3不支持此设备。
- **升级要求**: 为了升级，需要将ESP8266更换为ESP32 D1 Mini。ESP32 D1 Mini有相同的外形尺寸，使其能够直接替换主板上的旧模块。
- **引脚兼容性**: ESP32 D1 Mini 和旧的 AWTRIX 2.0 使用相同的引脚.
- **构建信息**: 可以访问这里获取更多信息: [AWTRIX 2.0 构建信息](https://awtrixdocs.blueforcer.de/#/en-en/awtrix_family?id=parts-list)

#### Q: 为什么 Ulanzi TC001 温度传感器报了高温？
A: 温度传感器测量的是外壳内部的温度，对于外部温度的测量并不是很有用。
内部组件比如点阵（取决于亮度和开启的LED数量）和电池产生的热量会影响温度测量。

您可以在dev.json文件中调整温度和湿度偏移设置，该文件可以在[AWTRIX 3 开发者设置](https://blueforcer.github.io/awtrix3/#/dev)页面找到。这些设置的配置取决于您的具体需求。

用文件管理器在根目录下创建一个`dev.json`文件，内容如下：

*dev.json 文件内容示例*
```json
{
  "temp_offset": -5,
  "hum_offset": -1
}
```

重启设备

#### Q: 左上角或左下角的 LED 闪烁，是什么意思?
A: 在AWTRIX固件中，有2个LED状态表示不同的问题：

- 位于左上角的闪烁LED表示连接WiFi时出现问题。
- 位于左下角的闪烁LED表示连接到您的MQTT时出现问题。

