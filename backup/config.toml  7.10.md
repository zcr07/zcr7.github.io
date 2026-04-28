## config.toml

###  私库

```
rename = "images/{month}.{day}:{hour}:{minute}:{second}{ext}"
default_uploader = "github"
[replacements]
"raw.githubusercontent.com" = "node1.zcr3.ddns-ip.net"

# "raw.githubusercontent.com" = "node1.k07.dpdns.org"
# "raw.githubusercontent.com" = "node1.r08.dpdns.org"
# "raw.githubusercontent.com" = "node1.z07.cloudns.be"
# "raw.githubusercontent.com" = "node1.z07.dpdns.org"
# "raw.githubusercontent.com" = "node1.zb25.x10.mx"
# "raw.githubusercontent.com" = "node1.zb9.ip-ddns.com"
# "raw.githubusercontent.com" = "node1.zbb06.filegear-sg.me"
# "raw.githubusercontent.com" = "node1.zcr3.ddns-ip.net"
# "raw.githubusercontent.com" = "node1.zcr5.qzz.io"

[output_formats]
"ccc" = '<p align="center"><img src="{url}" style="width:400px;"></p><br>'

[uploaders.github]
# 保存文件的分支，例如 master 或 main
branch = "main"
pat = "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"
repo = "node-1"
username = "zb9678"


```

### 公开库

```
rename = "im1/{month}.{day}:{hour}:{minute}:{second}{ext}"
default_uploader = "github"
[replacements]
"raw.githubusercontent.com" = "cdn.jsdelivr.net/gh"
"/main" = "@main"

[output_formats]
"bbcode" = "[img]{url}[/img]"
"html" = '<img src="{url}" />'
"markdown" = "![]({url})"
"ccc" = '<p align="center"><img src="{url}" style="width:400px;"></p><br>'

[uploaders.github]
# 保存文件的分支，例如 master 或 main
branch = "main"
pat = "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"
repo = "img9"
username = "zb9678"


```






