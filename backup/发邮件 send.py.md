## 发邮件send.py

- https://www.youtube.com/watch?v=hfx7ywW0QR4

## resend.com的设置如下 

- https://resend.com/api-keys

## API Keys

`re_NmeuQ3z2_CzwXAgo9fCEH2r2c7PRwoBQL`

## Domains

添加  `zcr7.xx.kg`

cF中设置完，记着点击 I've .....

## CF 设置

- https://dash.cloudflare.com/5e13acfeb51991ab52af94da59e959a2/zcr7.xx.kg/dns/records

DNS设置

MX  send   feedback-smtp.ap-northeast-1.amazonses.com   10
TXT send   v=spf1 include:amazonses.com ~all
TXT resend._domainkey  
p=MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCwkcyBszlJzCJ7HDLY26BOr66tYpKoTo9RToVigIPqgqSy262B78WHW5pVvVmSIEN4fxJISUSMXTwT5EjIkWBMS3NeaJl5+lFKy7TuvngBy2FvcQABOM0j/0IeerTbnbtqfamCnbw1i8cbqlLv/P/NEBLbpKaKkoGL3HVM/bOffQIDAQAB

## resend.com的设置

Emails
右上角  </> API

send.py文件内容如下 

```
import resend
resend.api_key = "re_NmeuQ3z2_CzwXAgo9fCEH2r2c7PRwoBQL"
params: resend.Emails.SendParams = {
  "from": "tt@zcr7.xx.kg",
  "to": ["zcr071225@gmail.com", "zkkev53@gmail.com"],
  "subject": "例子（1）",
  "html": """
        <h2>以下是代码内容：</h2>                 
        <pre>
⭐ 发送命令：/newbot
        </pre>        
              """
}
email = resend.Emails.send(params)
print(email)

```

## 注意：需要安装python

- 微软商店安装 


## 进入CMD  安装依赖

`pip install resend `                                       

##说明：

tt@zcr7.xx.kg   因为zcr7.xx.kg被添加到了自定义域，所以名字为任意  比如：qwfasdfahh@zcr7.xx.kg 也可以。