## 教程
https://www.youtube.com/watch?v=PGWiaf48xvU&t=394s

## 准备
SAP 官网：https://www.sap.com
临时邮箱：https://mail.cx/zh/
短信接码平台：https://lubansms.com
Cloud Foundry CLi 命令行客户端：
https://github.com/cloudfoundry/cli/releases
UUID 在线生成网站：
https://tooltool.net/zh/uuid
BTP 一键启动脚本：
https://github.com/xiaolin-007/clash/blob/main/%E5%90%AF%E5%8A%A8BTP.bat 

## BTP 主控室
https://account.hanatrial.ondemand.com/trial/#/globalaccount/3c0b83f7-7a61-4728-b4ca-4b88a7a38751/subaccount/28c3a741-d187-4f84-96af-2482304eb6eb/subaccountoverview

## 1. 登录美国
cf login -a https://api.cf.us10-001.hana.ondemand.com

登录新加坡
cf login -a https://api.cf.ap21.hana.ondemand.com
zkkev53@gmail.com
@Zb

2. 应用名 ak17
cf push ak17 --docker-image ghcr.io/uncleluogithub/mous:latest -m 512M --health-check-type port

打开dev  可看到ak17

3. 设置 UUID
cf set-env ak17 UUID 858b09b4-d8c3-432f-8fd2-92716de15554

4. 固化配置并重建
cf restage ak17

5) 查看生成的节点
cf logs ak17 --recent

https://account.hanatrial.ondemand.com/trial/#/globalaccount/3c0b83f7-7a61-4728-b4ca-4b88a7a38751/subaccount/28c3a741-d187-4f84-96af-2482304eb6eb/subaccountoverview

## 新加坡
vmess://ewogICJ2IjogIjIiLAogICJwcyI6ICLmsrnnrqHpopHpgZPvvJrogIHnvZflj5Tlj5TvvZxTQVAtVlBO55u06L+e54mIIiwKICAiYWRkIjogImFrMTcuY2ZhcHBzLmFwMjEuaGFuYS5vbmRlbWFuZC5jb20iLAogICJwb3J0IjogIjQ0MyIsCiAgImlkIjogIjg1OGIwOWI0LWQ4YzMtNDMyZi04ZmQyLTkyNzE2ZGUxNTU1NCIsCiAgImFpZCI6ICIwIiwKICAic2N5IjogImF1dG8iLAogICJuZXQiOiAid3MiLAogICJ0eXBlIjogIm5vbmUiLAogICJob3N0IjogImFrMTcuY2ZhcHBzLmFwMjEuaGFuYS5vbmRlbWFuZC5jb20iLAogICJwYXRoIjogIi9sYW9sdW8iLAogICJ0bHMiOiAidGxzIgp9
美国
vmess://ew0KICAidiI6ICIyIiwNCiAgInBzIjogIjAwMCDmsrnnrqHpopHpgZPvvJrogIHnvZflj5Tlj5TvvZxTQVAtVlBO55u06L+e54mIIiwNCiAgImFkZCI6ICJuZzcuY2ZhcHBzLnVzMTAtMDAxLmhhbmEub25kZW1hbmQuY29tIiwNCiAgInBvcnQiOiAiNDQzIiwNCiAgImlkIjogIjEyN2I4MDFjLTRkN2EtNDQ0ZS04Y2M1LTFiOGI5ZDJhODI2YiIsDQogICJhaWQiOiAiMCIsDQogICJzY3kiOiAiYXV0byIsDQogICJuZXQiOiAid3MiLA0KICAidHlwZSI6ICJub25lIiwNCiAgImhvc3QiOiAibmc3LmNmYXBwcy51czEwLTAwMS5oYW5hLm9uZGVtYW5kLmNvbSIsDQogICJwYXRoIjogIi9sYW9sdW8iLA0KICAidGxzIjogInRscyIsDQogICJzbmkiOiAiIiwNCiAgImFscG4iOiAiIiwNCiAgImZwIjogIiINCn0=

https://account.hanatrial.ondemand.com/trial/#/globalaccount/536a48fb-34aa-4321-8546-83fd0e40ed43/subaccount/caef4323-d894-4749-928d-f66565d17aae/subaccountoverview
Cloud Foundry 环境
API Endpoint:  https://api.cf.ap21.hana.ondemand.com
Org Name:  c9395869trial

## 保活  BTP.bat

```
@echo off
set CF_API=https://api.cf.ap21.hana.ondemand.com
set CF_USERNAME=zkkev53@gmail.com
set CF_PASSWORD=@Zb
set CF_ORG=c9395869trial
set CF_SPACE=dev
set CF_APP=ak17
echo === Login to Cloud Foundry ===
cf api %CF_API% --skip-ssl-validation
cf auth %CF_USERNAME% %CF_PASSWORD%
cf target -o %CF_ORG% -s %CF_SPACE%

echo === Try to start app ===
cf start %CF_APP%

if %errorlevel% neq 0 (
    echo Failed to start app. Trying restart...
    cf restart %CF_APP%
)

echo === Done ===

```

## 保活   BTPus.bat


```

@echo off
set CF_API=https://api.cf.us10-001.hana.ondemand.com
set CF_USERNAME=ngro1031@gmail.com
set CF_PASSWORD=@Zb
set CF_ORG=405a27abtrial
set CF_SPACE=dev
set CF_APP=ng7
echo === Login to Cloud Foundry ===
cf api %CF_API% --skip-ssl-validation
cf auth %CF_USERNAME% %CF_PASSWORD%
cf target -o %CF_ORG% -s %CF_SPACE%

echo === Try to start app ===
cf start %CF_APP%

if %errorlevel% neq 0 (
    echo Failed to start app. Trying restart...
    cf restart %CF_APP%
)

echo === Done ===

```


##  BTPus.vbs 同时启动2个bat

···

Set zz = CreateObject("WScript.Shell")

' 运行 BTPus.bat
zz.Run """D:\ahk1.0\Lib\6\BTPus.bat""", 0, False

' 运行 BTP.bat
zz.Run """D:\ahk1.0\Lib\6\BTP.bat""", 0, False



' 参数解释

' 0 = 隐藏运行（不弹出黑窗口）

' False = 不等待执行完成，两个批处理会同时运行

' True = 等待前一个执行完，再执行下一个

' 如果你希望 先执行完 BTPus.bat，再执行 BTP.bat，就把第一个改成：

' zz.Run """D:\ahk1.0\Lib\6\BTPus.bat""", 0, True


' 这样 BTPus.bat 完成后才会执行 BTP.bat。

···

========================================================

## .github/workflows/sync.yml  新建启动文件


https://github.com/zyy200712/asp


···

name: Daily CF App Start

on:
  schedule:
    # 每天北京时间 08:00 执行（UTC = 北京时间 - 8）
    - cron: "0 0 * * *"
  workflow_dispatch:   # 支持手动触发

jobs:
  run-cf:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Install Cloud Foundry CLI
        run: |
          sudo apt-get update
          sudo apt-get install -y wget
          wget -q -O cf-cli.deb "https://packages.cloudfoundry.org/stable?release=debian64&source=github"
          sudo dpkg -i cf-cli.deb
          cf --version

      - name: Login to Cloud Foundry
        env:
          CF_API: https://api.cf.ap21.hana.ondemand.com
          CF_USERNAME: ${{ secrets.CF_USERNAME }}
          CF_PASSWORD: ${{ secrets.CF_PASSWORD }}
          CF_ORG: c9395869trial
          CF_SPACE: dev
        run: |
          cf api $CF_API --skip-ssl-validation
          cf auth "$CF_USERNAME" "$CF_PASSWORD"
          cf target -o "$CF_ORG" -s "$CF_SPACE"

      - name: Start App
        env:
          CF_APP: ak17
        run: |
          cf start "$CF_APP" || cf restart "$CF_APP"

···


## 说明

定时任务

cron: "0 1 * * *" = 每天 UTC 01:00 → 北京时间 09:00。

如果你想改到北京时间 08:00，就写 0 0 * * *。

Secrets 设置
在 GitHub 仓库 → Settings → Secrets → Actions 添加：

CF_USERNAME = zkkev53@gmail.com

CF_PASSWORD = @Zb

运行逻辑

先 cf start app

如果失败（可能是已经运行过），就 cf restart app


## .github/workflows/sync.yml  新建启动文件


https://github.com/zyy200712/asp2


```

name: Daily CF App Start

on:
  schedule:
    # 每天北京时间 08:00 执行（UTC = 北京时间 - 8）
    - cron: "0 0 * * *"
  workflow_dispatch:   # 支持手动触发

jobs:
  run-cf:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repo
        uses: actions/checkout@v4

      - name: Install Cloud Foundry CLI
        run: |
          sudo apt-get update
          sudo apt-get install -y wget
          wget -q -O cf-cli.deb "https://packages.cloudfoundry.org/stable?release=debian64&source=github"
          sudo dpkg -i cf-cli.deb
          cf --version

      - name: Login to Cloud Foundry
        env:
          CF_API: https://api.cf.us10-001.hana.ondemand.com
          CF_USERNAME: ${{ secrets.CF_USERNAME }}
          CF_PASSWORD: ${{ secrets.CF_PASSWORD }}
          CF_ORG: 405a27abtrial
          CF_SPACE: dev
        run: |
          cf api $CF_API --skip-ssl-validation
          cf auth "$CF_USERNAME" "$CF_PASSWORD"
          cf target -o "$CF_ORG" -s "$CF_SPACE"

      - name: Start App
        env:
          CF_APP: ng7
        run: |
          cf start "$CF_APP" || cf restart "$CF_APP"

```

Secrets 设置
在 GitHub 仓库 → Settings → Secrets → Actions 添加：

CF_USERNAME = ngro1031@gmail.com

CF_PASSWORD = @Zb

=========================================================





