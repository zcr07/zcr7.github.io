## 使用python脚本发送邮件

  [教程](https://www.youtube.com/watch?v=hfx7ywW0QR4)

## 邮件服务  resend.com

-  https://resend.com/domains

### 创建API

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:43:22.png" style="width:400px;"></p><br>

###  添加域名如下

- zcr9.qzz.io

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:41:41.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:39:55.png" style="width:400px;"></p><br>

### 托管到CF

- https://resend.com/domains/b95e9d84-fa80-487b-b64d-2ce267537f8a

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:38:34.png" style="width:400px;"></p><br>

MX             send            feedback-smtp.ap-northeast-1.amazonses.com             10  

TXT             send            v=spf1 include:amazonses.com ~all 

TXT            resend._domainkey          p=MIGfMA0GCSqGSIb3DQEBAQUAA4

### 将以上3条填入CF的DNS记录中

- https://dash.cloudflare.com/5e13acfeb51991ab52af94da59e959a2/zcr9.qzz.io/dns/records

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:37:32.png" style="width:400px;"></p><br>

## 编写python脚本

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:47:02.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:48:48.png" style="width:400px;"></p><br>

### 脚本修改如下  send.py

```
import resend

resend.api_key = "re_btprifPM_GKtJH6v9fA7uNt5pEECUwrw8"

params: resend.Emails.SendParams = {
  "from": "1@zcr9.qzz.io",
  "to": ["zyy7031@gmail.com"],
  "subject": "好吧",
  "html": "<p>我一会儿就回</p>"
}

email = resend.Emails.send(params)
print(email)

```

## 利用ahk脚本发送邮件

```
F1 & p:: 
           Run, python "D:\ahk1.0\send.py", , Hide
return

```

## 编辑 send.py

```
F1 & s::
	o=D:\ahk1.0\Lib\0 tool\EmEditor-24.5.3-x64\EmEditor.exe

	1=D:\ahk1.0\Lib\0 tool\picgo-croe\config.toml
	2=C:\Users\z\.picgo\config.json
	3=D:\ahk1.0\Lib\ahk777.ahk
	4=D:\ahk1.0\Ahk3.ahk
        5=D:\ahk1.0\send.py

	Run,%o% "%1%" "%2%" "%3%" "%4%" "%5%"
return
```

##  收到的邮件

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im1/08.02:15:51:34.png" style="width:400px;"></p><br>

=========================================================================================













