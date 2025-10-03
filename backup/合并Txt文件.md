## 合并Txt文件

#### 需要先进入需合并文件的文件夹

```

F5 & h::
    ; 获取当前活动窗口（可能是资源管理器）
    WinGetClass, class, A
    if (class = "CabinetWClass") || (class = "ExploreWClass") ; 资源管理器
    {
        ; 尝试获取资源管理器当前路径
        for window in ComObjCreate("Shell.Application").Windows
        {
            try
            {
                if (window.hwnd = WinExist("A"))
                {
                    targetFolder := window.Document.Folder.Self.Path
                    break
                }
            }
        }
    }
    
    if !targetFolder
    {
        ; 如果无法获取资源管理器路径，回退到选择文件
        FileSelectFile, selectedFile, 1, , 请选择一个txt文件, *.txt
        if (selectedFile = "")
            return
        SplitPath, selectedFile, , targetFolder
    }
    
    ; 检查目标目录是否有txt文件
    FileCount := 0
    Loop, Files, %targetFolder%\*.txt
    {
        FileCount++
        break
    }
    
    if (FileCount = 0)
    {
        MsgBox, 在目录 %targetFolder% 中未找到txt文件
        return
    }
    
    Run, powershell.exe -Command "Set-Location '%targetFolder%'; Get-Content *.txt -Raw | Set-Content 111.txt -Encoding utf8",, Hide
    MsgBox, 文件合并完成！结果保存在：%targetFolder%\111.txt
return

;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & h  合并当前目录下所有的txt ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ

```

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#### 此脚本运行后，会找寻要合并的文件夹

```

F5 & n::
    ; 让用户选择包含txt文件的文件夹
    FileSelectFolder, selectedFolder, , 3, 请选择包含txt文件的文件夹
    if (selectedFolder = "")
        return
    
    ; 在选定的文件夹中执行PowerShell命令
    Run, powershell.exe -Command "Set-Location '%selectedFolder%'; Get-Content *.txt -Raw | Set-Content 111.txt -Encoding utf8",, Hide
    ;MsgBox, 文件合并完成！结果保存在：%selectedFolder%\111.txt
return

```

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:00:32.png" style="width:400px;"></p><br> 


PowerShell  进入文件夹，执行：

```

Get-Content *.txt | Set-Content 111.txt

```

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:01:12.png" style="width:400px;"></p><br> 


如果文件比较大，建议：


```

Get-Content *.txt -Raw | Out-File 111.txt -Encoding utf8 

```

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:02:13.png" style="width:400px;"></p><br> 

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:03:09.png" style="width:400px;"></p><br>










