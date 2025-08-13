## upgit.exe

- config.toml 配置文件如下

- D:\ahk1.0\Lib\0 tool\picgo-croe\config.toml

```
rename = "im8/{month}.{day}:{hour}:{minute}:{second}{ext}"
default_uploader = "github"
[replacements]
"raw.githubusercontent.com" = "cdn.jsdelivr.net/gh"
"/main" = "@main"

[output_formats]
"bbcode" = "[img]{url}[/img]"
"html" = '<img src="{url}" />'
"markdown" = "![]({url})"
"ccc" = '<p align="center"><img src="{url}" style="width:400px;"></p><br>'

[uploaders.github]
# 保存文件的分支，例如 master 或 main
branch = "main"
pat = "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"
repo = "img"
username = "zb9678"


```

## 上传脚本

```
LWin::return
#t::

Run, "D:\ahk1.0\Lib\0 tool\ScreenCapture\ScreenCapture.exe", , , pid    ; pid: 这是一个变量名，作用: 执行 kscrcap.exe 并将它的进程 ID 保存到变量 pid 中。
    	Process, WaitClose, %pid%, 30              ; --等待进程关闭，最长 30 秒

; 确认是否上传
    	MsgBox, 4,, 请在完成截图和编辑后点击“是”确认上传图片。
    	IfMsgBox, No
        	return  ; 选择“否”则退出

; 上传图片
    	Run, D:\ahk1.0\Lib\0 tool\picgo-croe\upgit.exe :clipboard -o clipboard -f ccc, , hide
    return
; Process: 这是 AutoHotkey 的另一个命令，用于处理与进程相关的操作。
; WaitClose: 这是 Process 命令的一个子命令，表示等待指定进程关闭。
; %pid%: 这里引用了上一步存储在 pid 变量中的进程 ID。% 是 AHK 中用于表示变量内容的语法。
; 30: 这是等待的时间（以秒为单位）。如果进程提前关闭，脚本会立即继续，而无需等待满 30 秒。

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

```