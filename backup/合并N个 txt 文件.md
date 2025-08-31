## 合并N个 txt 文件

shift+右键文件夹  选 PowerShell

## 进入 txt 文件夹，执行：

`Get-Content *.txt | Set-Content 111.txt`


## 如果文件比较大，建议：

`Get-Content *.txt -Raw | Out-File 111.txt -Encoding utf8`