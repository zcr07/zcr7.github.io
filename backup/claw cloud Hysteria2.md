## Hysteria2节点搭建

```

###  ---------------新建 App Launchpad----------------  01

hy3

snowdreamtech/frps:0.59

21114   udp://   udp.us-east-1.clawcloudrun.com:To be allocated

Local Storage   /data

###  ----------------进入终端根目录------------------  02

1.查询ip（根目录状态下）： 需新建窗口，仅操作这一次

 👉  Switched to namespace ns-qs4ycm6u
root@(ns-qs4ycm6u) ~$ curl -s ip.sb
47.90.175.227
root@(ns-qs4ycm6u) ~$ 

###  ----------------进入终端应用程序状态----------- 03

2.进入data（应用程序状态下）： 换回原先窗口

cd data

3.下载linux版hysteria2程序

wget https://github.com/apernet/hysteria/releases/download/app%2Fv2.6.1/hysteria-linux-amd64

4.给程序增加执行权限：

chmod +x hysteria-linux-amd64

5.创建CRT证书：

openssl genrsa -out hy2.key 2048

6.创建密钥：

openssl req -new -x509 -key hy2.key -out hy2.crt -days 36500

###  ----------------打开最右侧文件夹图标------------------- 04

上传（注意文件上传后的大小不为0   134.00 B） 
server.yaml
注意第一行冒号跟端口号之间无空格；其余每一行冒号后面都有一个空格

listen: :21115
speedTest: true
tls: 
  cert: hy2.crt
  key: hy2.key
  sniGuard: disable
auth:
  type: password
  password: zb

###  --------------应用程序状态-------------------- 05

8.启动server.yaml服务端：

./hysteria-linux-amd64 server -c server.yaml

###  ---------------V2ray操作-------------------- 06

手动添加V2ray的 Hysteria2 节点

hy3
47.90.175.227
46051
zb

开启 tls
true
--------------------------------------------------


====================================================
sh: bash: not found
ash: cd: can't cd to dta: No such file or directory
/ # cd data
/data # wget https://github.com/apernet/hysteria/releases/download/app%2Fv2.6.1/hysteria-linux-amd64
--2025-05-07 12:58:12--  https://github.com/apernet/hysteria/releases/download/app%2Fv2.6.1/hysteria-linux-amd64
Resolving github.com (github.com)... 140.82.113.3
Connecting to github.com (github.com)|140.82.113.3|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/257434373/f91793a3-a0fc-491d-a26e-3c873d818721?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250507%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250507T125812Z&X-Amz-Expires=300&X-Amz-Signature=56b97075ffabe5d3c4cfeccaddda5e9d48409740a7225b4415670ee89bcaf447&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dhysteria-linux-amd64&response-content-type=application%2Foctet-stream [following]
--2025-05-07 12:58:12--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/257434373/f91793a3-a0fc-491d-a26e-3c873d818721?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20250507%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20250507T125812Z&X-Amz-Expires=300&X-Amz-Signature=56b97075ffabe5d3c4cfeccaddda5e9d48409740a7225b4415670ee89bcaf447&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3Dhysteria-linux-amd64&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.109.133, 185.199.110.133, 185.199.108.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.109.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 18796696 (18M) [application/octet-stream]
Saving to: 'hysteria-linux-amd64'

hysteria-linux-amd64                100%[==========================>]  17.93M  44.5MB/s    in 0.4s    
2025-05-07 12:58:12 (44.5 MB/s) - 'hysteria-linux-amd64' saved [18796696/18796696]

/data # chmod +x hysteria-linux-amd64
/data # openssl genrsa -out hy2.key 2048
/data # openssl req -new -x509 -key hy2.key -out hy2.crt -days 36500
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:
State or Province Name (full name) [Some-State]:
Locality Name (eg, city) []:
Organization Name (eg, company) [Internet Widgits Pty Ltd]:
Organizational Unit Name (eg, section) []:
Common Name (e.g. server FQDN or YOUR name) []:
Email Address []:
/data # ./hysteria-linux-amd64 server -c server.yaml
2025-05-07T13:02:39Z    INFO    server mode
2025-05-07T13:02:39Z    INFO    server up and running   {"listen": ":21115"}
2025-05-07T13:04:13Z    INFO    client connected        {"addr": "172.16.0.190:50362", "id": "user", "tx": 0}
2025-05-07T13:04:44Z    INFO    client disconnected     {"addr": "172.16.0.190:50362", "id": "user", "error": "accepting stream failed: timeout: no recent network activity"}

=====================================================
```