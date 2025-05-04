## 批量复制粘贴工具

```
global MyClipData
global page
*>!q:: 批量复制粘贴工具()
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
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ art+q 批量复制粘贴   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 4-216
```