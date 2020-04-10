---
title: 在VSCode上配置Arduino写作环境
tags:
---

解决头文件找不到的问题：
<https://mithatkonar.com/wiki/doku.php/arduino/configuring_visual_studio_code_for_arduino_development>

解决 Intellisense 无法识别`Serial`对象的问题：
<https://stackoverflow.com/questions/51614871/why-wont-arduino-intellisense-work-in-vscode>

以下放出`.vscode`中的 cpp 配置文件：

```json
{
  "configurations": [
    {
      "name": "Win32",
      "includePath": [
        "C:\\Program Files (x86)\\Arduino\\tools\\**",
        "C:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\**",
        "C:/Program Files (x86)/Arduino/hardware/arduino/avr/cores/arduino/",
        "C:/Program Files (x86)/Arduino/hardware/arduino/avr/libraries/EEPROM/",
        "C:/Program Files (x86)/Arduino/hardware/arduino/avr/libraries/HID/",
        "C:/Program Files (x86)/Arduino/hardware/arduino/avr/libraries/SPI/",
        "C:/Program Files (x86)/Arduino/hardware/arduino/avr/libraries/SoftwareSerial/",
        "C:/Program Files (x86)/Arduino/hardware/arduino/avr/libraries/Wire/",
        "C:/Program Files (x86)/Arduino/hardware/tools/avr/avr/include/",
        "C:/Program Files (x86)/Arduino/hardware/tools/avr/avr/include/avr/",
        "C:/Program Files (x86)/Arduino/hardware/tools/avr/avr/include/compat/",
        "C:/Program Files (x86)/Arduino/hardware/tools/avr/avr/include/util/"
      ],
      "defines": ["USBCON"],
      "browse": {
        "limitSymbolsToIncludedHeaders": true,
        "databaseFilename": ""
      },
      "forcedInclude": [
        "C:\\Program Files (x86)\\Arduino\\hardware\\arduino\\avr\\cores\\arduino\\Arduino.h"
      ],
      "intelliSenseMode": "msvc-x64",
      "compilerPath": "C:/Program Files (x86)/Microsoft Visual Studio/2019/Community/VC/Tools/MSVC/14.24.28314/bin/Hostx64/x64/cl.exe",
      "cStandard": "c11",
      "cppStandard": "c++17"
    }
  ],
  "version": 4
}
```
