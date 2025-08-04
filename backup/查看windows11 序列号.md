## 查看windows11 序列号

VK7JG-NPHTM-C97JM-9MPGT-3V66T
DNH2Q-2FBYM-RJCVH-XDP3D-JHV8X
VK7JG-NPHTM-C97JM-9FDEY-3V66T
DNH2Q-3HBYM-RJCVH-XDP3R-JHV8X


打开regedit 打开如下位置

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\SoftwareProtectionPlatform

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/08.04:23:04:12.png" style="width:400px;"></p><br>

## PowerShell

输入如下内容

` (Get-WmiObject –query ‘select * from SoftwareLicensingService’).OA3xOriginalProductKey  `

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img9@main/im2/08.04:23:19:32.png" style="width:400px;"></p><br>
