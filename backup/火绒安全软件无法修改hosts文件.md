##  火绒安全软件无法修改hosts文件

- https://bbs.huorong.cn/forum.php?mod=viewthread&action=printable&tid=141158

## 管理员运行power shell

```
$manifest = (Get-AppxPackage Microsoft.WindowsNotepad).InstallLocation + '\AppxManifest.xml' ; Add-AppxPackage -DisableDevelopmentMode -Register $manifest
```

这条 PowerShell 命令的作用是 重新注册并修复 Windows 记事本（Notepad）应用。