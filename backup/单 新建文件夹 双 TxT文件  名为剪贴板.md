## 单 新建文件夹 双 TxT文件  名为剪贴板

```
 >^b::
if wincc_presses > 0 ; SetTimer 已经启动, 所以我们记录键击.
{
    wincc_presses += 1
    return
}
; 否则, 这是新开始系列中的首次按下. 把次数设为 1 并启动
; 计时器：
wincc_presses = 1
SetTimer, Keywincc, 300 ; 在 400 毫秒内等待更多的键击.
return

Keywincc:
SetTimer, Keywincc, off
if wincc_presses = 1 ; 此键按下了一次.
{
   Click right
sleep,200
Send, wf
Clipboard= %Clipboard%
sleep,200
send,{ctrl down}v{ctrl up}
ClipWait
send, {enter}
}
else if wincc_presses = 2 ; 此键按下了两次.
{
   Click right
sleep,200
Send, w{up 1}{enter}                                            ; 调整新建压缩包还是txt
Clipboard= %Clipboard%
sleep,200
send,{ctrl down}v{ctrl up}
ClipWait
send, {enter}
}
wincc_presses = 0
return
;ΞΞΞΞΞΞΞΞΞΞΞΞ   >^b  单 新建文件夹 双 TxT文件  名为剪贴板    ΞΞΞΞΞΞΞΞΞΞΞΞΞ 06-373
```