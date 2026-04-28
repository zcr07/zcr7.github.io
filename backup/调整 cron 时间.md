
## 方案一：调整 cron 时间 设置为早上7:00运行

- cron: "0 23 * * *"

- 这个时间默认不是北京时间，它表示的是服务器系统时区的早上 7:00。

- UTC = 北京时间 - 8   (往前推8个小时)

- 23:00  向后增加 8个小时  即准备设置成的运行时间 7:00




```

name: Daily CF App Start

on:
  schedule:
    # UTC时间23:00 = 北京时间次日07:00
    - cron: "0 23 * * *"
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


##   方案二：设置时区环境变量

- cron: "0 7 * * *"

-  TZ: Asia/Shanghai  # 关键设置：指定时区为北京时间

如果你的服务器特意设置为亚洲/上海（Asia/Shanghai）时区，那么系统时间就是北京时间。

在这种情况下，0 7 * * * 就是北京时间的早上 7 点。



```

name: Daily CF App Start

on:
  schedule:
    # 这个7点会被TZ时区设置解释为北京时间07:00
    - cron: "0 7 * * *"
  workflow_dispatch:   # 支持手动触发

jobs:
  run-cf:
    runs-on: ubuntu-latest
    env:
      TZ: Asia/Shanghai  # 关键设置：指定时区为北京时间

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

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/09.15:08:47:37.png" style="width:400px;"></p><br>












