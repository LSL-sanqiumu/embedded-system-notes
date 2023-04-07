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





## VSCode+IDF













