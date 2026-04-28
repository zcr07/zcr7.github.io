```

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

#If ( WinActive("ahk_exe chrome.exe")  or WinActive("ahk_exe WeChatAppEx.exe")  or WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Notepad3.exe") or WinActive("ahk_exe EmEditor.exe") or WinActive("ahk_exe Joplin.exe"))
www=0
F4 & Esc::
{
www:=!www
If(www=0)
{
SetTimer, aaaa, Off
SetTimer, bba, Off

}
ELSE
	{
	SetTimer, aaaa, 50	 ;滚动速度
	}
}
Return
	aaaa:
	{
	ControlGetFocus, control, A
	SendMessage, 0x115, 0, 0, %control%, A
	;SendMessage, 0x115, 2, , %control%, A
	}
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F4 & Esc 快速向上滚动   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000001-1765

F4 & F1::
{
	www:=!www
	If(www=0)
	{
	SetTimer, bba, Off
	SetTimer, aaaa, Off
	}
ELSE
	{
	SetTimer, bba, 50	;滚动速度
	}
}
Return
	bba:
	{
	ControlGetFocus, control, A
	SendMessage, 0x115, 1, 0, %control%, A
	;SendMessage, 0x115, 3, , %control%, A
	}
Return
#IfWinActive
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F4 & F1 快速向下滚动   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000002-1789

F3 & Esc::
{
www:=!www
If(www=0)
{
SetTimer, aaa, Off
SetTimer, bb, Off
}
ELSE
	{
	SetTimer, aaa, 1000	 ;滚动速度
	}
}
Return
	aaa:
	{
	ControlGetFocus, fcontrol, A
	Loop 1                                                          ; 行数
	SendMessage, 0x115, 0, 0, %fcontrol%, A
	}
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F3 & Esc 缓慢向上滚动   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000003-1812

#ifwinactive
www=0

F3 & F1::
{
	www:=!www
	If(www=0)
	{
	SetTimer, bb, Off
	SetTimer, aaa, Off
	}
ELSE
	{
	SetTimer, bb, 1000	;滚动速度
	}
}
Return
	bb:
	{
	ControlGetFocus, fcontrol, A
	Loop 1                                     ; 行数
	SendMessage, 0x115, 1, 0, %fcontrol%, A
}
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F3 & F1 缓慢向下滚动   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000004-1838

F2 & Esc::                                                               ; 向下滚动 3行
Click , WU, 1
Return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F2 & Esc 缓慢向下滚动   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000004-1838

;F2 & F1::                                                               ; 向上滚动 3行
Click , WD, 1
Return

F2 & F1::                                                               ; 向上滚动 3行
    Send, {WheelDown 1} ; 向下滚动 1 行
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F2 & F1 缓慢向下滚动   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000004-1838

; 🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵   滚动   速度   🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵🔵
;🎵🎵🎵🎵🎵🎵🎵🎵🎵🎵    颜色   坐标   🎵🎵🎵🎵🎵🎵🎵🎵🎵🎵🎵

F5 & o::
	MouseGetPos, mouseX, mouseY
PixelGetColor, color, %mouseX%, %mouseY%, RGB ; 调用 PixelGetColor 函数，获得 RGB 值，并赋值给 color                     
StringRight color,color,6    ; 截取 color（第二个 color）右边的6个字符，因为获得的值是这样的：0x8700FF，一般我们只需要 8700FF 部分。把截取到的值再赋给 color（第一个 color）。

	clipboard = #%color%        ;--------------------------------- 添加了 #
	tooltip, %clipboard%          ;--------------- 把 color 的值发送到剪贴板
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & o 获得 RGB 值    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000001-1853

F5 & P::  
    	ClipSaved := ClipboardAll        ; ------------------保存当前剪贴板内容
    	Clipboard := ""                         ;-- 清空剪贴板以确保后续操作的准确性
	Send ^c  
    	ClipWait                                    ; ------------------等待剪贴板内容更新
	color := Clipboard                    ;------------------ 获取剪贴板中的色值
    	;Clipboard := ClipSaved           ;----------------------- 恢复剪贴板内容

    ; 检查颜色格式并转换为 RGB
    if (SubStr(color, 1, 1) = "#") {
        color := SubStr(color, 2)  ; 去掉 "#"
    }
    
    if (StrLen(color) = 6) {
        ; 使用 AutoHotkey 内置的十六进制转换
        r := "0x" SubStr(color, 1, 2)
        g := "0x" SubStr(color, 3, 2)
        b := "0x" SubStr(color, 5, 2)

Gui, New, +Escape +AlwaysOnTop, Color Preview          ; 创建 GUI 窗口以显示颜色，并启用 Esc 关闭功能
        	Gui, Color, % "0x" color  ; 设置背景颜色为获取的颜色        

        	Gui, Add, Text, Center, #%color%）
        	Gui, Font, s14 Bold  ; 设置字体大小和样式
Gui, Show, w200 h200, Color Preview    ; 设置窗口大小为正方形 200x200 像素
} 
	else 
{
        	MsgBox, Invalid color format. Please use #RRGGBB.
}
	return
	GuiClose:
	GuiEscape:
	Gui, Destroy
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & p 显示颜色  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000002-1890

	autostart:=1
	autostartLnk:=A_StartupCommon . "D:\ahk1.0\Lib\se.ahk"
F5 & [::

	if(autostart)
{
    	IfExist, % autostartLnk
{
        	FileGetShortcut, %autostartLnk%, lnkTarget
        	if(lnkTarget!=A_ScriptFullPath)
FileCreateShortcut, %A_ScriptFullPath%, %autostartLnk%, %A_WorkingDir%
}
	else
{
FileCreateShortcut, %A_ScriptFullPath%, %autostartLnk%, %A_WorkingDir%
}
}
	else
{
    	IfExist, % autostartLnk
{
       	FileDelete, %autostartLnk%
}
}
;----------------------------------------------------------------------------------
WinMoveZ(hWnd, C, X, Y, W, H, Redraw:=0) 
{ ;  WinMoveZ v0.5 by SKAN on D35V/D361 @ tiny.cc/winmovez
Local V:=VarSetCapacity(R,48,0), A:=&R+16, S:=&R+24, E:=&R, NR:=&R+32, TPM_WORKAREA:=0x10000
C:=( C:=Abs(C) ) ? DllCall("SetRect", "Ptr",&R, "Int",X-C, "Int",Y-C, "Int",X+C, "Int",Y+C) : 0
DllCall("SetRect", "Ptr",&R+16, "Int",X, "Int",Y, "Int",W, "Int",H)
DllCall("CalculatePopupWindowPosition", "Ptr",A, "Ptr",S, "UInt",TPM_WORKAREA, "Ptr",E, "Ptr",NR)
X:=NumGet(NR+0,"Int"),  Y:=NumGet(NR+4,"Int")
Return DllCall("MoveWindow", "Ptr",hWnd, "Int",X, "Int",Y, "Int",W, "Int",H, "Int",Redraw)
}
;----------------------------------------------------------------------------------
	#NoEnv
	#SingleInstance, Force
	CoordMode, Mouse, Screen
	CoordMode, Pixel, Screen

Gui New, -Caption  +Escape +Border +hWndhWnd +Disabled +AlwaysOnTop
	Gui, Margin, 15, 70         ; ----------------------------------宽度与高度
Gui, Add, Edit, w50 Center  yellow   ;文字左右居中 Center, yellow  加上逗号则上下居中
	Gui, Show
	WinGetPos, X, Y, W, H, ahk_id %hWnd%
	PX:=X, PY:=Y
	Loop
{
  	MouseGetPos, X, Y
  	If ! (X=PX and Y=PY)
{
      	WinMoveZ(hWnd, 96, X, Y, W, H), PX:=X, PY:=Y
      	PixelGetColor, C, %X%, %Y%, RGB
      	Gui, Color, % PC:=C
      	GuiControl,,Edit1, % Format("{:06X}",C)
}
  	Sleep 50
}
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & [  颜色值 鼠标跟随  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000003-1951

F5 & ]::
	MouseGetPos, xpos, ypos
	clipboard = %xpos%,%ypos%
	a = %xpos%_%ypos% 	;-------------------------a = 鼠标位置`(X,Y`)
	tooltip, %a%
	return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & ] 获取当前鼠标指针的坐标   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000004-1959

;🎵🎵🎵🎵🎵🎵🎵🎵🎵🎵    颜色   坐标   🎵🎵🎵🎵🎵🎵🎵🎵🎵🎵🎵
; 🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧🚧    上传   图库   🚧 🚧 🚧 🚧 🚧 🚧 🚧 🚧🚧   

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

AppsKey & w::Send {Up}
	AppsKey & s::Send {Down}
		AppsKey & a::Send {Left}
			AppsKey & d::Send {Right}
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    adws 上 下 左 右   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000001-2076

AppsKey & q:: Send, {Bs}
	AppsKey & e:: Send, {delete}
		AppsKey & f:: Send, {Enter}
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    q 退格 e 删除 f 回车    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 0000002-2081

AppsKey & g::
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

/*
#IfWinActive ahk_exe chrome.exe or ahk_exe EmEditor.exe     ;只对chrome  EmEditor 起作用
F1::return                                         ; 覆盖单独按下 F1 的功能，不执行任何操作
F1 & 2::                                            ; 打开谷歌翻译，回车激活切换中英
Click, 1400,170  , Right
	Click Right
	Send {T}{enter}
Click, 1400,170
return
#IfWinActive                                     ; 结束限制
*/
;-----------------------------------------------------------------------------------

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

F4 & z::
Run, nircmd speak text "确定注销，请点是" 0 90
Run, nircmd.exe cmdwait 100 qboxcom ".............注  销............." "  注意：保存文件" exitwin logoff
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & z 注销     ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000001-2280
F4 & c::
;Run, nircmd speak text "确定重启 请点是" 0 90
Run, nircmd.exe  cmdwait 100 qboxcom ".............重  启............." "  注意：保存文件" exitwin reboot
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & c 重启     ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000002-2285

F4 & g::
;Run, nircmd speak text "确定关机 请点是" 0 90
Run, nircmd.exe cmdwait 100 qboxcom ".............关  机............." "  注意：保存文件" exitwin poweroffr
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & g 关机    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000003-2291

F4 & S::
;Run, nircmd speak text "进入待机 请点是" 0 90
Run, nircmd.exe cmdwait 100 qboxcom ".............睡　眠............" "  睡眠：注意保存文件" standby
sleep, 500
send, y
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & S 睡眠    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000004-2299

F4 & x::
;Run, nircmd speak text "确定休眠 请点是" 0 90
Run, nircmd.exe cmdwait 100 qboxcom ".............休　眠............." "  注意：保存文件" hibernate
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & X 休眠    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000005-2305

F4 & E::
Run, nircmd speak text "重启资源管理器" 0 90
sleep, 2000
process,close,explorer.exe
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & E 重启资源管理器    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000006-2312

F4 & p::
Run, nircmd speak text "关屏" 0 90
Run, nircmd.exe cmdwait 2000 monitor off
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ    F4 & p 关屏    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 000000007-2318

; 🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼 关机  重启  🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼🎼
; 🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️ 文档  编辑  🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️🕸️
/*
  ？和 *
::a8::ā     a8        需空格ā       ya8   只能单独使用，前面有y就不能变为 ā
:?:a0::ā   a0        需空格ā        yā     前面有y没关系。

:*:a9::ā    无需空格 ā          ya9     只能单独使用，前面有y就不能变为 ā
:*?:a7::ā  无需空格 ā           yā       前面有y没关系。
-------------------------------------------------------------------------------
  o 和 *
;     :o:     :o:a111::ā      a111按下空格后　ā   　   ā后无空格           sa111 空格无法替换        非自动　去除后面的空格  o omit　即忽略空格，但不能自动触发
;     :*:      :*:a111::ā       a111自动替换为　ā　　  ā后无空格           sa111 空格无法替换　　　自动　 去除后面的空格   *  无需空格,就能自动触发
-------------------------------------------------------------------------------
   c
;      :c:　输入时需要区分大小写　　  :c:Gu::xxx   只有输入的是是Gu才能输出xxx　　gu　GU　gU　　都无法输出xxx

:C:BTW::  ; 输入所有大写字母.
:C:Btw::  ; 只有第一个字母输入大写字母.
: :btw::  ; 输入任何其他组合.
    case_conform_btw() {
        hs := A_ThisHotkey  ; 为了方便, 以防被打断.
        if (hs == ":C:BTW")
            Send BY THE WAY
        else if (hs == ":C:Btw")
            Send By the way
        else
            Send by the way
    }
return
;===============================
3种输出结果
btw               by the way
BTW             BY THE WAY
Btw               By the way
-------------------------------------------------------------------------------
   r
;      :r:　原样输出　:r:dc::{enter}　原样输出 {enter} 　而不会转义成按下回车
-------------------------------------------------------------------------------
   b0
;      :b0:              :b0:<li>::</li>{left 5}　　在输入内容后添加::后的内容　<li></li>

;      :b:              :b:<li>::</li>{left 5}　　输出 </li>　然后光标移至最左边　
-------------------------------------------------------------------------------
*/

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

:?*:9'::(){left}
:?*:0'::（）{left}				        ; 中文标点
:?*:-'::<>{left}

:?*:['::[]{left}
:?*:]'::{{}{}}{left}

:?*:u'::〔〕{left}				        ; 中文标点
:?*:i'::【】{left}				        ; 中文标点
:?*:o'::〖〗{left}				        ; 中文标点
:?*:p'::《》{left}				        ; 中文标点
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   `m::<br>  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 02-2368

:*:.``::。
:*:``.::……
:*:,``::，

:*::``::：
:*:`;``::；

:*:`/``::、  

:*?:``m::<br>
:*:m``:: •{space}
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   。，：；、 • ……    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 03 -2458


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

{
    ; F6 & R 红色        ;ROYGQBP WETUI
    F6 & r::b205("#f20c00")

    ; F6 & O 橙色                       
    F6 & o::b205("#ec6800")

; F6 & y 暗红色
    F6 & y::b205("#fff143")

; F6 & g 亮绿色
    F6 & g::b205("#00e500")

; F6 & q 兰绿色
    F6 & q::b205("#177cb0")

    ; F6 & B 浅蓝色
    F6 & b::b205("#44cef6")

; F6 & p 暗紫色
    F6 & p::b205("#b61aae")

; F6 & w 绿色
    F6 & w::b205("#bce672")

; F6 & e 绿色
    F6 & e::b205("#955539")

; F6 & t 兰绿色

    F6 & t::b205("#d7003a")

; F6 & u 深紫色
    F6 & u::b205("#ff0097")

; F6 & i 紫色
    F6 & i::b205("#ff461f")
}

; 快捷增加字体颜色
b205(s){
      clipboard := ""
    SendInput,^x
sleep,100
	clipboard = <span style="color: %s%; font-size:18px">%clipboard%</span>
 	SendInput {ctrl down}v{ctrl up}
	;Send {Left 7} ; 光标跟随到文本
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & O 橙色   joplin字体颜色  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 04 -2434

{
; F7 & q 兰绿色
    F7 & q::b204("#177cb0")

; F7 & w 绿色
    F7 & w::b204("#bce672")

; F7 & e 绿色
    F7 & e::b204("#955539")

; F7 & R 红色
    F7 & r::b204("#f20c00")

; F7 & t 兰绿色
    F7 & t::b204("#d7003a")

; F7 & y 暗红色
    F7 & y::b204("#fff143")

; F7 & u 深紫色
    F7 & u::b204("#ff0097")

; F7 & i 紫色
    F7 & i::b204("#ff461f")

; F7 & O 橙色      ; ORBPYGMST
    F7 & o::b204("#ec6800")

; F7 & p 暗紫色
    F7 & p::b204("#b61aae")

; F7 & B 浅蓝色
    F7 & b::b204("#44cef6")

; F7 & G 亮绿色
    F7 & g::b204("#00e500")
}

; 快捷增加字体颜色
b204(s){
      clipboard := ""
    SendInput,^x
sleep,100
	clipboard = <span style="font-family:KaiTi; font-size:30px; color: %s%">%clipboard%</span>
	SendInput {ctrl down}v{ctrl up}
	;Send {Left 7} ; 光标跟随到文本
}
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F7 & O 橙色   joplin字体颜色  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 05-2484

    ; F8 & q 兰绿色       ;   QWERTYUIOP  BG
    F8 & q::b203("#177cb0")

; F8 & w 绿色
    F8 & w::b203("#426666")

; F8 & e 绿色
    F8 & e::b203("#955539")

    ; F8 & R 红色
    F8 & r::b203("#f20c00")

; F8 & t 兰绿色
    F8 & t::b203("#d7003a")

; F8 & y 暗红色
    F8 & y::b203("#fff143")

; F8 & u 兰绿色
    F8 & u::b203("#ff0097")

; F8 & i 紫色
    F8 & i::b203("#ff461f")

    ; F8 & O 橙色
    F8 & o::b203("#ec6800")

; F8 & p 暗紫色
    F8 & p::b203("#b61aae")

    ; F8 & B 浅蓝色
    F8 & b::b203("#44cef6")

; F8 & g 暗绿色
    F8 & g::b203("#00e500")

; 快捷增加字体颜色
b203(s)
{
    clipboard := ""
    SendInput,^x
sleep,100
    SendInput, {TEXT}<span style="font-family:LiSu; font-size:24px; color: #2E3138; background: %s%">%clipboard%</span>
    Send {Left 25}{home}
}                                             ;  ------------------------------------- r t y o p     g b     m s
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F8 & O 橙色 Tyora 背景色    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 06 -2532

; F9 & q 兰绿色       ;   QWERTYUIOP  BG
    F9 & q::b202("#177cb0")

; F9 & w 绿色
    F9 & w::b202("#426666")

; F9 & e 绿色
    F9 & e::b202("#955539")

    ; F9 & R 红色
    F9 & r::b202("#f20c00")

; F9 & t 兰绿色
    F9 & t::b202("#d7003a")

; F9 & y 暗红色
    F9 & y::b202("#000000")

; F9 & u 兰绿色
    F9 & u::b202("#ff0097")

; F9 & i 紫色
    F9 & i::b202("#ff461f")

    ; F9 & O 橙色
    F9 & o::b202("#ec6800")

; F9 & p 暗紫色
    F9 & p::b202("#b61aae")

    ; F9 & B 浅蓝色
    F9 & b::b202("#44cef6")

; F9 & g 暗绿色
    F9 & g::b202("#00e500")

; 快捷增加字体颜色
b202(s)
{
   clipboard := ""
    SendInput ^x
sleep,100
          SendInput, {TEXT}<table><td bgcolor=%s%><font size = '4'></font>%clipboard%<td bgcolor=#2E3138></table>
a := "1"
;Send {Left 8}%a%{Left 20}{home}-{Space}
Send {Left 8}%a%{home}{up}-{Space}
}                                             ;  ------------------------------------- r t y o p     g b     m s
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F9 & O 橙色 Tyora 背景色    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 07-2582

F7 & 1::b201(12)
F7 & 2::b201(14)
F7 & 3::b201(16)
F7 & 4::b201(18)
F7 & 5::b201(20)
F7 & 6::b201(22)
F7 & 7::b201(24)

b201(size)
{
    clipboard := ""          ; 清空剪贴板
    SendInput ^x             ; 剪切选中的文本
    Sleep, 100               ; 等待剪贴板有内容
    ClipWait                 ; 等待剪贴板内容更新
    ; 设置新的剪贴板内容
    clipboard := "<span style='font-family: KaiTi; font-size: " size "pt;'>" clipboard "</span>"
    ; 等待剪贴板内容更新    color: #d7003a;
    ClipWait
    ; 粘贴新的内容
    SendInput ^v
    ; 光标左移 7 次
    Send {Left 7}
}
return
#IfWinActive
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F7 & 1-7  Tyora 字号    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 08-2609

;🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁  颜色  处理  🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁🎁
;👔👔👔👔👔👔👔👔👔👔👔  段落  处理  👔👔👔👔👔👔👔👔👔👔👔

#F2::
if (onoff := !onoff)
	{
	Send {home}
	}
else
	{
    	Send {end}
keywait, F2
}
 Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #F2 行首 行尾    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 09-2625

#F3::
if (onoff := !onoff)
	{
	Send #!{home}
	}
else
	{
    	Send #!{end}
keywait, F3
}
 Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  #F3 段首 段尾     ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 10 -2638

#F4::
if (onoff := !onoff)
	{
send, ^a{left}
	}
else
	{
send, ^a{right}
	keywait, F4
	}
 Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #F4 页首 页尾    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 11-2651

;👔👔👔👔👔👔👔👔👔👔👔  段落  处理  👔👔👔👔👔👔👔👔👔👔👔
;🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀  空行  处理  🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀🎀

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

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))                  ;---仅Typora  Joplin 

F6 & F1::
	clipboard := ""
    	SendInput,^x
	sleep,100
	clipboard = #  <span style="font-family:KaiTi; font-size:30px; color: #d7003a">%clipboard%</span>  [^0]   ; ------------- 12 握了请握  [^012] {left}
	SendInput {ctrl down}v{ctrl up}{home}{up}{right 2}
return
#If
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F1 标题添加序号等    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 001-2803 

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))
F6 & F2::
	send {space 2}
	clipboard = - [ ] <span style="color: #4c221b">确定已经掌握了请打上对勾！</span>
	SendInput {ctrl down}v{ctrl up}                      ; ------------- 确定已经掌握了请打上对勾！
return
#If
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F2 确定已经掌握了请打上对勾    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 002-2812 

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))

 F6 & F4::zaa()
	zaa()
{
	clipboard := ""
	Send ^x
	Sleep 500
	clipboard = <center>%clipboard%</center>
	Sleep 50
	Send ^v
}
return
#IfWinActive
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F4 Tyora 居中   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 003-2828

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))

F6 & F5::
	send >✌️ 
	sleep, 100
	send {enter}{bs}{enter}{left 2}
return
#If
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F5  > :v:    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 004-2838 

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))

F6 & F7::zc()
	zc()
{
	clipboard := ""
	Send ^x
	Sleep 500
	clipboard = ``%clipboard%``
	Sleep 50
	Send ^v
}
return
#If
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F7 Tyora 代码块   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 005-2854

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))

 F6 & F8::zb()
	 zb()
{
	clipboard := ""
	Send ^x
	Sleep 500
	clipboard = ^%clipboard%^
	Sleep 50
	Send ^v
}
return
#If
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F8 上标    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 006-2870

#If (WinActive("ahk_exe Typora.exe") or WinActive("ahk_exe Joplin.exe"))

 F6 & F9::zd()
	zd()
{
	clipboard := ""
	Send ^x
	Sleep 500
	clipboard = ~%clipboard%~
	Sleep 50
	Send ^v
}
return
#If
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F6 & F9 下标    ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 007-2886

;🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒  马克  文档  🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒🛒
;🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧  文档  序号  🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧

appskey & v::
    	if (!bzz)
        	bzz := "1"                           ; 如果变量 bzz 尚未初始化，则初始化为 "1"
    	SendInput, %bzz%.{space}
    	bzz++
     Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   appskey & b  1.2.3.到无穷   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 007-2886

appskey & b::
    if (!bz)
        bz := "a"                                    ; 如果变量 bz 尚未初始化，则初始化为 "a"
    SendInput, %bz%.{space}

    ; 字母递增逻辑                                 判断是否在 'a-z' 范围 ASCII码a-z 97-122
    if (StrLen(bz) == 1 && Asc(bz) >= 97 && Asc(bz) < 122) 
        bz := Chr(Asc(bz) + 1)  ; 递增到下一个字母
    else if (bz == "z")
        bz := "a"  ; 如果当前是 'z'，循环回到 'a'
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   appskey & b   a-z 循环   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 007-2886

appskey & n::
    if (!uz)
        uz := "A"                                    ; 如果变量 uz 尚未初始化，则初始化为 "A"
    SendInput, %uz%.{space}

    ; 字母递增逻辑                                 判断是否在 'a-z' 范围 ASCII码a-z 97-122
    if (StrLen(uz) == 1 && Asc(uz) >= 65 && Asc(uz) < 90) 
        uz := Chr(Asc(uz) + 1)  ; 递增到下一个字母
    else if (uz == "Z")
        uz := "A"  ; 如果当前是 'z'，循环回到 'a'
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   appskey & n  A-Z 循环   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 007-2886

;appskey & m::
    	if (!azz)
        	azz := "1"                           ; 如果变量 azz 尚未初始化，则初始化为 "1"
    	SendInput, %azz%.{space}
; 更新数字，如果超过9则重置为1
azz := (azz < 9) ? azz + 1 : 1
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   appskey & m 如果超过9则重置为1  ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 007-2886

;🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧  文档  序号  🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧🧧
/*
#MaxHotkeysPerInterval 200		         ; 设置的时间里, 不触发警告对话框情况下可以按下的热键最大数目.
scrollLines := 3  ; 设定初始滚动行数，避免未定义或负数

F5 & esc::  ; **每次增加 2**
    scrollLines += 2
    UpdateToolTip()
Return

F5 & F1::  ; **减少 3**
    scrollLines := Max(scrollLines - 3, 0)  ; 避免负数
    UpdateToolTip()
Return

; **测试当前 `scrollLines` 值**
F5 & F2::
    MsgBox, 当前滚动行数: %scrollLines%
Return

~WheelDown::
    MouseGetPos, xpos, ypos
    if (xpos >= 0 && xpos <= 15)
        SendInput {Volume_Down}
    else if (scrollLines > 0)
    {
        Loop, %scrollLines%
            MouseClick, WheelDown
    }
Return

~WheelUp::
    MouseGetPos, xpos, ypos
    if (xpos >= 0 && xpos <= 15)
        SendInput {Volume_Up}
    else if (scrollLines > 0)
    {
        Loop, %scrollLines%
            MouseClick, WheelUp
    }
Return

UpdateToolTip() {
    global scrollLines
    ToolTip, 当前滚动行数: %scrollLines%
    Sleep, 1000
    ToolTip
}
Return
*/

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 &Esc增加滚动行数 F5 & F1 减少 ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 007-3057

F1 & ESC::                                                       
    run, "D:\ahk1.0\Lib\0 tool\程序占用检测 V1.0.exe"
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F1 & esc  查看并终结进程   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 00000004-3237

XButton1::
send, ^]
return

XButton2::
run D:\ahk1.0\Lib\0 tool\kscrcap\kscrcap.exe
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   设置鼠标滚轮左右   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ       vless

F5 & ,::        ;  y.txt内    IPv6格式 [2A06:98C1:3122::CACE]    IPv4格式 104.17.111.246

originalText := "vless://612ffa24-0dde-4c05-8533-c8c48e25b433@1.1.1.1:2083?encryption=none&security=tls&sni=amkj.zc08.dpdns.org&fp=random&type=ws&host=amkj.zc08.dpdns.org&path=%2F%3Fed%3D2560%26PROT_TYPE%3Dvless%26PROXYIP%3Dproxyip.cmliussss.net#U"

;originalText := "vless://88f67d70-5a4f-4485-b983-c9caad714a48@1.1.1.1:2096?encryption=none&security=tls&sni=am.zcr4.ip-ddns.com&fp=randomized&type=ws&host=am.zcr4.ip-ddns.com&path=%2F%3Fed%3D2560%26PROXYIP%3Dts.hpc.tw#v5"
;originalText := "vless://dc6bf7b6-d00f-429d-bc97-1e27578fc52a@1.1.1.1:2087?encryption=none&security=tls&sni=Wbp.zcr05.V6.aRMy&alpn=http%2F1.1&fp=randomized&type=ws&host=wbp.zcr05.v6.army&path=%2FR4tUpvqfK3E6HBND%2FdHMuaHBjLnR3%3Fed%3D2560#v6"


    ; 读取 IP 列表文件
    ipList := []
    Loop, Read, y.txt
    {
        ipList.Push(A_LoopReadLine)  ; 逐行读取并存入数组
    }

    newText := ""  ; 存储最终文本

    ; 依次替换 IP
    for index, ip in ipList
    {
        newText .= StrReplace(originalText, "1.1.1.1", ip) . "`n"
    }

    ; 写入剪贴板
    Clipboard := RTrim(newText, "`n")
    ;MsgBox, 生成完成，已复制到剪贴板！
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & , 将 y.txt 中的IP替换为节点   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ     trojan

F5 & .::        ; trojan节点  y.txt内  IPv6格式 2A06:98C1:3122::CACE  IPv4格式 104.17.111.246

originalText := "trojan://zbb@1.1.1.1:443?security=tls&sni=t.zcr4.ip-ddns.com&fp=randomized&type=ws&host=t.zcr4.ip-ddns.com&path=%2F%3Fed%3D2560%26PROXYIP%3Dts.hpc.tw#T5"
;originalText := "trojan://zbb@1.1.1.1:2087?security=tls&sni=t.zcr4.ip-ddns.com&fp=randomized&type=ws&host=t.zcr4.ip-ddns.com&path=%2Fpyip%3Dts.hpc.tw#Tr4"
   
 ; 读取 IP 列表文件
    ipList := []
    Loop, Read, y.txt
    {
        ipList.Push(A_LoopReadLine)  ; 逐行读取并存入数组
    }

    newText := ""  ; 存储最终文本

    ; 依次替换 IP
    for index, ip in ipList
    {
        newText .= StrReplace(originalText, "1.1.1.1", ip) . "`n"
    }

    ; 写入剪贴板
    Clipboard := RTrim(newText, "`n")
    ;MsgBox, 生成完成，已复制到剪贴板！
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & . 将 y.txt 中的IP替换为节点   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  mihomo       yaml

; mihomo/订阅管理/右上角 +/x.yaml
;#Persistent
;#NoEnv
;SetTitleMatchMode, 2
;SetBatchLines, -1

F5 & /::
RunWait, "D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe" "D:\ahk1.0\yaml 模板.yaml"
Sleep, 1000
{
    ; 预定义原始文本模板
    originalText := "  - {name: 01, server: 1.1.1.1, port: 443, type: vless, uuid: a8dbc8e2-3d3e-4654-b028-b2382770a2d8, tls: true, tfo: false, skip-cert-verify: true, servername: yyyty.zbb25.filegear-sg.me, client-fingerprint: random, network: ws, ws-opts: {path: ""/?ed=2560"", headers: {Host: yyyty.zbb25.filegear-sg.me}}}"

    ipList := []
    index := 1

    ; 读取 y.txt 里的 IP 地址
    Loop, Read, y.txt
    {
        ipList[index] := A_LoopReadLine
        index++
    }

    newText := ""  ; 存储最终文本

    ; 依次替换 IP 和 Name
    for index, ip in ipList
    {
        tempText := StrReplace(originalText, "1.1.1.1", ip)  ; 替换 IP
        tempText := StrReplace(tempText, "name: 01", "name: " Format("{:02}", index))  ; name 递增
        newText .= tempText . "`n"
    }

    ; **保存到剪贴板**
    Clipboard := RTrim(newText, "`n")

    ; **自动替换 `XXXXoXXXXoo`**
    ReplaceClipboardText("XXXXoXXXXoo", Clipboard)

    ; **粘贴替换后的文本**
    Sleep, 100
    Send, ^v  

    ; **执行“另存为”**
    SaveToDesktop()

    return
}

ReplaceClipboardText(findText, replaceText)
{
    ; **检查剪贴板**
    if (replaceText = "") {
        MsgBox, 剪贴板为空，请先生成内容！
        return
    }

    ; **全选并复制文本**
    Clipboard := ""
    Send, ^a
    Sleep, 100
    Send, ^c
    ClipWait, 1
    if (Clipboard = "") {
        MsgBox, 未检测到文本，请确保当前窗口有可选内容！
        return
    }

    text := Clipboard ; 获取选中的文本
    newText := StrReplace(text, findText, replaceText)

    ; **检查是否替换成功**
    if (newText = text) {
        MsgBox, 未检测到 "%findText%" 需要替换！
        return
    }

    ; **更新剪贴板**
    Clipboard := newText
    return
}

SaveToDesktop()
{
    desktopPath := A_Desktop . "\x.yaml"
    
    ; 检查剪贴板内容
    if (Clipboard = "") {
        MsgBox, 剪贴板为空！
        return
    }

    ; 使用 FileDelete 删除原有文件（如果存在）
    if FileExist(desktopPath) {
        FileDelete, %desktopPath%
    }

    ; 使用 FileAppend 保存剪贴板内容，确保编码为 UTF-8
    FileEncoding, UTF-8
    FileAppend, %Clipboard%, %desktopPath%

    ; 检查文件是否成功创建
    if !FileExist(desktopPath)
    {
        MsgBox, 无法创建文件：%desktopPath%
        return
    }

    ;MsgBox, 文件已成功保存至桌面：%desktopPath%
}


/*
SaveToDesktop()
{
    desktopPath := A_Desktop . "\x.yaml"

    ; 以 UTF-8 无 BOM 方式写入
    FileDelete, %desktopPath%  ; 先删除旧文件
    FileAppend, %Clipboard%, %desktopPath%, UTF-8

    ; 检查文件是否成功创建
    if !FileExist(desktopPath)
    {
        MsgBox, 无法创建文件：%desktopPath%
        return
    }

    ;MsgBox, 文件已成功保存至桌面：%desktopPath%
}
*/
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & / 将 y.txt 中的IP替换为节点   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ            singbox

; D:\ahk1.0\singboxyyy.json                    提前准备好这个模板
; D:\ahk1.0\y.txt                                      提前准备好这个 IP地址文件
;D:\ahk1.0\Lib\0 tool\GUI.for.SingBox-windows-amd64\data\subscribes\ID_hmhx96r2.json  将生成的文件改名后粘贴至此
;D:\ahk1.0\Lib\0 tool\GUI.for.SingBox-windows-amd64\data\local\ID_hmhx96r2.json            将生成的文件再粘贴1份至此
;#NoEnv                           修改:SingBox/订阅/添加/本地文件/命名 abc 本地路径 data\local\ID_hmhx96r2.json 注意改文件名
;#SingleInstance Force

F5 & \::
	desktopPath := A_Desktop "\"  ; 获取桌面路径
	inputJson := "D:\ahk1.0\singboxyyy.json"  ; 源 JSON 文件
	inputTxt := "D:\ahk1.0\y.txt"  ; 包含 IP 地址的文本文件
	outputJson := desktopPath "data7local7www.json"                                ; 最终的合并 JSON 文件

; 检查文件是否存在
	if !FileExist(inputJson) {
	MsgBox, 错误：未找到 JSON 文件 "`n" inputJson "`n请检查文件路径。"
    	ExitApp
}
	if !FileExist(inputTxt) {
    	MsgBox, 错误：未找到 IP 地址文件 "`n" inputTxt "`n请检查文件路径。"
    	ExitApp
}

	ips := []
	Loop Read, %inputTxt%
{
    	line := Trim(A_LoopReadLine) 			       ; --------------------去掉首尾空格
    	if (line != "")				                    ; -------------------------过滤空行
        	ips.Push(line)
}

	if (ips.Length() = 0) {
    	MsgBox, 错误：IP 地址文件 "`n" inputTxt "`n为空或格式错误。"
    	ExitApp
}

	FileRead, jsonStr, %inputJson%
	if (jsonStr = "") {
    	MsgBox, 错误：无法读取 JSON 文件 "`n" inputJson "`n请检查文件是否为空或被占用。"
    	ExitApp
}

mergedJson := "["  ; 初始化 JSON 数组

	Loop % ips.Length() {
    	newTag := Format("{:02}", A_Index)  ; 生成 01, 02, 03...
    	newServer := ips[A_Index]

; 复制 jsonStr 以确保每次都是从原始 JSON 进行修改
    	jsonNew := jsonStr  

; 使用正则替换 "server" 和 "tag" 的值
    	jsonNew := RegExReplace(jsonNew, "i)(""server""\s*:\s*"")[^""]*("")", "$1" newServer "$2")
    	jsonNew := RegExReplace(jsonNew, "i)(""tag""\s*:\s*"")[^""]*("")", "$1" newTag "$2")

; 去掉 JSON 最外层的方括号 `[` 和 `]`
    	jsonNew := RegExReplace(jsonNew, "^\s*\[|\]\s*$", "")

; 添加到 `mergedJson`
    	if (A_Index > 1)  					       ; ---------------不是第一个就加 `,`
        	mergedJson .= ","
    	mergedJson .= jsonNew
}

mergedJson .= "]"  ; 结束 JSON 数组

; 删除旧文件（如果存在）
	if (FileExist(outputJson))
    	FileDelete, %outputJson%

; 写入合并后的 JSON 文件
	FileAppend, %mergedJson%, %outputJson%

; 检查是否成功创建
	if (FileExist(outputJson))
    	MsgBox, 成功生成合并 JSON 文件：`n"%outputJson%"
else
    	MsgBox, 错误：生成 JSON 文件失败，请检查权限或磁盘空间！
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 & \ 将 y.txt 中的IP替换为节点   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ singbox

F5 & '::           ;  2400:CB00:F00E:41C9:FFBC:D4E8:82BD:1616   不加 [ ]

{
originalText := "
(
{
  ""v"": ""2"",
  ""ps"": ""Vm2"",
  ""add"": ""172.67.163.102"",
  ""port"": ""30000"",
  ""id"": ""5aab3936-16d7-4377-8c33-0d77f2d295ee"",
  ""aid"": ""64"",
  ""scy"": ""auto"",
  ""net"": ""ws"",
  ""type"": ""none"",
  ""host"": ""www.14601176.xyz"",
  ""path"": ""/path/300022113329"",
  ""tls"": ""tls"",
  ""sni"": ""www.14601176.xyz"",
  ""alpn"": """",
  ""fp"": """"
}
)"


    ipList := []
    Loop, Read, y.txt
    {
        line := Trim(A_LoopReadLine)
        if (line != "")
            ipList.Push(line)
    }

    finalOutput := ""
    for index, ip in ipList
    {
        json := StrReplace(originalText, "172.67.163.102", ip)
        base64 := Utf8ToBase64(json)
        finalOutput .= "vmess://" . base64 . "`n"
    }

    Clipboard := RTrim(finalOutput, "`n")
    ;MsgBox, Operation completed! Results copied to clipboard.
}
return

Utf8ToBase64(s) {
    ; 1. Get UTF-8 byte length
    len := StrPut(s, "UTF-8") - 1
    
    ; 2. Allocate memory buffer
    VarSetCapacity(buf, len)
    
    ; 3. Convert string to UTF-8
    StrPut(s, &buf, len + 1, "UTF-8")
    
    ; 4. Base64 encoding
    return CryptBinaryToBase64(&buf, len)
}

CryptBinaryToBase64(ptr, len) {
    static CRYPT_STRING_BASE64 := 0x1
    DllCall("Crypt32.dll\CryptBinaryToStringA"
        , "Ptr", ptr
        , "UInt", len
        , "UInt", CRYPT_STRING_BASE64 | 0x40000000 ; CRYPT_STRING_NOCRLF
        , "Ptr", 0
        , "UInt*", size)
    
    VarSetCapacity(out, size * (A_IsUnicode ? 2 : 1))
    DllCall("Crypt32.dll\CryptBinaryToStringA"
        , "Ptr", ptr
        , "UInt", len
        , "UInt", CRYPT_STRING_BASE64 | 0x40000000
        , "Ptr", &out
        , "UInt*", size)
    
    return StrGet(&out, size, "CP0")
}
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   F5 &' 将 y.txt 中的IP替换为节点   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ vmess

F1 & h::
Run, "D:\ahk1.0\Lib\run_hidden.vbs", , Hide
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & h  更新Github dns   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 

+insert::
send, ^a
sleep, 400
send, ^r
return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ +insert  节点测速   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ

<^0::  
AutoTrim Off  ; 保留剪贴板中任何前导和尾随空白字符.
ClipboardOld := ClipboardAll
Clipboard := ""  ; 必须清空, 才能检测是否有效.
Send ^c
ClipWait 1
if ErrorLevel  ; ClipWait 超时.
    return
; 替换 CRLF 和/或 LF 为 `n 以便用于 "发送原始模式的" 热字串:
; 对其他任何在原始模式下可能出现问题
; 的字符进行相同的处理:
StringReplace, Hotstring, Clipboard, ``, ````, All  ; 首先进行此替换以避免和后面的操作冲突.
StringReplace, Hotstring, Hotstring, `r`n, ``r, All  ; 在 MS Word 等软件中中使用 `r 会比 `n 工作的更好.
StringReplace, Hotstring, Hotstring, `n, ``r, All
StringReplace, Hotstring, Hotstring, %A_Tab%, ``t, All
StringReplace, Hotstring, Hotstring, `;, ```;, All
Clipboard := ClipboardOld  ; 恢复剪贴板之前的内容.
; 这里会移动 InputBox 的光标到更人性化的位置:
SetTimer, MoveCaret, 10
; 显示 InputBox, 提供默认的热字串:
InputBox, Hotstring, New Hotstring, Type your abreviation at the indicated insertion point. You can also edit the replacement text if you wish.`n`nExample entry: :R:btw`::by the way,,,,,,,, :R:`::%Hotstring%
if ErrorLevel  ; 用户选择了取消.
    return
if InStr(Hotstring, ":R`:::")
{
    MsgBox You didn't provide an abbreviation. The hotstring has not been added.
    return
}
; 否则添加热字串并重新加载脚本:
FileAppend, `n%Hotstring%, %A_ScriptFullPath%  ; 在开始处放置 `n 以防文件末尾没有空行.
Reload
Sleep 200 ; 如果加载成功, reload 会在 Sleep 期间关闭当前实例, 所以永远不会执行到下面的语句.
MsgBox, 4,, The hotstring just added appears to be improperly formatted. Would you like to open the script for editing? Note that the bad hotstring is at the bottom of the script.
IfMsgBox, Yes, Edit
return

MoveCaret:
IfWinNotActive, New Hotstring
    return
; 否则移动 InputBox 中的光标到用户输入缩写的位置.
Send {Home}{Right 3}
SetTimer, MoveCaret, Off
return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  <^0  将选中文字转为热字符串   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ
```