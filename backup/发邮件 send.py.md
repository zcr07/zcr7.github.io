## 发邮件 send.py


重要须知：
 
1.首先要安装python

2.cmd运行  pip install resend

Microsoft Windows [版本 10.0.26100.6584]
(c) Microsoft Corporation。保留所有权利。

C:\Users\z>pip install resend
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: resend in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (2.17.0)
Requirement already satisfied: requests>=2.31.0 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from resend) (2.32.5)
Requirement already satisfied: typing-extensions>=4.4.0 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from resend) (4.15.0)
Requirement already satisfied: charset_normalizer<4,>=2 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (3.4.4)
Requirement already satisfied: idna<4,>=2.5 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (3.11)
Requirement already satisfied: urllib3<3,>=1.21.1 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (2.5.0)
Requirement already satisfied: certifi>=2017.4.17 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (2025.10.5)

[notice] A new release of pip is available: 25.2 -> 25.3
[notice] To update, run: C:\Users\z\AppData\Local\Microsoft\WindowsApps\PythonSoftwareFoundation.Python.3.13_qbz5n2kfra8p0\python.exe -m pip install --upgrade pip

如显示以上内容红色部分，需要先安装如下蓝色部分

C:\Users\z>C:\Users\z\AppData\Local\Microsoft\WindowsApps\PythonSoftwareFoundation.Python.3.13_qbz5n2kfra8p0\python.exe -m pip install --upgrade pip
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: pip in c:\program files\windowsapps\pythonsoftwarefoundation.python.3.13_3.13.2544.0_x64__qbz5n2kfra8p0\lib\site-packages (25.2)
Collecting pip
  Downloading pip-25.3-py3-none-any.whl.metadata (4.7 kB)
Downloading pip-25.3-py3-none-any.whl (1.8 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 1.8/1.8 MB 4.3 MB/s  0:00:00
Installing collected packages: pip
  WARNING: The scripts pip.exe, pip3.13.exe and pip3.exe are installed in 'C:\Users\z\AppData\Local\Packages\PythonSoftwareFoundation.Python.3.13_qbz5n2kfra8p0\LocalCache\local-packages\Python313\Scripts' which is not on PATH.
  Consider adding this directory to PATH or, if you prefer to suppress this warning, use --no-warn-script-location.
Successfully installed pip-25.3

显示成功后，再重新运行如下

C:\Users\z>pip install resend
Defaulting to user installation because normal site-packages is not writeable
Requirement already satisfied: resend in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (2.17.0)
Requirement already satisfied: requests>=2.31.0 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from resend) (2.32.5)
Requirement already satisfied: typing-extensions>=4.4.0 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from resend) (4.15.0)
Requirement already satisfied: charset_normalizer<4,>=2 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (3.4.4)
Requirement already satisfied: idna<4,>=2.5 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (3.11)
Requirement already satisfied: urllib3<3,>=1.21.1 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (2.5.0)
Requirement already satisfied: certifi>=2017.4.17 in c:\users\z\appdata\local\packages\pythonsoftwarefoundation.python.3.13_qbz5n2kfra8p0\localcache\local-packages\python313\site-packages (from requests>=2.31.0->resend) (2025.10.5)

C:\Users\z>

到此就成功了，可以发信了。

=========================================================================

send.py  分别为2个帐号的内容


https://resend.com/domains/e9722895-14e3-49f1-84df-1e8abec98182      zk
zcr7.xx.kg

---------------------------------------------------------------------------------
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

# 注意：如无法发送，需要 1.先安装python，2. cmd运行 pip install resend 

------------------------------------------------------------------------------------


https://resend.com/domains/67bf865f-1e6e-45f4-bd30-16ded5a818e1     zcr
zcr7.qzz.io

------------------------------------------------------------------------------------

import resend

# 设置API密钥
resend.api_key = "re_FgeyySdD_FxoTNeimCAsacyzSFg7GgZef"

# 邮件内容和格式设置
params: resend.Emails.SendParams = {
    "from": "3@zcr7.qzz.io",
    "to": ["zcr071225@gmail.com", "zkkev53@gmail.com"],
    "subject": "2025年10月27日",
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
        <h1>S先生，您好！ </h1>
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

------------------------------------------------------------------------------------





















