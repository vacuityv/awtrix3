如果你想从 Ulanzi TC001 中移除 AWTRIX，你可以烧录回原始固件。
本教程适用于 Windows 平台，但您可以在其他平台的烧录工具中使用该固件。

## 方法1
1. 下载 [原始固件](https://raw.githubusercontent.com/Blueforcer/awtrix3/main/docs/assets/ulanzi_original_firmware.bin)
2. 把你的 Ulanzi 和电脑连接起来，在浏览器打开 https://esp.huhn.me/
3. 点击 Connect -> Erase
4. 上传 .bin 文件然后输入 0x00000。然后点击"program"  
![image](https://github.com/Blueforcer/awtrix3/assets/31169771/b79bdf7e-477e-47f6-a41e-9106519f636b)
  
  
  
## 方法2 (仅适用于Windows) 
1. 下载 [ESP32 download tool](https://www.espressif.com/en/support/download/other-tools)
2. 下载 [原始固件](https://raw.githubusercontent.com/Blueforcer/awtrix3/main/docs/assets/ulanzi_original_firmware.bin)
3. 运行 ESP32 download tool 并在芯片类型中选择 ESP32
 
像下面这样设置然后点击"Start"  
  
![image](https://github.com/Blueforcer/awtrix3/assets/31169771/48a29f33-4896-4ee5-a001-17b44710c8ae)
