## 安装 PowerShell 7+ 的方法

### 方法一：用 Winget（推荐，最简单）

如果你的 Windows 里已经有 winget 包管理器（Win10 / Win11 默认带有）：
在命令提示符或 PowerShell 输入：

```

winget install --id Microsoft.Powershell --source winget

```

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:18:19.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:20:06.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:19:32.png" style="width:400px;"></p><br>


### 方法二：手动下载安装

https://github.com/PowerShell/PowerShell/releases

PowerShell-7.x.x-win-x64.msi

下载并安装，安装时建议勾选：

✅ 添加到 PATH

✅ 在 Windows Terminal 中注册

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:24:48.png" style="width:400px;"></p><br>

## 验证版本

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:26:20.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im3/10.03:13:28:22.png" style="width:400px;"></p><br>

Windows PowerShell 5.1（系统自带），这个版本已经停更了。要用 -Join 这种新参数，需要安装 PowerShell 7+（也叫 PowerShell Core）。













