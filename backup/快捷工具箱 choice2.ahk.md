##  快捷工具箱 2

- choice2.ahk


```

#notrayicon
#SingleInstance Force
#NoEnv
SetWorkingDir %A_ScriptDir%
SetBatchLines -1

#Include %A_ScriptDir%\ControlColor.ahk

Gui +hWndhMainWnd
Gui Font, s9, Microsoft YaHei UI
Gui Color, 0x3E9700
;Gui Add, Text, hWndhTxt x102 y49 w132 h71 +0x200, 选择要启动的软件
;ControlColor(hTxt, hMainWnd, 0x118080, 0xff0040)

Gui Add, Button, g1 x29 y17 w80 h23, 系统信息
Gui Add, Button, g2 x130 y17 w80 h23, 控制面板
Gui Add, Button, g3 x234 y17 w80 h23, 网络连接

Gui Add, Button, g4 x29 y57 w80 h23, 蓝牙
Gui Add, Button, g5 x130 y57 w80 h23, wifi
Gui Add, Button, g6 x234 y57 w80 h23, win功能

Gui Add, Button, g7 x29 y97 w80 h23, win更新
Gui Add, Button, g8 x130 y97 w80 h23, 安装字体
Gui Add, Button, g9 x234 y97 w80 h23, 备份与还原

Gui Add, Button, g10 x29 y137 w80 h23, GoldWave
Gui Add, Button, g11 x130 y137 w80 h23, 录音机
Gui Add, Button, g12 x234 y137 w80 h23, 批量改名

Gui Add, Button, g13 x29 y177 w80 h23, 输入法管理
Gui Add, Button, g14 x130 y177 w80 h23, 重复文件
Gui Add, Button, g15 x234 y177 w80 h23, 计算器

Gui Add, Button, g16 x29 y217 w80 h23, LosslessCut
Gui Add, Button, g17 x130 y217 w80 h23, mkvtool
Gui Add, Button, g18 x234 y217 w80 h23, ShaEncoder

; 计算y坐标
yPos := A_ScreenHeight - 640  

; 显示窗口，设置宽度、高度和位置
Gui, Show, w340 h260 x498 y%yPos%, ◌◄◌►系统工具及其他◄◌►◌
Return

1:
;Run ms-settings:network-proxy
Run control.exe /name Microsoft.System
ExitApp 1  ; 设置返回码为 1
Return

2:
Run control
ExitApp 2  ; 设置返回码为 2
Return

3:
Run control.exe /name Microsoft.NetworkAndSharingCenter
ExitApp 3  ; 设置返回码为 3
Return

4:
Run ms-settings:bluetooth
ExitApp 4  ; 设置返回码为 4
Return

5:
Run ms-settings:network-wifi
ExitApp 5  ; 设置返回码为 5
Return

6:
run C:\Windows\System32\OptionalFeatures.exe
ExitApp 6  ; 设置返回码为 6
Return

7:
Run  control.exe /name Microsoft.WindowsUpdate
ExitApp 7  ; 设置返回码为 7
Return

8:
Run control.exe /name Microsoft.Fonts
ExitApp 8  ; 设置返回码为 8
Return

9:
Run  control.exe /name Microsoft.BackupAndRestoreCenter
ExitApp 9  ; 设置返回码为 9
Return

10:
run, "C:\3\0\9 GoldWave 6.57 (x64)\GoldWave Digital Audio Editor.exe"
ExitApp 10  ; 设置返回码为 10
Return

11:
run, "D:\ahk1.0\Lib\0 tool\MOO0.exe"
ExitApp 11  ; 设置返回码为 11
Return

12:
run, "D:\ahk1.0\Lib\0 tool\ReNamer\ReNamer.exe"
ExitApp 12  ; 设置返回码为 12
Return

13:
run, "D:\ahk1.0\Lib\0 tool\9 imetl3输入法\输入法管理器.exe"
ExitApp 13  ; 设置返回码为 13
Return

14:
run, "C:\3\4\9 AllDup_4.5.20_Portable\AllDupPortable.exe"
ExitApp 14  ; 设置返回码为 14
Return

15:
run, "C:\3\4\9 CalcVoice2.14.exe"
ExitApp 3  ; 设置返回码为 3
Return

16:
run, "C:\3\0\9 LosslessCut3.36.0\LosslessCut.exe"
ExitApp 16  ; 设置返回码为 16
Return

17:
run, "C:\3\0\mkvtoolnix\mkvtoolnix-gui.exe"
ExitApp 17  ; 设置返回码为 17
Return

18:
run, "C:\3\0\9 ShanaEncoder\ShanaEncoder.exe"
ExitApp 18  ; 设置返回码为 18
Return

GuiEscape:
GuiClose:
    ExitApp


```


<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.29:00:11:03.png" style="width:400px;"></p><br>