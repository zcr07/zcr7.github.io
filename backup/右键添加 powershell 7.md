## 右键添加 (管理员) powershell 7

#### 右键菜单 目录背景

HKEY_LOCAL_MACHINE\SOFTWARE\Classes\Directory\background\shell

默认

(管理员) PowerShell 7 

Position

Bottom

Icon

C:\Program Files\PowerShell\7\pwsh.exe

---------------------------------------------------------------------------------

command

"C:\Program Files\PowerShell\7\pwsh.exe" -NoExit -WorkingDirectory "%V"


=================================================

#### 右键菜单 文件夹图标

HKEY_CLASSES_ROOT\Directory\shell\PowerShell7Admin\command

默认

(管理员) PowerShell 7 

Position

Top

Icon

C:\Program Files\PowerShell\7\pwsh.exe

-----------------------------------------------------------------------------------------

command

powershell -Command "Start-Process 'pwsh' -Verb RunAs -WorkingDirectory '%1'"

<br><br><br><br>


＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆＆


## 右键添加  powershell 7

#### 右键菜单 目录背景

HKEY_LOCAL_MACHINE\SOFTWARE\Classes\Directory\background\shell

默认

PowerShell 7 

Position

Bottom

Icon

C:\Program Files\PowerShell\7\pwsh.exe

---------------------------------------------------------------------------------

command

pwsh.exe -noexit -WorkingDirectory "%V"


=================================================

#### 右键菜单 文件夹图标

HKEY_CLASSES_ROOT\Directory\shell\PowerShell7Admin\command

默认

PowerShell 7 

Position

Top

Icon

C:\Program Files\PowerShell\7\pwsh.exe

-----------------------------------------------------------------------------------------

command

pwsh.exe -noexit -WorkingDirectory "%1"



<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:16:42:07.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:16:43:07.png" style="width:400px;"></p><br>



















