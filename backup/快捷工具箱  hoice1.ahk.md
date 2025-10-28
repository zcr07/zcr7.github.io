##  快捷工具箱 1

- choice1.ahk

- 注意：要将ControlColor.ahk和它放在一个目录下。

- D:\ahk1.0\Lib\choice1.ahk

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

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.29:00:09:52.png" style="width:400px;"></p><br>

========================================================

## ControlColor.ahk

- D:\ahk1.0\Lib\ControlColor.ahk

```

; http://www.autohotkey.com/board/topic/104539-controlcol-set-background-and-text-color-gui-controls/

ControlColor(Control, Window, bc := "", tc := "", Redraw := True) {
    Local a := {}
    a["c"]  := Control
    a["g"]  := Window
    a["bc"] := (bc == "") ? "" : (((bc & 255) << 16) + (((bc >> 8) & 255) << 8) + (bc >> 16))
    a["tc"] := (tc == "") ? "" : (((tc & 255) << 16) + (((tc >> 8) & 255) << 8) + (tc >> 16))

    CC_WindowProc("Set", a, "", "")

    If (Redraw) {
        WinSet Redraw,, ahk_id %Control%
    }
}

CC_WindowProc(hWnd, uMsg, wParam, lParam) {
    Local tc, bc, a
    Static Win := {}
    ; Critical

    If uMsg Between 0x132 And 0x138 ; WM_CTLCOLOR(MSGBOX|EDIT|LISTBOX|BTN|DLG|SCROLLBAR|STATIC)
    If (Win[hWnd].HasKey(lParam)) {
        If (tc := Win[hWnd, lParam, "tc"]) {
            DllCall("gdi32.dll\SetTextColor", "Ptr", wParam, "UInt", tc)
        }

        If (bc := Win[hWnd, lParam, "bc"]) {
            DllCall("gdi32.dll\SetBkColor",   "Ptr", wParam, "UInt", bc)
        }

        Return Win[hWnd, lParam, "Brush"] ; Return the HBRUSH to notify the OS that we altered the HDC.
    }

    If (hWnd == "Set") {
        a := uMsg
        Win[a.g, a.c] := a

        If ((Win[a.g, a.c, "tc"] == "") && (Win[a.g, a.c, "bc"] == "")) {
            Win[a.g].Remove(a.c, "")            
        }

        If (!Win[a.g, "WindowProcOld"]) {
            Win[a.g,"WindowProcOld"] := DllCall("SetWindowLong" . (A_PtrSize == 8 ? "Ptr" : "")
            , "Ptr", a.g, "Int", -4, "Ptr", RegisterCallback("CC_WindowProc", "", 4), "UPtr")
        }

        If (Win[a.g, a.c, "bc"] != "") {
            Win[a.g, a.c, "Brush"] := DllCall("gdi32.dll\CreateSolidBrush", "UInt", a.bc, "UPtr")
        }

        Return
    }

    Return DllCall("CallWindowProc", "Ptr", Win[hWnd, "WindowProcOld"], "Ptr", hWnd, "UInt", uMsg, "Ptr", wParam, "Ptr", lParam, "Ptr")
}


```
