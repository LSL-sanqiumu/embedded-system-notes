# 开发环境

## Arduino

1、新建一个文件夹`ArdunioProjects`用来存放ESP32支持包。

2、解压`esp32c3_支持ESP32和ESP32S2.zip`后，放到`ArdunioProjects/hardware`中。

3、打开arduino配置首选项，将项目文件夹地址改为`ArdunioProjects`目录，使用绝对路径。

4、工具  → 开发板 → 选择ESP32Arduino（in stetchbook）→ 选开发板。

## VSCode+Arduino

1、安装Arduino插件。

2、View → Command Palette →  Arduino: Board Config、Arduino: Board Manager、Arduino Examples。

3、左下角设置 →  settings →  Open settings → 添加上：

```json
"arduino.path": "D:\\EmbeddedSoftware\\Arduino", //添加这句路径，实际路径改为你安装的文件夹
```

settings.json ：

```json
{
    "workbench.iconTheme": "vscode-icons",
    "editor.linkedEditing": true,
    "files.autoSave": "afterDelay",
    "window.zoomLevel": 1.3,
    "editor.fontLigatures": true,
    "editor.fontFamily": "Fira Code Retina",
    "remote.SSH.remotePlatform": {
        "MyCentOS7": "linux"
    },
    "arduino.path": "D:\\EmbeddedSoftware\\Arduino", //添加这句路径，实际路径改为你安装的文件夹
    "C_Cpp.intelliSenseEngine": "Tag Parser",
    "editor.insertSpaces": true,
    "files.autoGuessEncoding": true,
    "arduino.logLevel": "info",
    "explorer.confirmDelete": false,
    "editor.detectIndentation": false,
}
```

## MicroPython

1、开发软件与固件下载：

下载安装Thonny：[Thonny, Python IDE for beginners](https://thonny.org/)，直接安装即可。

芯片固件下载：[MicroPython - Python for microcontrollers](https://micropython.org/download/)，往下拉找到需要的MCU的固件，ESP32、ESP32—C3、ESP32—S3等，下载最新版的.bin文件。

2、Thonny——配置解析器与固件烧录进芯片：

1. 开发板用USB线与电脑连接。
2. 打开Thonny → 工具 → 选项 → 解释器，然后选择解释器——ESP32的就选ESP32的，ESP32—C3、ESP32—S3就选ESP8266的。
3. 然后点击`安装或更新MicroPython`，选择串口通道、选择下载好的bin文件后点击安装，等待直到出现`done`。（有些板子可能在安装时需要长按板子上的BOOT键）

3、完成。

 4、开发文档：[Quick reference for the ESP8266 — MicroPython latest documentation](https://docs.micropython.org/en/latest/esp8266/quickref.html#)，C3、S3的是8266的，ESP32则是ESP32。



# 管脚

ESP32C3—MINI 1模组：

| 从ESP往USB接口方向，右边 | 从ESP往USB接口方向，左边 |
| ------------------------ | ------------------------ |
| TXD0                     | GND                      |
| RXD0                     | V3                       |
| IO19                     | NC1                      |
| IO18                     | IO2                      |
| IO9                      | IO3                      |
| IO8                      | NC2                      |
| IO7                      | EN                       |
| IO6                      | NC3                      |
| IO5                      | NC4                      |
| IO4                      | IO0                      |
| IO10                     | IO1                      |
| GND                      | GND                      |
| V3                       | V5                       |
|                          |                          |













