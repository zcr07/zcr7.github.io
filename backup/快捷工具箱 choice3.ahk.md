## 快捷工具箱  3

- choice3.ahk


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

Gui Add, Button, g16 x29 y217 w80 h23, 出入站规则
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
Run wf.msc
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

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.29:00:09:10.png" style="width:400px;"></p><br>