

## 合并Txt文件

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










