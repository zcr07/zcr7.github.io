## 合并N个 txt 文件

shift+右键文件夹  选 PowerShell

## 进入 txt 文件夹，执行：

`Get-Content *.txt | Set-Content 111.txt`


## 如果文件比较大，建议：

`Get-Content *.txt -Raw | Out-File 111.txt -Encoding utf8`

===================================================

##  批处理文件

- 合并txt.bat  放到txt文件夹中。

```
@echo off
chcp 65001 >nul   :: 设置编码为 UTF-8（防止中文路径乱码）
setlocal enabledelayedexpansion

:: 输出文件名
set output=merged.txt

:: 如果已存在，先删除
if exist "%output%" del "%output%"

echo 正在合并当前目录下的所有 txt 文件...

:: 遍历当前目录下的 txt 文件
for %%f in (*.txt) do (
    echo 正在处理: %%f
    type "%%f" >> "%output%"
    echo. >> "%output%"   :: 每个文件后加一行空行
)

echo.
echo 合并完成！生成文件：%output%
pause

```



