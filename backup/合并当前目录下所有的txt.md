## 合并当前目录下所有的txt

```

F5 & h::
    ; 获取当前活动窗口
    WinGetClass, class, A
    if (class = "CabinetWClass") || (class = "ExploreWClass") 
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
Run, pwsh.exe -NoProfile -Command "Set-Location '%targetFolder%'; (Get-Content *.txt -Raw) -join '`r`n' | Set-Content 111.txt -Encoding utf8",, Hide

return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F5 & h  合并当前目录下所有的txt ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ

```



<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.07:14:52:54.png" style="width:400px;"></p><br>