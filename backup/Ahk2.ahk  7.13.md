```

#Requires AutoHotkey v1.1.36
Menu, Tray, Icon, %A_ScriptDir%\Lib\0\Library.ico  ; 自定义托盘图标
Menu, Tray, Tip, Ahk1.1                                    ; 托盘提示

#NoEnv                                                             ; 不使用旧环境变量
#SingleInstance Force                                      ; 防止重复运行
SendMode Input                                              ; 更快的发送方式
#WinActivateForce                                           ; 强制激活窗口
#ClipboardTimeout -1                                      ; 剪贴板永不超时
SetWorkingDir, %A_ScriptDir%                        ; 以脚本目录为工作目录
SetTitleMatchMode, 2                                      ; 设置窗口标题匹配为“包含”
DetectHiddenWindows, On                             ; 可以操作隐藏窗口

; 以下性能优化设置请根据需求决定是否保留
;SetBatchLines, 10ms                                        ; -1 为最大性能（高CPU）
;Process, Priority,, High                                     ; 设置脚本为高优先级
#HotkeyModifierTimeout 0                             ; 修饰键粘滞问题修复（可选）

#Persistent                                                       ; 让脚本保持常驻
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 1-19

#include *i %A_ScriptDir%\Lib\ImagePut.ahk%A_TrayMenu%.ahk
#Include *i %A_ScriptDir%\Lib\ImagePut.ahk
#Include *i %A_ScriptDir%\Lib\BTT.ahk
#Include *i %A_ScriptDir%\Lib\Gdip_All.ahk
#Include *i %A_ScriptDir%\Lib\NonNull.ahk
#Include *i %A_ScriptDir%\Lib\TrayIcon.ahk
#Include *i %A_ScriptDir%\Lib\StdOutToVar.ahk
#Include *i %A_ScriptDir%\Lib\ahk777.ahk
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 2-29

#SingleInstance Off
;MsgBox, 4096,, % A_Now
return

	OnlyOne(flag="") 
  {
  	static init:=OnlyOne("001")
  	DetectHiddenWindows, % (bak:=A_DetectHiddenWindows) ? "On":"On"
  	mypid:=DllCall("GetCurrentProcessId")
  	flag:="Ahk_OnlyOne_Ahk<<" . flag . ">>"
  	Gui, Ahk_OnlyOne_Ahk: Show, Hide, %flag%
  	WinGet, list, List, %flag% ahk_class AutoHotkeyGUI
  	Loop, % list
  	IfWinExist, % "ahk_id " . list%A_Index%
  {
    	WinGet, pid, PID
    	IfEqual, pid, %mypid%, Continue
   	 WinClose, ahk_pid %pid% ahk_class AutoHotkey,, 3
    	IfWinNotExist,,, Continue
    	Process, Close, %pid%
    	WinWaitClose
  }

  	WinGet, list, List, %flag% ahk_class AutoHotkeyGUI
  	IfNotEqual, list, 1, ExitApp
  	DetectHiddenWindows, %bak%
  }

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   限制单进程运行    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 3-63

;🎫🎫🎫🎫🎫🎫🎫🎫🎫🎫    基本   设置   🎫🎫🎫🎫🎫🎫🎫🎫🎫🎫🎫
;🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁    复制   粘贴   🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁
global MyClipData
global page
Tab & q:: 批量复制粘贴工具()
	#IfWinExist, 批量复制粘贴工具 ahk_class AutoHotkeyGUI
$^c::
	Clipboard:=""
	Send ^c{Ctrl Up}
	ClipWait, 3
	s:=Clipboard
	if (s="")
	ToolTip,
else
	批量复制粘贴工具(s)
	return
1::
	nume:=1
	Gosub copytt(nume)
	return
2::
	nume:=2
	Gosub copytt(nume)
	return
3::
	nume:=3
	Gosub copytt(nume)
	return
4::
	nume:=4
	Gosub copytt(nume)
	return
5::
	nume:=5
	Gosub copytt(nume)
	return
6::
	nume:=6
	Gosub copytt(nume)
	return
7::
	nume:=7
	Gosub copytt(nume)
	return
8::
	nume:=8
	Gosub copytt(nume)
	return
9::
	nume:=9
	Gosub copytt(nume)
	return
copytt(nume):
{
	i:=nume
	Clipboard:=MyClipData[i:=(page-1)*10+i]
	Send ^v
	return
}
0::
	nume1:=0
	Gosub copytt(nume1)
	return
copytt(nume1):
{
	i:=nume1
	Clipboard:=MyClipData[i:=(page-1)*10+10+i]
	Send ^v
	return
}
#IfWinExist
;-------- 下面是函数 --------
批量复制粘贴工具(s:="", Cmd:="")
{
static
  	if (Cmd="Move")
{
	if (A_GuiControl="")
	SendMessage, 0xA1, 2
	return
}
else if (Cmd="Click")
{
    	i:=SubStr(A_GuiControl, 3)
    	if (i>=1 and i<=10)
{
      	s:=MyClipData[i:=(page-1)*10+i]
      	if (s="")
        	return
      	if (!clear)
{
       	; Gui, MyClip: Hide
        	; Gui, MyClip: Show, NA
        	Clipboard:=s
        	Send ^v
        	Sleep, 200
        	return
}
      	MyClipData.RemoveAt(i)
      	if (MyClipData.length()<(page-1)*10+1)
        	page--
}
else if (i=11 and page>1)
	page--
else if (i=13 and MyClipData.length()>page*10)
	page++
else if (i=12)
      	clear:=!clear
}
else if (Cmd="" and s!="")
{
    	MyClipData.InsertAt(1,s), page:=1, clear:=0
}
 	 if !IsObject(MyClipData)
{
    MyClipData:=[], page:=1, clear:=0
    Run:=Func(A_ThisFunc).Bind("","Click")
    Gui, MyClip: Destroy
    Gui, MyClip: +AlwaysOnTop +ToolWindow +E0x08000000
    Gui, MyClip: Margin, 10, 10
    Gui, MyClip: Color, f39bdc8
    Gui, MyClip: Font, s11,c364f6b
    Loop, 13
    {
      i:=A_Index, v:=(i=11 ? "<<" : i=13 ? ">>" : "")
      j:=(i=1 ? "w250 Left" : i=11 ? "xm w75"
        : i=12 ? "x+0 w100" : i=13 ? "x+0 w75" : "y+0 wp Left")
      Gui, MyClip: Add, Button, %j% vbt%i% Hwndid -Wrap, %v%
      GuiControl, MyClip: +g, %id%, % Run
    }
    Gui, MyClip: Show, NA, %A_ThisFunc%
    OnMessage(0x201, Func(A_ThisFunc).Bind("","Move"))
    v:=Func(A_ThisFunc).Bind("","")
    Menu, Tray, Add
    Menu, Tray, Add, %A_ThisFunc%, %v%
    Menu, Tray, Default, %A_ThisFunc%
    Menu, Tray, Click, 1
  }
  Loop, 10
  {    Menu, Tray, Click, 1

    i:=A_Index, v:=MyClipData[(page-1)*10+i]
    v:=(v="" ? v : "[" StrLen(v) "] " SubStr(v,1,50))
    v:=RegExReplace(v, "s+", " ")
    GuiControl, MyClip: , bt%i%, %v%
  }
  GuiControl, MyClip: , bt12, % clear ? "点选条目":"+删除条目+"
  Gui, MyClip: Show, NA
}
return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ Tab+q 批量复制粘贴   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 4-216

;#Persistent
	Copy(clipboardID) 
{
	global 
	local oldClipboard := ClipboardAll ; Save the (real) clipboard

	Clipboard := "" 
	SendInput {Ctrl Down}c{Ctrl Up}
	ClipWait, 2, 1 
if ErrorLevel 
{
	Clipboard := oldClipboard ; Restore old (real) clipboard
	return
}
	ClipboardData%clipboardID% := Clipboard
	Clipboard := oldClipboard ; Restore old (real) clipboard
}
Cut(clipboardID) 
{
	global ; All variables are global by default
	local oldClipboard := ClipboardAll ; Save the (real) clipboard
	Clipboard := "" ; Erase the clipboard first, or else ClipWait does nothing
	SendInput {Ctrl Down}x{Ctrl Up}
	ClipWait, 2, 1 ; Wait 1s until the clipboard contains any kind of data
if ErrorLevel 
{
	Clipboard := oldClipboard ; Restore old (real) clipboard
	return
}
	ClipboardData%clipboardID% := Clipboard
	Clipboard := oldClipboard ; Restore old (real) clipboard
}
Paste(clipboardID) 
{
	global
	local oldClipboard := ClipboardAll ; Save the (real) clipboard
	Clipboard := "" ; Erase the clipboard first, or else ClipWait does nothing
	Clipboard := ClipboardData%clipboardID%
	ClipWait, 2, 1 ; Wait 1s until the clipboard contains any kind of data
	SendRaw, % Clipboard ; Was having an issue with ^v
	Clipboard := oldClipboard ; Restore old (real) clipboard
}
	return
;---------------------------------------------------------------------------   copy
Tab & 2::Copy(1)
Tab & 3::Copy(2)
Tab & 4::Copy(3)
Tab & 5::Copy(4)
Tab & 6::Copy(5)
Tab & s::Copy(6)
Tab & d::Copy(7)
 ;---------------------------------------------------------------------------   paste
Tab & w::Paste(1)
Tab & e::Paste(2)
Tab & r::Paste(3)
Tab & t::Paste(4)
Tab & y::Paste(5)
Tab & x::Paste(6)
Tab & c::Paste(7)
;-----------------------------------------------------------------------------   cut
Tab & f::Cut(1)
;---------------------------------------------------------------------------   paste
Tab & v::Paste(1)                                 ;-------------->Tab &  s  剪切   Tab &  x 粘贴
;-----------------------------------------------------------------------------------
return
;ΞΞΞΞΞΞΞΞΞΞ   Tab &  2345678复制  wertyui 粘贴 sd剪 xc粘 ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 05-295

;➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿➿

NumpadEnter::
	KeyList := "Shift|Ctrl|Alt|CapsLock|space|Appskey|win|F1|F2|F3|F4|F5|F6|F7|F8|F9" 
Loop, Parse, KeyList, |
      {
    	If GetKeystate(A_Loopfield, "P")   ; 如果你觉得某些按键像是“卡住了”，释放以上修饰键
        	Send % "{" A_Loopfield " Up}"
      }
; 如果你修改了桌面快捷方式或图标但图标没刷新 ⇒ 可能需要 ie4uinit.exe -ClearIconCache
Run *RunAs C:\Windows\System32\ie4uinit.exe -ClearIconCache  

sleep,1000
	reload                   ; 如果你只是修改了脚本内容，想让新内容生效 ⇒ 只要 reload
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  NumpadEnter 重启脚本 ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000005-330

;🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁    复制   操作   🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁
;🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆    截图   操作   🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆

Appskey & 5::                                ;---- 后台截图　4000 为间隔4秒  共运行3 次 
run, nircmd  loop 3 4000 savescreenshot "C:\Users\z\Desktop\a\~$currtime.HHmm_ss$ ~$loopcount$.png"
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ Appskey & 5  后台间隔截图 全屏  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 008-353
 
b100(timeout = 400, keyOverride := "")              ; keyOverride 作用是调用函数时，能指定一个按键，而不是总是使用 A_ThisHotKey 来获取当前热键
{
    tout := timeout / 1000
    key := keyOverride ? keyOverride : RegExReplace(A_ThisHotKey, "[\*\~\$\#\+\!\^]")
    Loop 
{
        t := A_TickCount
        KeyWait %key%
        Pattern .= A_TickCount - t > timeout
        KeyWait %key%, DT%tout%
        If (ErrorLevel)
            Return Pattern
    }
}
;-----------------------------------------------------------------------------------

+Esc:: 
    p := b100()
    If (p = "0")                  ; 用户触发 b106(), 开始检测当前热键的按键模式
    {
        Run, c:\3\9 FSCapture97\FSCapture.exe, , min
        Sleep, 800
        SendInput, !+x ; 开始截图
        ; 等待编辑器窗口打开
        WinWait, ahk_class TMainWin.UnicodeClass, , 20 ; 等待 5 秒，超时则跳过
        IfWinExist, ahk_class TMainWin.UnicodeClass
        {
            WinActivate ; 激活编辑器窗口
            Sleep, 500  ; 确保窗口完全激活
            SendInput, <^s
        }
    }
    If (p = "00")
    {
        Process, Close, FSCapture.exe
    }
return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  +Esc::  单击FSCapture双击退出   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 006-452

$<^Esc::     
	run "D:\ahk1.0\Lib\0 tool\ScreenCapture\ScreenCapture.exe"
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <^Esc  截图    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 21-408

$+#s::                                        ;-------------------系统自带加了一个保存在桌面
	clipboard =
	clipboard = clipboardALL
	Send, {PrintScreen}
sleep,5000
	file := ImagePutFile(clip, "C:\oneD\OneDrive\desktop\" )
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  +#s  截图  剪贴板 desktop   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 011-507

 CoordMode, Mouse, Client  ; 设置坐标模式为客户端
F1 & c::
	Run "C:\Program Files\Google\Chrome\Application\chrome.exe" ; --new-window, , max
	WinWait, ahk_exe chrome.exe, , 5         ;---------------- 最多等待 5 秒
	;Run, C:\3\v2rayN-With-Core\v2rayN.exe , , min
	;Run, D:\ahk1.0\Lib\0 tool\karing_1.0.39.527_windows_x64\karing.exe , , min
/*
Send, ^t
Sleep, 300
Send, ^+{Del}                                                       ; 执行 Ctrl + Shift + Delete
Sleep, 1000

; 定义点击次数和位置
clickCount := 1  ; 设置需要点击的次数
xPos := 978      ; 点击的 X 坐标（根据 Client 坐标调整）
yPos := 617       ; 点击的 Y 坐标（根据 Client 坐标调整）

; 循环执行 ControlClick
Loop, %clickCount%
{
    ControlClick, x%xPos% y%yPos%, ahk_class Chrome_WidgetWin_1
    Sleep, 300  ; 每次点击后暂停300毫秒，确保应用程序有时间处理请求
}
send, ^w
*/
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & C  打开 chrome     ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00011-969

#SingleInstance force                                                          ; 强制加载新的脚本
isRunning := false                  ; 状态变量: isRunning 用于跟踪脚本是否正在运行
F1 & v::
    Process, Exist, v2rayN.exe                                      ; 检查程序是否已经在运行
    if (ErrorLevel)                 ;根据 ErrorLevel 的值来决定是关闭程序还是启动程序
    {
                                                                            ; 如果程序正在运行，则关闭它
        Process, Close, v2rayN.exe
        isRunning := false                                                        ; 更新状态为未运行
    } 
    else 
    {
                                                                        ; 如果程序没有在运行，则启动它
        Run, D:\ahk1.0\Lib\0 tool\v2rayN-With-Core\v2rayN.exe , , min 
        isRunning := true                                                     ; 更新状态为正在运行
    }
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F1 & v 打开 v2rayN.exe ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00007-894

#esc::	                                                               ;   框选OCR
send, !j
sleep, 10
send, ^]
sleep, 9000
send, !u
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ #esc  关闭Vpn Ocr 再打开Vpn ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 14-305

;#SingleInstance Force
;#NoEnv
displayNum := 0
visibleState := true

F9 & 9::
	pasteToScreen(){
	if DllCall("IsClipboardFormatAvailable", "UInt", 1)
	displayText(Clipboard)
	If DllCall("IsClipboardFormatAvailable", "UInt", 2)
{
	if DllCall("OpenClipboard", "uint", 0) 
{
	hBitmap := DllCall("GetClipboardData", "uint", 2)
	DllCall("CloseClipboard")
}
	displayImg(hBitmap)
}
	if DllCall("IsClipboardFormatAvailable", "UInt", 15){
	imgFile := Clipboard
	if(hBitmap := LoadPicture(imgFile))
	displayImg(hBitmap)
}
}
	displayText(text)
{
	global
Gui, New, +hwndpasteText%displayNum% -Caption +AlwaysOnTop +ToolWindow -DPIScale
	local textHnd := pasteText%displayNum%
	Gui, Margin, 10, 10
	Gui, Font, s16
	Gui, Add, Text,, % text
	OnMessage(0x201, "move_Win")
	OnMessage(0x203, "close_Win")
	Gui, Show,, pasteToScreen_text
	transparency%textHnd% := 100
	displayNum++
}
	displayImg(hBitmap)
{
	global
Gui, New, +hwndpasteImg%displayNum% -Caption +AlwaysOnTop +ToolWindow -DPIScale
	local imgHnd := pasteImg%displayNum%
	Gui, Margin, 0, 0
	Gui, Add, Picture, Hwndimg%imgHnd%, % "HBITMAP:*" hBitmap
	OnMessage(0x201, "move_Win")
	OnMessage(0x203, "close_Win")
	Gui, Show,, pasteToScreen_img
	local img := img%imgHnd%
ControlGetPos,,, width%imgHnd%, height%imgHnd%,, ahk_id %img%
	scale%imgHnd% := 100
	transparency%imgHnd% := 100
	displayNum++
}
	move_Win()
{
	PostMessage, 0xA1, 2
}
	close_Win()
{
	id := WinExist("A")
	transparency%id% := ""
	scale%id% := ""
	width%id% := ""
	height%id% := ""
	Gui, Destroy
}

return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F9+9 贴图   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 013-588
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    Shift+鼠标滚动   改变粘贴的透明度   ΞΞΞΞΞΞΞΞΞΞ 014-588
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    鼠标滚轮改变贴图大小 双击关闭   ΞΞΞΞΞΞΞΞΞΞΞΞΞ015-588

F9 & 0::
	toggleVisibleState()
{
	global visibleState
	if(visibleState){
	WinGet, id, List, pasteToScreen
	Loop, %id%
{
	this_id := id%A_Index%
	WinHide, ahk_id %this_id%
}
	visibleState := false
} 
	else 
{
	DetectHiddenWindows, On
	WinGet, id, List, pasteToScreen
	Loop, %id%
{
	this_id := id%A_Index%
	WinShow, ahk_id %this_id%
}
	DetectHiddenWindows, Off
	visibleState := true
}
}
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F9+0 隐藏或显示所有粘贴    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 016-619

F9 & -::
	destroyAllPaste()
{
	WinGet, id, List, pasteToScreen
	Loop, %id%
{
	this_id := id%A_Index%
	SendMessage, 0x203,,,, ahk_id %this_id%
}
}
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F9+- 关闭贴图    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 017-632

F9 & =::
	FileSelectFile, imgFile, 3, C:\oneD\OneDrive\desktop\
	hBitmap := LoadPicture(imgFile)
	displayImg(hBitmap)
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F9+= 打开图并设置为贴图   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 018-639

F9 & 8::
	Imageshow({image: %clipboardAll%, scale: ["auto", 600]})  ;长自动，宽600
	;Imageshow({image: %clipboardAll%, scale: 2.25})   ; 放大到2.25倍
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F9 & 8 剪贴板贴图 放大到1.25倍   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 019-645

;🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆    截图   操作   🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆
;🎟🎟🎟🎟🎟🎟🎟🎟🎟🎟    显隐   操作   🎟🎟🎟🎟🎟🎟🎟🎟🎟🎟🎟

F5 & r::
	HideShowTaskbar()
{
   	static SW_HIDE := 0, SW_SHOWNA := 8, SPI_SETWORKAREA := 0x2F
   	DetectHiddenWindows, On
   	hTB := WinExist("ahk_class Shell_TrayWnd")
   	WinGetPos,,,, H
hBT := WinExist("ahk_class Button ahk_exe Explorer.EXE")  ; for Windows 7
   	b := DllCall("IsWindowVisible", "Ptr", hTB)
   	for k, v in [hTB, hBT]
( v && DllCall("ShowWindow", "Ptr", v, "Int", b ? SW_HIDE : SW_SHOWNA) )
   	VarSetCapacity(RECT, 16, 0)
   	NumPut(A_ScreenWidth, RECT, 8)
   	NumPut(A_ScreenHeight - !b*H, RECT, 12, "UInt")
DllCall("SystemParametersInfo", "UInt", SPI_SETWORKAREA, "UInt", 0, "Ptr", &RECT, "UInt", 0)
   	WinGet, List, List
	Loop % List
{
	WinGet, res, MinMax, % "ahk_id" . List%A_Index%
	if (res = 1)
WinMove, % "ahk_id" . List%A_Index%,, 0, 0, A_ScreenWidth, A_ScreenHeight - !b*H
}
}
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F5 & r  隐藏任务栏   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0002-679

F5 & y::          ;;隐藏文件
RegRead,value,HKEY_CURRENT_USER,Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\, Hidden
	If(value=1)
	value = 2
	Else
	value = 1
RegWrite, REG_DWORD, HKEY_CURRENT_USER,Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\, Hidden, %Value%
RegWrite, REG_DWORD, HKEY_CURRENT_USER,Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\, ShowSuperHidden, %Value%-1
	PostMessage,0x111,0x7103,0,SHELLDLL_DefView1,A
	return

F5 & k::           ;;显示文件扩展名
RegRead,Value,HKEY_CURRENT_USER,Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\,HideFileExt
	If(value=0)
	value = 1
	Else
	value = 0
RegWrite, REG_DWORD,HKEY_CURRENT_USER,Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced\,HideFileExt, %Value%
	PostMessage,0x111,0x7103,0,SHELLDLL_DefView1,A
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & k 显示扩展名 F5 & y 显隐文件   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0005-728

F5 & s::
; 设置注册表路径和值名称
regPath := "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced"
valueName := "IconsOnly"

; 读取当前的 IconsOnly 值
RegRead, currentValue, %regPath%, %valueName%

; 如果读取失败（值不存在），则将值初始化为 0
if (ErrorLevel)
    currentValue := 0

; 切换值：如果当前值是 0 则设置为 1，否则设置为 0
newValue := (currentValue = 0) ? 1 : 0

; 写入新值到注册表
RegWrite, REG_DWORD, %regPath%, %valueName%, %newValue%

 ; 刷新资源管理器以应用更改
;send, ^r
; 使用 COM 对象刷新桌面和文件资源管理器窗口
for window in ComObjCreate("Shell.Application").Windows
{
    if (window.FullName != "")  ; 检查是否是有效的资源管理器窗口
        window.Refresh()
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & s  缩略图   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0006-757

F5 & c::
Send, <!p
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F5 & c 显示预览窗格  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0007-762

F5 & 6::
	WinGetActiveTitle, Title
	Title := StrReplace(Title, "Ξ置顶 Ξ")
	ID := WinExist("A")
	WinGet, ExStyle, ExStyle, ahk_id %ID%
	If (ExStyle & 0x8)
{
	WinSet,TopMost,,A
	WinSetTitle, , ,Ξ OFF Ξ
 	SoundPlay, D:\ahk1.0\Lib\0\y2253.mp3
}
	Else
{
	WinSet,TopMost,,A
	WinSetTitle, , ,Ξ 置顶 Ξ
   	SoundPlay, D:\ahk1.0\Lib\0\2.mp3
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F5 & 6  窗口置顶    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0008-782

;🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁    显隐   操作   🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁🍁
;🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆    打开   操作   🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆

F5 & 9::
	Imageshow("D:\ahk1.0\1\1.png")
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & 9  快捷键目录   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00002-801

F5 & 0::
	Imageshow("D:\ahk1.0\1\2.png")
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & 0  快捷键目录   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00003-806
 
F5 & -::
	Imageshow("D:\ahk1.0\1\7.png")
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & 0  快捷键目录   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00003-806
 
F5 & +::
	Imageshow("D:\ahk1.0\1\5.png")
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & 0  五笔键图示   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00003-806

F5 & 8::
	o=D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe

	1=D:\ahk1.0\Lib\0 tool\picgo-croe\config.toml
	2=C:\Users\z\.picgo\config.json
	3=D:\ahk1.0\Lib\ahk777.ahk
	4=D:\ahk1.0\Ahk1.1.ahk

	Run,%o% "%1%" "%2%" "%3%" "%4%"
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & 8    EmEditor 打开4文件   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00006-856

^+z:: 
	WinGet, processID, PID, A                      ;--获取当前活动窗口的进程ID
WinGet, exePath, ProcessPath, ahk_pid %processID%    ; 获取可执行文件路径 
	SplitPath, exePath, , fileDir            ; 提取文件夹路径
	Run, %fileDir%            ; 打开文件夹
 	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  ^+z 打开当前软件的文件夹   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00005-846

CoordMode, Mouse, Window
Rctrl & 4::
WeChat:="ahk_class WeChatMainWndForPC"
WeChat_path:="C:\Program Files\Tencent\WeChat\WeChat.exe" ，max

if ProcessExist("WeChat.exe")=0
{
	Run, %WeChat_path%
WinWait, ahk_class WeChatLoginWndForPC
}
else
{
	WinGet,wxhwnd,ID,%WeChat%
	if strlen(wxhwnd)=0
	{
		winshow,%WeChat%
		winactivate,%WeChat%
	}
	else
	{
		winhide,%WeChat%
	}
}
return

ProcessExist(exe){		   ;一个自定义函数,根据自定义函数的返回值作为#if成立依据原GetPID
	Process, Exist,% exe
	return ErrorLevel
}
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  Rctrl & 4  打开 微信    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00014-1062

;#Persistent                     ;确保脚本常驻：保证脚本不因长时间未使用而自动退出。
Rctrl & 5::
    KeyWait, Rctrl, D  ; 确保释放 Rctrl 键后再执行操作

    ; 检查 EmEditor.exe 是否已存在
    IfWinNotExist, ahk_exe EmEditor.exe
    {
        Run "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe"
        ;Run "C:\0　　tool\EmEditor\EmEditor.exe"
        WinWait, ahk_exe EmEditor.exe, , 5  ; 最多等待 5 秒
    }
    Else IfWinNotActive, ahk_exe EmEditor.exe
    {
        WinActivate  ; 激活窗口
    }
    Else
    {
        ; 检查窗口是否已最小化
        IfWinExist, ahk_exe EmEditor.exe
        {
            WinGet, MinimizedState, MinMax, ahk_exe EmEditor.exe
            if (MinimizedState = -1)  ; 如果窗口已最小化
                WinRestore  ; 还原窗口
            else
                WinMinimize  ; 否则最小化窗口
        }
    }
Return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  Rctrl & 5   打开 EmEditor  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00012-999

Rctrl & 6::
    KeyWait, Rctrl, D  ; 确保释放 Rctrl 键后再执行操作

    IfWinNotExist, ahk_class CabinetWClass
    {
        Run, "C:\Windows\explorer.exe"
        WinWait, ahk_class CabinetWClass, , 5  ; 最多等待 5 秒
        If !ErrorLevel  ; 确保窗口确实已存在
        {
            Sleep, 100  ; 短暂延时确保稳定
            WinActivate
        }
    }
    Else IfWinNotActive, ahk_class CabinetWClass
    {
        WinActivate
    }
    Else
    {
        WinMinimize
    }
Return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  Rctrl & 6  打开 资源处理器   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00013-1026

;🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆    打开   操作   🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆🎆
; 💢⭐💢⭐💢⭐💢⭐💢⭐💢⭐    杂类   操作   ⭐💢⭐💢⭐💢⭐💢⭐💢⭐💢⭐💢

F6 & d::
	Clip(Format("{:" GetNextCaseFormat() "}", Clip()), true)
	GetNextCaseFormat()
{
   	static i := 0, Formats := ["U", "L", "T"]
   	return Formats[++i > 3 ? i := 1 : i]
}
	Clip(Text="", Reselect="")
{
	Static BackUpClip, Stored, LastClip
If (A_ThisLabel = A_ThisFunc) 
{
	If (Clipboard == LastClip)
	Clipboard := BackUpClip
	BackUpClip := LastClip := Stored := ""
} 
	Else 
{
If !Stored {
	Stored := True
	BackUpClip := ClipboardAll ; ClipboardAll must be on its own line
} 
	Else
	SetTimer, %A_ThisFunc%, Off
	LongCopy := A_TickCount, Clipboard := "", LongCopy -= A_TickCount ; LongCopy gauges the amount of time it takes to empty the clipboard which can predict how long the subsequent clipwait will need
	If (Text = "") 
{
	SendInput, ^c
	ClipWait, LongCopy ? 0.6 : 0.2, True
} 
	Else 
{
	Clipboard := LastClip := Text
	ClipWait, 10
	SendInput, ^v
}
	SetTimer, %A_ThisFunc%, -700
Sleep 20 ; Short sleep in case Clip() is followed by more keystrokes such as {Enter}
If (Text = "")
	Return LastClip := Clipboard
	Else If ReSelect and ((ReSelect = True) or (StrLen(Text) < 3000))
	SendInput, % "{Shift Down}{Left " StrLen(StrReplace(Text, "`r")) "}{Shift Up}"
}
	Return
	Clip:
	Return Clip()
}
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F6 & d 大小写 首字母大写  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000002-1124

<^!z::
send, ^y
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <^!z   撤消    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000007-1192

;#NoEnv
   ;SendMode Input
   ;SetWorkingDir %A_ScriptDir%
	MoveCycle(Add)
{
	static StepsInCycle = 2                        ;--------------在2种状态间切换
	static SizeCycle = 0
	SizeCycle := Mod(SizeCycle + Add, StepsInCycle)
	if (SizeCycle < 0)
	{
		SizeCycle := SizeCycle + StepsInCycle
	}
	if (Add = 111) {
		SizeCycle = 1
	}
	else if (Add = 222) {
		SizeCycle = 2
	}
	else if (Add = 333) {
		SizeCycle = 3
	}

	if (SizeCycle = 0) {
		MoveWindow(50, 50)
	}
	else if (SizeCycle = 1) {
		MoveWindow(0, 50)
	}
	else if (SizeCycle = 2) {
		MoveWindow(0, 100)
	}
	else if (SizeCycle = 3) {
		MoveWindow(15, 70)

	}
	else if (SizeCycle = 4) {
		MoveWindow(20, 80)
	}
else if (SizeCycle = 5)
	{
		MoveWindow(10, 80)
	}
}

MoveWindow(XP, WP)
{
	; Get current Window
	WinGetActiveTitle, WinTitle
	WinGetPos, X, Y, WinWidth, WinHeight, %WinTitle%

	; Get Taskbar height
	WinGetPos,,, tbW, tbH, ahk_class Shell_TrayWnd

	; Calculate new position and size
	XNew := (A_ScreenWidth * XP / 100)
	WNew := (A_ScreenWidth * WP / 100)
	HNew := (A_ScreenHeight - tbH)
	TopNew := 2

	; MsgBox, %XNew% - %WNew% ; DEBUG
	WinRestore, %WinTitle%
	WinMove, %WinTitle%,, %XNew%, %TopNew%, %WNew%, %HNew%
}

<!z::
	MoveCycle(-1)
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ <!z  窗口左半，右半切换   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000008-1261

F5 & 7::
run D:\ahk1.0\Lib\二维码.ahk
send, ^c
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & 7  二维码  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000010-1320

!LButton::    ;-- 【Win+鼠标左键】任意移动窗口位置
#LButton::    ;-- 【Win+鼠标右键】任意调整窗口大小
Critical
CoordMode, Mouse
MouseGetPos, x1, y1, id
IfWinNotExist, ahk_id %id%
  return
WinGet, flag, MinMax    ;-- 不操作最大化的窗口
if flag=1
  return
SetWinDelay, 20
WinGetPos, x2, y2, w2, h2
While GetKeyState(SubStr(A_ThisLabel,2),"P")
{
  MouseGetPos, x3, y3
  if A_ThisLabel = !LButton
    WinMove, x3-x1+x2, y3-y1+y2
  else
    WinMove,,,,, x3-x1+w2, y3-y1+h2
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  !+左键 移窗口 #+左键 调窗口大小   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000011-1363


+F12::
   p := b100()

          If (p = "0")
	Run ms-settings:network-proxy            ;------------------------- 代理 1

   Else If (p = "00")
	Run control.exe sysdm.cpl`,`,3               ;---------------------环境变量 2

   Else If (p = "000")
	;Run compMgmtLauncher
              

	run devmgmt.msc                                  ;------------------ 设备管理器 4
		
   Else If (p = "1")　
;Run, C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Administrative Tools\Task Scheduler.lnk
Run, C:\3\Windows11Manager\App\MyTask.exe ;------------------- 计划任务  5

   Else
{
	;Run dcomcnfg                                    ;------------------------组件服务 6  次数5次以上
	Run mmc 
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F12  代理 变量 管理 控制台 组件服务    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000015-1571
+F11::
   p := b100()

          If (p = "0")
	Run control                                            ;---------------------控制面板 1
	;Run control.exe  main.cpl`,`,2
	;Run control.exe sysdm.cpl`,`,2
	;Run control.exe  intl.cpl`,`,0
	;Run  intl.cpl
	;Run control.exe ncpa.cpl 
   Else If (p = "00")
Run, %A_ComSpec% /k ipconfig  ; 打开 CMD 并直接运行 ipconfig   ; ipconfig 2  C:\Windows\system32\cmd.exe
		
   Else If (p = "000")　　
	Run gpedit.msc                                      ;-----------------------组策略 3

   Else If (p = "0000")
	;Run ncpa.cpl                                          ;---------------------网络连接 4
	;Run shell:::{8E908FC9-BECC-40f6-915B-F4CA0E70D03D}
	Run control.exe /name Microsoft.NetworkAndSharingCenter

   Else If (p = "1")　　
{
               Run compmgmt.msc                             ;------------------ 计算机管理 3
	;Run shrpubw
	;Run fsmgmt.msc                                    ;-------------------共享文件夹   长按
;Run C:\Windows\System32\net1.exe
;Run C:\Windows\System32\net.exe
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F11 控制面板 IP 组策略 网络连接 共享  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000016-1593

; 💢⭐💢⭐💢⭐💢⭐💢⭐💢⭐    杂类   操作   ⭐💢⭐💢⭐💢⭐💢⭐💢⭐💢⭐💢
; ➰➰➰➰➰➰➰➰➰➰   选行   选段   ➰➰➰➰➰➰➰➰➰➰➰

<!1::
send, {home}{shiftdown}{end}{shiftup}^c
Return
<!q::
Send +{Home}^c
Return
<!a::
Send {shift down}{End down}{End up}{shift up}^c
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <!1 复整行　<!q 到行首  <!a 到行尾   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000002-1679

<!2::
send, {home}{shiftdown}{end}{shiftup}^v
Return
<!w::
Send +{Home}^v
Return
<!s::
Send {shift down}{End down}{End up}{shift up}^v
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <!2 粘整行  <!w 光标前 <!s 光标后     ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000003-1690

<!3::
send, {home}{shiftdown}{end}{shiftup}^x
Return
<!e::
Send +{Home}^x
Return
<!d::
Send {shift down}{End down}{End up}{shift up}^x
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <!3 剪整行  <!e 光标前   <!d 光标后    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000004-1701

<#1::
send, {home}{shift down}{end}{shift up}
Return
<#q::
Send +{Home}
Return
<#a::
Send {shift down}{End down}{End up}{shift up}
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <#1选整行　<#q到行首 <#a到行尾    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000005-1712

<#3::
send !{End}+!{home}
Return
<#w::
Send +{Home}{delete}
Return
<#s::
Send {shift down}{End down}{End up}{shift up}{delete}
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <#3 选整段  <#w光标前 <#s光标后    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000006-1723

<#2::
send, {home}{shiftdown}{end}{shiftup}{delete}
Return
#If (WinActive("ahk_class XLMAIN") or WinActive("ahk_class OpusApp") or WinActive("ahk_exe Notepad3.exe") or WinActive("ahk_exe EmEditor.exe") or WinActive("ahk_class Chrome_WidgetWin_1"))
<#e::
Send ^+{home}
Return
#IfWinActive
<#d::
Send ^+{End}
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <#2 删整行 <#e 光标前 <#d 光标后   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000007-1736

; ➰➰➰➰➰➰➰➰➰➰   选行   选段   ➰➰➰➰➰➰➰➰➰➰➰
; 🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵   滚动   速度   🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵

; Process: 这是 AutoHotkey 的另一个命令，用于处理与进程相关的操作。
; WaitClose: 这是 Process 命令的一个子命令，表示等待指定进程关闭。
; %pid%: 这里引用了上一步存储在 pid 变量中的进程 ID。% 是 AHK 中用于表示变量内容的语法。
; 30: 这是等待的时间（以秒为单位）。如果进程提前关闭，脚本会立即继续，而无需等待满 30 秒。
Lwin::return
#t::
;Run, "C:\3\9金山截图王\kscrcap.exe", , , pid
;Run, "D:\ahk1.0\Lib\0 tool\SGScreencapture\screencapture.exe", , , pid
Run, "D:\ahk1.0\Lib\0 tool\ScreenCapture\ScreenCapture.exe", , , pid
Process, WaitClose, %pid%, 10

; 确认是否上传
MsgBox, 4,, 请在完成截图和编辑后点击“是”确认上传图片。
IfMsgBox, No
    return

; 上传图片
RunWait, D:\ahk1.0\Lib\0 tool\picgo-croe\upgit.exe :clipboard -o clipboard -f ccc, , hide
/*
; 替换剪贴板中多余的路径
ClipWait, 4
clipboard := StrReplace(clipboard, "/zb9678/node-1/main/", "/")

*/
return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ     #T  上传截图到github/img       ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  000001-1984

#y::

    ; 获取选中文件的路径
    	FilePath := ""
    	Send, ^c                                                 ; 复制选中文件路径到剪贴板
    	Sleep, 200
    	FilePath := Clipboard
    	if (FilePath = "")
    {
        	MsgBox, 请先选中一个文件！
        	return
    }

    ; 提取目录和扩展名
    	SplitPath, FilePath, , Dir, Ext, Name
    	NewFileName := "up111." . Ext
    	NewFilePath := Dir . "\" . NewFileName
    ; 重命名文件（避免中文名）
    	FileMove, %FilePath%, %NewFilePath%, 1
    	if (ErrorLevel)
    {
        	MsgBox, 文件重命名失败！
        	return
    }

    ; 上传文件, 将文件的下载地址或直链复制到剪贴板中  txt,png为直链，ahk为下载地址
    	RunWait, "upgit.exe" "%NewFilePath%" --output-type clipboard, , hide   

    ; 恢复原文件名
    	FileMove, %NewFilePath%, %FilePath%, 1
    return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #y  上传剪贴板中的文件   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  000006-2067

;#Persistent
#u::

	clipboard := "" 
	Send, ^c
	Sleep, 100  ; 等待剪贴板更新

	filePath := Clipboard  ; 获取剪贴板内容
	if (!FileExist(filePath))
       {
   	 MsgBox, 16, 错误, 剪贴板内容无效，请复制文件后再试。
    	return
      }

	RunWait, cmd /c picgo u "%filePath%", , Hide
	MsgBox, 文件上传完成！
    return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #u  上传剪贴板中的文件   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  000005-2051

#i::
; 如果上传后，剪贴板中显示有链接，但链接却打开失败，要修改CF的worker.js中第12行的Token
; https://dash.cloudflare.com/67409d2d85f857acbae76bd86edbe9fc/workers/services/edit/billowing-morning-node123/production
; 如果上传后，剪贴板中无内容，要修改config.json的第24行的Token
; C:\Users\z\.picgo\config.json

    	;Run, "D:\ahk1.0\Lib\0 tool\SGScreencapture\screencapture.exe", , , pid
	Run, "D:\ahk1.0\Lib\0 tool\ScreenCapture\ScreenCapture.exe", , , pid
    	Process, WaitClose, %pid%, 30  ; 等待进程关闭，最长 30 秒

; 确认是否上传
    	MsgBox, 4,, 请在完成截图和编辑后点击“是”确认上传图片。

    	IfMsgBox, No                                         ;---------------选择“否”则退出
        	return             

; 上传图片
    	RunWait, cmd /c "picgo u",, hide
    return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #i  上传截图到github/img   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  000002-2000

; 🚧🚧🚧🚧🚧🚧🚧🚧🚧🚧🚧  上传   图库    🚧🚧🚧🚧🚧🚧🚧🚧🚧🚧
; 🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞  光标   操作    🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞

CapsLock & q:: Send, {Backspace}
CapsLock & e:: Send, {Delete}
CapsLock & f:: Send, {Enter}
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    q 退格 e 删除 f 回车    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000002-2081

CapsLock & g::
	Send {End}
	Send {Enter}
	Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    AppsKey & g 任意位置回     ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000003-2087

; 🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞  光标 鼠标  🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞
; 🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞 快捷  搜索  🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞

F1 & 1::
send,{ctrl down}c{ctrl up}
sleep,200
ClipWait

  	Run, "C:\3\Everything-1.5.0.1356a.x64\Everything64.exe"  -s "%clipboard%"

return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & 1 用Evething搜索选中的文字    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000001-2102

#If (WinActive("ahk_exe chrome.exe") or WinActive("ahk_exe EmEditor.exe"))
F1::return  ; 禁用 F1 的单独功能
F1 & 2:: 
Click, 1400,170  , Right
	Click Right
	Send {T}{enter}
Click, 1400,170
return
#If  ; 结束限制
;如果你的条件比较简单且仅仅是检查窗口，#IfWinActive 完全可以满足需求。
;如果你需要更复杂的条件判断，下面这种  #If 更加灵活且强大。
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F1 & 2   谷歌翻译  中/ 英   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000002 -2128

F1 & 3::                                                                
	send, ^c
	KeyWait F1
	if WinExist("ahk_exe 百度翻译.exe")
{
	WinActivate
}
	else
{
    run, "D:\ahk1.0\Lib\0 tool\百度翻译v1.8.0开代理\BaiDuTranslator.exe"
}
	sleep, 2000
	send, ^v
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F1 & 3   百度翻译    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000003-2183

F1 & 4::
	Send, {ctrl down}c{ctrl up}
	KeyWait F1
	Run https://www.baidu.com/s?ie=UTF-8&wd=%clipboard%
	return
 ;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & 4 用百度搜索选中的文字   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000004-2190

F1 & 5::
  	Send, {ctrl down}c{ctrl up}
	KeyWait F1
	Run http://www.google.com.tw/search?hl=zh-TW&q=%Clipboard%
	return
 ;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & 5 用谷歌搜索选中的文字   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000005-2197

F1 & 6::
    Send, ^c
    Sleep, 100

    ; 检查程序是否已运行
    IfWinNotExist, ahk_exe 9 MobipocketReader_6.2.exe
    {
        Run, "C:\3\4\9 MobipocketReader_6.2.exe"
        WinWait, ahk_exe 9 MobipocketReader_6.2.exe, , 5 ; 最多等待 5 秒
    }

    ; 激活程序窗口
    WinActivate, ahk_exe 9 MobipocketReader_6.2.exe
    WinWaitActive, ahk_exe 9 MobipocketReader_6.2.exe, , 5 ; 确保窗口激活，最多等待 5 秒

    ; 发送按键操作
    Send, {Up}{Enter}^v{Enter}
Return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F1 & 6 Mobi    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000006-2220

F1 & 7::
; 复制当前选中的文字
clipboard := ""          ; 清空剪贴板
Send, ^c
ClipWait, 1              ; 最多等1秒等待剪贴板
if (!clipboard)
{
    MsgBox, 未复制到任何文本，请重试。
    return
}
clipboard := Trim(clipboard)

; 启动或激活 Mobipocket Reader
if WinExist("ahk_class MobiDesktopReader")
{
    WinActivate
}
else
{
    Run, "C:\3\4\9 MobipocketReader_6.2.exe"
    WinWait, ahk_class MobiDesktopReader, , 10
    if ErrorLevel
    {
        MsgBox, Mobipocket Reader 未能在10秒内启动。
        return
    }
}

WinWaitActive, ahk_class MobiDesktopReader, , 2
if ErrorLevel
{
    MsgBox, Mobipocket Reader 窗口未能在2秒内激活。
    return
}

; 聚焦搜索框
ControlFocus, Edit1, ahk_class MobiDesktopReader
Sleep, 100
ControlClick, Edit1, ahk_class MobiDesktopReader
Sleep, 100

; 清空搜索框
SendInput, ^a{Backspace}
Sleep, 100

; 输入剪贴板内容（逐个字符）
Loop, Parse, clipboard
{
    SendInput, %A_LoopField%
    Sleep, 10  ; 可调整打字速度，防止太快丢字
}

Sleep, 100
SendInput, {Enter}
return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F1 & 0 Mobi    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000003-2183

F1 & 8::
clipboard := ""
    Send {ctrl down}c{ctrl up}
Run, D:\ahk1.0\Lib\0\1.chm
sleep, 600
SendInput {alt down}s{alt up}
sleep, 50
SendInput {ctrl down}v{ctrl up}{Enter}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F1 & 8  帮助文档    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00001-796

F1 & 9::
	Send, {ctrl down}c{ctrl up}
	KeyWait F1
	sleep,20
  	Run  http://youtube.com/results?q=%clipboard%
	return
 ;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & 9  youtube   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000008-2235

F1 & 0::
	Send, {ctrl down}c{ctrl up}
		KeyWait F1
	sleep,20
  	Run  https://zh.wikipedia.org/wiki/Special:Search/%clipboard%
	  	return
 ;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F1 & 0  wiki    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000010-2260

; 🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞 快捷  搜索  🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞🎞
; 🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼 关机  重启  🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼

F5 & E::
Run, nircmd speak text "重启资源管理器" 0 90
sleep, 2000
process,close,explorer.exe
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F5 & E 重启资源管理器    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000006-2312

; 🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼 关机  重启  🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼
; 🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️ 文档  编辑  🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️


:*?:a111::ā
:*?:a222::á
:*?:a333::ǎ
:*?:a444::à

:*?:e111::ē
:*?:e222::é
:*?:e333::ě
:*?:e444::è

:*?:o111::ō
:*?:o222::ó
:*?:o333::ǒ
:*?:o444::ò

:*?:i111::ī
:*?:i222::í
:*?:i333::ǐ
:*?:i444::ì

:*?:u111::ū
:*?:u222::ú
:*?:u333::ǔ
:*?:u444::ù                                                             ;   努 nǔ     路 lù

:*?:v111::ǖ                                                             ;  只用于  n 、l    比如：女（nǚ）和绿（lǜ）
:*?:v222::ǘ
:*?:v333::ǚ
:*?:v444::ǜ
:*?:v555::ü
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  3个12345  aoeiuü    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 01-2354

:*:]\9::zb9678@gmail.com		         ; f9

:*:]\z::zcr071225@gmail.com                                ; f7
:*:]\k::kev071225@gmail.com
:*:]\n::ngro1031@gmail.com

:*:]\y::zyy7031@gmail.com		         ; f8
:*:]\7::zbb7001@gmail.com
:*:]\o::zb9678@outlook.com
:*:]\h::zb9678@hotmail.com

:*:]\1::9678@163.com

:*:]\r::r@zbb07.filegear-sg.me
:*:]\z::z@zbb07.filegear-sg.me
:*:]\2::2@zbb07.filegear-sg.me
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   ]\ z 9 k n y 7 o h   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 03 -2470

; 🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️ 文档  编辑  🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️
;🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁  颜色  处理  🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁

F6 & 1::
    Clipboard := ""
    Send, ^c
    ClipWait, 2
    Clipboard := RegExReplace(Clipboard, "(\R\s*){2,}", "`r`n`r`n")
    Send, ^v
return
; 当我们使用 "`r`n" 时，它只会将光标移动到下一行的开始，但不会创建一个空行。使用 "`r`n`r`n" 实际上是创建了两个连续的换行符，这就会产生一个空行的效果.
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F6 & 1  选中 合并多行空行为１行   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 12-2665

F6 & 2::
SetWorkingDir, %A_ScriptDir%  ; 设置工作目录

; 复制内容到剪贴板
Send, ^c
ClipWait, 2
sleep, 200
if ErrorLevel
{
    MsgBox, 复制失败或超时
    return
}

; 处理剪贴板内容
text := Clipboard
text := StrReplace(text, "`r")  ; 移除所有回车符

; 使用数组存储非空行
lines := StrSplit(text, "`n")
output := ""

for index, line in lines
{
    if (line != "") {  ; 忽略空行
        output .= line . "`n"
    }
}

; 移除最后一个换行符
output := RTrim(output, "`n")

; 将结果写回剪贴板
Clipboard := output
Send, ^v

return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F6 & 2  选中 删除空行   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 13-2706

F6 & 3::
    	Clipboard := ""
    	Send, ^c
    	ClipWait
    	Clipboard := RegExReplace(Clipboard, "\R", "`r`n`r`n")
    	Send, ^v
return                                                                   ;-------回车变换行即增加一行
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F6 & 3 选中 添加空行   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 14-2715
/*
F6 & 4::
	clipboard =
	send, ^c
	sleep, 100
	a = %clipboard%
	stringreplace, out, a, ` , `n, All
	send, %out%
return                                                                   ;-------回车变换行即增加一行．和上面的区别：空格处也变换行　
*/
F6 & 4::
    	Clipboard := ""
    	Send, ^c
    	ClipWait
    	Clipboard := RegExReplace(Clipboard, "\s", "`r`n")
    	Send, ^v
return  
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F6 & 4  选中 空格及回车 变换行  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 15-2725

F6 & 5::
    Clipboard := ""  ; 清空剪贴板
    Send, ^c         ; 发送 Ctrl+C 复制选中的文本
    ClipWait, 1     ; 等待最多 1 秒，直到剪贴板有内容
    if (ErrorLevel) {
        MsgBox, 剪贴板没有内容，请确保已选中文本。
        return
    }
    ; 使用更简单的正则表达式来替换换行符
    Clipboard := RegExReplace(Clipboard, "\s*[\r\n]+\s*", "")  ; 替换多个换行符为空格
    Send, ^v         ; 粘贴处理后的内容
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F6 & 5 多行文字合并成一行  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 16-2739

;🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀  空行  处理  🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀
;🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️  空格  处理  🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️

F6 & 6::
	Clipboard := ""
	Send, ^c
	ClipWait
	Clipboard := RegExReplace(Clipboard, "[ \R]+", "$1")
sleep, 400
send, ^v
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ F6 & 6  选中 删除空格   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 17-2752

F6 & 7::
	Clipboard := ""
	Send, ^c
	ClipWait
	Clipboard := RegExReplace(Clipboard, "[ \R]+", " ")
sleep, 400
send, ^v^a
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F6 & 7  选中 多个空格变一个  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 18-2762

F6 & 8::
	Clipboard := ""
	Send, ^c
	ClipWait
	Clipboard := RegExReplace(Clipboard, "m)^[ \R]+|[ \R]+$", "$1")
	Clipboard := Trim(clipboard)
sleep, 400
send, ^v
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F6 & 8  选中  只删除首尾空格  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 19-2773

F6 & 9::
clipboard =
send, ^c
sleep, 500
Loop
{
StringReplace, clipboard, clipboard, `t ,` , UseErrorLevel                         ;  注意`后有个空格    空格表示法 `
    if ErrorLevel = 0
        break
}
sleep,200
send,^v
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F6 & 9 Tab替换成空格    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 20-2788

;🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️  空格  处理  🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️🎞️
;🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒  马克  文档  🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒

F1 & h::
Run, "D:\ahk1.0\Lib\run_hidden.vbs", , Hide
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & h  更新Github dns   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 
Tab::tab




```