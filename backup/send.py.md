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
  "from": "1@zcr9.qzz.io",
  "to": ["zyy7031@gmail.com"],
  "subject": "例子（11）",
    "html": """
        <h2>以下是示例代码：</h2>
        <pre>
为什么这样写？

&lt;pre&gt; ... &lt;/pre&gt;：会保留空格、缩进、换行，非常适合展示代码。
    
    <!-- <pre> ... </pre>：会保留空格、缩进、换行，非常适合展示代码。 -->

    "from": "dddddd@zcr9.qzz.io",
    
    "to": ["zyy7031@gmail.com"],
    
    "subject": "ok",
    
    "html": \"\"\"
    
    点击<a href="https://chatgpt.com/c/688f348d-701c-8325-ac7e-d4a85681f421">这里</a>查看更多。
        </pre>
            """
}

email = resend.Emails.send(params)
print(email)

```
















