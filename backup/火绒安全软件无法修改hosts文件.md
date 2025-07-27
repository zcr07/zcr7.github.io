##  火绒安全软件无法修改hosts文件

- https://bbs.huorong.cn/forum.php?mod=viewthread&action=printable&tid=141158

## 管理员运行power shell

```
$manifest = (Get-AppxPackage Microsoft.WindowsNotepad).InstallLocation + '\AppxManifest.xml' ; Add-AppxPackage -DisableDevelopmentMode -Register $manifest
```

OK  !!!