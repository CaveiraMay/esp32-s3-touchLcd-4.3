# ESP32-S3-Touch-LCD-4.3C Brookesia 桌面

面向微雪 Waveshare ESP32-S3-Touch-LCD-4.3C（800×480 RGB、GT911 触摸、ES8311 扬声器、ES7210 麦克风）的 Brookesia 多应用桌面移植版。包含启动器、Settings、AIChats、SquareLine 演示、计算器、画板、图库、音乐播放器、视频播放器、录音机和频谱分析仪。

4.3C BSP 补丁位于 `components/waveshare__esp32_s3_touch_lcd_4_3c`；其他 ESP-IDF 组件由组件清单解析。

## 构建与烧录

使用 ESP-IDF 5.5.x 和 ESP32-S3 工具链：

```sh
idf.py set-target esp32s3
idf.py build
idf.py -p /dev/cu.usbmodemXXXX flash monitor
```

首次烧录会写入应用、分区表及生成的模型/存储镜像。切换固件前请先备份整片 Flash。`build/`、`managed_components/`、生成的 `sdkconfig` 和设备专属备份均不纳入此仓库。
