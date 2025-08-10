## 发送邮件 send.py

```
F1 & p:: 
Run, python "D:\ahk1.0\send.py", , Hide
return

```

## 编辑send.py

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


## send.py

```
import resend

resend.api_key = "re_btprifPM_GKtJH6v9fA7uNt5pEECUwrw8"

params: resend.Emails.SendParams = {
  "from": "tt@zcr9.qzz.io",
  "to": ["zyy7031@gmail.com", "zcr071@jhb.edu.kg", "kevinzh@zmkk.edu.kg", "zcr007@zmkk.edu.kg"],
  "subject": "例子（28）",
  "html": """
        <h2>以下是邮件内容：7行星号：</h2>       
             
        <pre>

⭐ 创建电报机器人获取Bot_Token：@BotFather

⭐ 发送命令：/newbot

⭐ 获取创建的频道Chat_ID：@VersaToolsBot

⭐ 环境变量名称：TG_Bot_Token

⭐ 环境变量值：您在@BotFather获取到的Bot_Token

⭐ 环境变量名称：TG_Chat_ID

⭐ 环境变量值：您在@VersaToolsBot获取到的CHAT_ID

        </pre>
        
              """
}

email = resend.Emails.send(params)
print(email)

```


## 注意：

` """ `  邮件内容中要加 ` \ `            `  \"\"\"  `

`  <xxx>  `                                     `&lt;xxx&gt;`


<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/08.10:19:13:38.png" style="width:400px;"></p><br>

## 获取 re_btprifPM_GKtJH6v9fA7uNt5pEECUwrw8


resend.api_key = "re_btprifPM_GKtJH6v9fA7uNt5pEECUwrw8"

- https://resend.com/api-keys

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/08.10:18:58:49.png" style="width:400px;"></p><br>

## 添加自定义域

- https://resend.com/domains

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/08.10:18:57:08.png" style="width:400px;"></p><br>





