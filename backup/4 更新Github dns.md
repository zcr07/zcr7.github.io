## 更新Github dns  



```

F1 & h::
Run, "D:\ahk1.0\Lib\run_hidden.vbs", , Hide
Return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  F1 & h  更新Github dns   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ 

```

## run_hidden.bat

```

@echo off
:: 提权判断（如果不是管理员则自我提权）
net session >nul 2>&1
if %errorlevel% neq 0 (
    powershell -Command "Start-Process -Verb runAs -WindowStyle Hidden -FilePath '%~f0'"
    exit /b
)

:: 执行 Git Bash 脚本，窗口隐藏
powershell.exe -WindowStyle Hidden -NoProfile -Command ^
    "& 'C:\Program Files\Git\git-bash.exe' -c '/d/ahk1.0/fetch_github_hosts'"

```

## run_hidden.vbs

```

set ws=WScript.CreateObject("WScript.Shell") 
ws.Run "run_hidden.bat",0


```

## fetch_github_hosts



```

_hosts=$(mktemp /tmp/hostsXXX)
hosts=/c/Windows/System32/drivers/etc/hosts
remote=https://gitlab.com/ineo6/hosts/-/raw/master/next-hosts
reg='/# GitHub520 Host Start/,/# Github520 Host End/d'

sed "$reg" $hosts > "$_hosts"
curl "$remote" >> "$_hosts"
cat "$_hosts" > "$hosts"

rm "$_hosts"


```













