# 搜索  IPV4  IPV6  域名

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im4/02.18:12:45:12.png" style="width:400px;"></p><br> 

```

; 搜索IPv6
:*?:6'::                                        ; SendRaw  原样发送所有字符，不处理特殊符号
    SendRaw, (\w+:)+(\w+):+(\w+:)+(\w+)
sleep, 200
send, {enter}
return

; :*?:6r::(\w{+}:)`+(\w{+})`::(\w{+}:)`+(\w{+})


:*?:4'::                                          ; 搜索 IPv4
SendRaw, \b(?:(?:25[0-5]|2[0-4]\d|1\d{2}|[1-9]?\d)\.){3}(?:25[0-5]|2[0-4]\d|1\d{2}|[1-9]?\d)\b
Sleep, 200
Send, {Enter}
Return


; 搜索域名
:*?:y'::                                        ; SendRaw  原样发送所有字符，不处理特殊符号
    SendRaw, \b(?:[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?\.)+[a-zA-Z]{2,}\b
sleep, 200
send, {enter}
return

; 搜索x和y区间的内容，不包括 x y
:*?:b'::                                                  ; 把 X 替换为开始字符，Y 替换为结束字符。如@和？之间（？要转义\?）  @\K.*?(?=\?)
    SendRaw, (?<=x)(\d+)(?=y)
return                                      

 ; 搜索x和y区间的内容，并且包括 x y
:*?:h'::                                                  ; 把 X 替换为开始字符，Y 替换为结束字符。如@和？之间（？要转义\?）  @\K.*?(?=\?)
    SendRaw, x[^y]*y
return                                                  ; x[^y]*y  [^y]* 是一个字符集，表示 不包含  y 的任何字符。

```