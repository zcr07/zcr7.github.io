## 发邮件send.py

- https://www.youtube.com/watch?v=hfx7ywW0QR4

## resend.com的设置如下 

- https://resend.com/api-keys

## API Keys

`re_NmeuQ3z2_CzwXAgo9fCEH2r2c7PRwoBQL`

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/09.02:22:43:50.png" style="width:400px;"></p><br>

## Domains

添加  `zcr7.xx.kg`

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/09.02:22:44:43.png" style="width:400px;"></p><br>

cF中设置完，记着点击 I've .....

## CF 设置

- https://dash.cloudflare.com/5e13acfeb51991ab52af94da59e959a2/zcr7.xx.kg/dns/records

DNS设置

MX  send   feedback-smtp.ap-northeast-1.amazonses.com   10
TXT send   v=spf1 include:amazonses.com ~all
TXT resend._domainkey  
p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCwkcyBszlJzCJ7HDLY26BOr66tYpKoTo9RToVigIPqgqSy262B78WHW5pVvVmSIEN4fxJISUSMXTwT5EjIkWBMS3NeaJl5+lFKy7TuvngBy2FvcQABOM0j/0IeerTbnbtqfamCnbw1i8cbqlLv/P/NEBLbpKaKkoGL3HVM/bOffQIDAQAB

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/09.02:22:48:03.png" style="width:400px;"></p><br>


## resend.com的设置

Emails
右上角  </> API

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/09.02:22:46:59.png" style="width:400px;"></p><br>


send.py 文件内容如下 

```
import resend

# 设置API密钥
resend.api_key = "re_NmeuQ3z2_CzwXAgo9fCEH2r2c7PRwoBQL"

# 邮件内容和格式设置
params: resend.Emails.SendParams = {
    "from": "zb@zcr7.xx.kg",
    "to": ["zcr071225@gmail.com", "zkkev53@gmail.com"],
    "subject": "2025年10月07日",
	"html": r"""
    <html>
    <head>
        <meta charset="UTF-8">
        <style>
            h1 {
                color: #d7003a;
            }
            pre {
                font-size: 20px;
                background-color: #1e1e1e;
                color: #0078D4;
                padding: 15px;
                border-radius: 8px;
                line-height: 1.6;
                white-space: pre-wrap; /* 防止长行超出 */
            }
        </style>
    </head>
    <body>
        <h1>C女士，您好！ </h1>
	<pre>
        🍀 PowerShell 7.5.3
        🍀 PS C:\Users\z\Desktop> pip install resend
        🍀 需要先安装支持
         <p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.05:01:02:59.png" style="width:700px;"></p>
        💥 重要！
        💥 切记！
	</pre>
    </body>
    </html>
    """
}

# 发送邮件
email = resend.Emails.send(params)

# 打印邮件发送的结果
print(email)

```

## 注意：需要安装python

- 微软商店安装 


## 进入CMD  安装依赖

`pip install resend `                                       

##说明：

tt@zcr7.xx.kg   因为zcr7.xx.kg被添加到了自定义域，所以名字为任意  比如：qwfasdfahh@zcr7.xx.kg 也可以。