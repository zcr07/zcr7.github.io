## 创建工具组窗口

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.07:14:59:56.png" style="width:400px;"></p><br>


### 启动choice1.ahk


```

F5 & F10::
Run D:\ahk1.0\Lib\choice1.ahk
Return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & F10  服务类面板 ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 

```


### choice1.ahk

```

#notrayicon
#SingleInstance Force
#NoEnv
SetWorkingDir %A_ScriptDir%
SetBatchLines -1

#Include %A_ScriptDir%\ControlColor.ahk

Gui +hWndhMainWnd
Gui Font, s9, Microsoft YaHei UI
Gui Color, 0x002E39
;Gui Add, Text, hWndhTxt x102 y49 w132 h71 +0x200, 选择要启动的软件
;ControlColor(hTxt, hMainWnd, 0xFF8080, 0x800040)

Gui Add, Button, g1 x29 y17 w80 h23, CorelDRW
Gui Add, Button, g2 x130 y17 w80 h23,Photoshop
Gui Add, Button, g3 x234 y17 w80 h23,  PDFXEdit

Gui Add, Button, g4 x29 y57 w80 h23, Joplin
Gui Add, Button, g5 x130 y57 w80 h23, FiiNote
Gui Add, Button, g6 x234 y57 w80 h23, Excel快捷
Gui Add, Button, g7 x29 y97 w80 h23, 微信
Gui Add, Button, g8 x130 y97 w80 h23, Telegram
Gui Add, Button, g9 x234 y97 w80 h23, Word

Gui Add, Button, g10 x29 y137 w80 h23, y.txt
Gui Add, Button, g11 x130 y137 w80 h23, 6
Gui Add, Button, g12 x234 y137 w80 h23, hosts

Gui Add, Button, g13 x29 y177 w80 h23, 发邮件
Gui Add, Button, g14 x130 y177 w80 h23, config.toml
Gui Add, Button, g15 x234 y177 w80 h23, config.json

Gui Add, Button, g16 x29 y217 w80 h23, 开机启动项
Gui Add, Button, g17 x130 y217 w80 h23, ahk3.ahk
Gui Add, Button, g18 x234 y217 w80 h23, ahk777.ahk

; 计算y坐标
yPos := A_ScreenHeight - 640  

; 显示窗口，设置宽度、高度和位置
Gui, Show, w340 h260 x107 y%yPos%, ⁘⁘⁘⁘⁘  软件及设置  ⁘⁘⁘⁘⁘
Return

1:
run "c:\Program Files\Corel\CorelDRAW Graphics Suite 2020\Programs64\CorelDRW.exe
ExitApp 1  ; 设置返回码为 1
Return

2:
run "C:\3\Photoshop_CC_2019_20.0.10.28848_Green\Photoshop.exe"
ExitApp 2  ; 设置返回码为 2
Return

3:
run "D:\ahk1.0\Lib\0 tool\9 PDFXEdit10_Portable_x64\PDFXEdit.exe"
ExitApp 3  ; 设置返回码为 3
Return

4:
run "D:\ahk1.0\Lib\0 tool\9 JoplinPortable\Joplin.exe"
ExitApp 4  ; 设置返回码为 4
Return

5:
run "C:\Program Files (x86)\FiiNote\FiiNote.exe"
ExitApp 5  ; 设置返回码为 5
Return

6:
run "D:\0　　tool\0000\Office\9                Office2016\Office16\EXCEL.EXE" "D:\ahk1.0\1\2\00   快捷键目录.xlsx"
ExitApp 6  ; 设置返回码为 6
Return

7:
run "C:\Program Files\Tencent\WeChat\WeChat.exe"
ExitApp 7  ; 设置返回码为 7
Return

8:
run "D:\3\Telegram\Telegram.exe"
ExitApp 8  ; 设置返回码为 8
Return

9:
run "D:\0　　tool\0000\Office\9                Office2016\Office16\WINWORD.EXE"
ExitApp 9  ; 设置返回码为 9
Return

10:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\y.txt"
ExitApp 10  ; 设置返回码为 10
Return

11:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\6"
ExitApp 11  ; 设置返回码为 11
Return

12:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "C:\Windows\System32\drivers\etc\hosts"
ExitApp 12  ; 设置返回码为 12
Return

13:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\send.py"
ExitApp 13  ; 设置返回码为 13
Return

14:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\Lib\0 tool\picgo-croe\config.toml"
ExitApp 14  ; 设置返回码为 14
Return

15:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "C:\Users\z\.picgo\config.json"
ExitApp 3  ; 设置返回码为 3
Return

16:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\1\2\00   开机启动项.ahk"
ExitApp 16  ; 设置返回码为 16
Return

17:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\Ahk3.ahk"
ExitApp 17  ; 设置返回码为 17
Return

18:
run, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\Lib\ahk777.ahk"
ExitApp 18  ; 设置返回码为 18
Return

GuiEscape:
GuiClose:
    ExitApp


```

### choice2.ahk


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

### choice.ahk


```
#notrayicon
#SingleInstance Force
#NoEnv
SetWorkingDir %A_ScriptDir%
SetBatchLines -1

#Include %A_ScriptDir%\ControlColor.ahk

Gui +hWndhMainWnd
Gui Font, s9, Microsoft YaHei UI
Gui Color, 0xC23E00
;Gui Add, Text, hWndhTxt x102 y49 w132 h71 +0x200, 选择要启动的软件
;ControlColor(hTxt, hMainWnd, 0xFF8080, 0x800040)

Gui Add, Button, g1 x29 y17 w80 h23, 共享文件夹
Gui Add, Button, g2 x130 y17 w80 h23, 共享向导
Gui Add, Button, g3 x234 y17 w80 h23, 本地安全策略

Gui Add, Button, g4 x29 y57 w80 h23, 磁盘管理
Gui Add, Button, g5 x130 y57 w80 h23, 事件查看器
Gui Add, Button, g6 x234 y57 w80 h23, 策略gpedit

Gui Add, Button, g7 x29 y97 w80 h23, 本地用户和组
Gui Add, Button, g8 x130 y97 w80 h23, 打印管理
Gui Add, Button, g9 x234 y97 w80 h23, 高级安全

Gui Add, Button, g10 x29 y137 w80 h23, 计算机管理
Gui Add, Button, g11 x130 y137 w80 h23, 设备管理器
Gui Add, Button, g12 x234 y137 w80 h23, 用户配置

Gui Add, Button, g13 x29 y177 w80 h23, 服务
Gui Add, Button, g14 x130 y177 w80 h23, 计划任务
Gui Add, Button, g15 x234 y177 w80 h23, 组件服务

Gui Add, Button, g16 x29 y217 w80 h23, Win11Mger
Gui Add, Button, g17 x130 y217 w80 h23, 环境变量
Gui Add, Button, g18 x234 y217 w80 h23, 性能监视器

; 计算y坐标
yPos := A_ScreenHeight - 640  

; 显示窗口，设置宽度、高度和位置
Gui, Show, w340 h260 x888 y%yPos%, •◃◍▹系统工具◃◍▹•
Return

1:
run C:\Windows\System32\fsmgmt.msc
ExitApp 1  ; 设置返回码为 1
Return

2:
run C:\Windows\System32\shrpubw.exe
ExitApp 2  ; 设置返回码为 2
Return

3:
run C:\Windows\System32\secpol.msc
ExitApp 3  ; 设置返回码为 3
Return

4:
run C:\Windows\System32\diskmgmt.msc
ExitApp 4  ; 设置返回码为 4
Return

5:
run C:\Windows\System32\eventvwr.msc
ExitApp 5  ; 设置返回码为 5
Return

6:
run C:\Windows\System32\gpedit.msc
ExitApp 6  ; 设置返回码为 6
Return

7:
run C:\Windows\System32\lusrmgr.msc
ExitApp 7  ; 设置返回码为 7
Return

8:
run C:\Windows\System32\printmanagement.msc
ExitApp 8  ; 设置返回码为 8
Return

9:
run C:\Windows\System32\WF.msc
ExitApp 9  ; 设置返回码为 9
Return

10:
run C:\WINDOWS\system32\compmgmt.msc
ExitApp 10  ; 设置返回码为 10
Return

11:
run C:\Windows\System32\devmgmt.msc
ExitApp 11  ; 设置返回码为 11
Return

12:
run C:\Windows\System32\DevModeRunAsUserConfig.msc
ExitApp 12  ; 设置返回码为 12
Return

13:
run C:\WINDOWS\system32\services.msc
ExitApp 13  ; 设置返回码为 13
Return

14:
;run C:\WINDOWS\system32\taskschd.msc
Run, D:\ahk1.0\Lib\0 tool\Windows11Manager\App\MyTask.exe
ExitApp 14  ; 设置返回码为 14
Return

15:
run C:\WINDOWS\system32\comexp.msc
ExitApp 3  ; 设置返回码为 3
Return

16:
run "D:\ahk1.0\Lib\0 tool\Windows11Manager\Windows11Manager.exe"
ExitApp 16  ; 设置返回码为 16
Return

17:
;run C:\Windows\System32\SystemPropertiesRemote.exe
Run control.exe sysdm.cpl`,`,3
ExitApp 17  ; 设置返回码为 17
Return

18:
run C:\Windows\System32\perfmon.msc
ExitApp 18  ; 设置返回码为 18
Return

GuiEscape:
GuiClose:
    ExitApp



```



















