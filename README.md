# ESP32-S3-Touch-LCD-4.3C Brookesia

A Brookesia multi-app desktop port for the Waveshare ESP32-S3-Touch-LCD-4.3C (800×480 RGB, GT911 touch, ES8311 speaker, ES7210 microphones). Includes the launcher, Settings, AIChats, SquareLine demo, Calculator, DrawPanel, Gallery, MusicPlayer, VideoPlayer, Recorder, and SpecAnalyzer.

The 4.3C BSP override is included under `components/waveshare__esp32_s3_touch_lcd_4_3c`; other ESP-IDF components are resolved from the component manifests.

## Build and flash

Use ESP-IDF 5.5.x with the ESP32-S3 toolchain:

```sh
idf.py set-target esp32s3
idf.py build
idf.py -p /dev/cu.usbmodemXXXX flash monitor
```

The first flash writes the app, partition table, and generated model/storage images. Save a full-flash backup before flashing a different image. `build/`, `managed_components/`, generated `sdkconfig`, and device-specific backups are excluded from this repository.
