##  火绒安全软件无法修改hosts文件

- https://bbs.huorong.cn/forum.php?mod=viewthread&action=printable&tid=141158

## 管理员运行power shell

```
$manifest = (Get-AppxPackage Microsoft.WindowsNotepad).InstallLocation + '\AppxManifest.xml' ; Add-AppxPackage -DisableDevelopmentMode -Register $manifest
```

这条 PowerShell 命令的作用是 重新注册并修复 Windows 记事本（Notepad）应用。

`Get-AppxPackage Microsoft.WindowsNotepad`
获取当前用户安装的 Notepad 应用的包信息（这是 UWP 应用的一种）。

`.InstallLocation`
获取该应用的安装目录路径。

`+ '\AppxManifest.xml'`
在该目录下拼接出 AppxManifest.xml 的完整路径。这个 XML 是 UWP 应用的配置清单，定义了应用的元数据、权限等。


## 作用：使用应用清单重新注册记事本程序，让它恢复到正常状态。常用于：

- 记事本无法启动

- 记事本图标丢失

- 系统应用损坏

