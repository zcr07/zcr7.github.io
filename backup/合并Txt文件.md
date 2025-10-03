

## 合并Txt文件

PowerShell  进入文件夹，执行：

```

Get-Content *.txt | Set-Content 111.txt

```


如果文件比较大，建议：


```

Get-Content *.txt -Raw | Out-File 111.txt -Encoding utf8 

```