##  picgo-core

-  config.json 配置文件如下

- C:\Users\z\.picgo\config.json

```
{
  "picBed": {
    "current": "github",
    "uploader": "github",
    "smms": {
      "token": ""
    },
    "list": [
      {
        "type": "smms",
        "name": "SM.MS",
        "visible": false
      },
      {
        "type": "github",
        "name": "GitHub",
        "visible": true
      }
    ],
    "github": {
      "_configName": "node-1",
      "repo": "zcr07/node-1",
      "branch": "main",
      "token": "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",
      "path": "imgss/",
      "customUrl": "https://cdn.jsdelivr.net/gh/zcr07/node-1@main",
      "_id": "dc6c8cac-b260-49d1-b260-8832960dd53d",
      "_createdAt": 1732321803260,
      "_updatedAt": 1733281530319
    }
  },
  "settings": {
    "shortKey": {
      "picgo:upload": {
        "enable": true,
        "key": "CommandOrControl+Shift+P",
        "name": "upload",
        "label": "QUICK_UPLOAD"
      }
    },
    "showUpdateTip": false,
    "autoStart": false,
    "autoRename": true,
    "encodeOutputURL": false,
    "privacyEnsure": true,
    "pasteStyle": "URL"
  },
  "needReload": false,
  "picgoPlugins": {
    "picgo-plugin-compress-next": true,
    "picgo-plugin-autocopy": true,
    "picgo-plugin-gitlab-files": true
  },
  "picgo-plugin-compress-next": {
    "Compress Type": "tinypng",
    "Gif compress Type": "webp-converter",
    "Auto Refresh TinyPng Key Across Months": true,
    "TinyPng API Key": "scHQZ2CmlQDdRJnMQ9SjXKVfByCwY3YD"
  },
  "uploader": {
    "github": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "d4b75295-a443-4075-ad2e-73caf72e078c",
          "_createdAt": 1730352070049,
          "_updatedAt": 1730352070049
        },
        {
          "_configName": "img",
          "repo": "zcr07/img",
          "branch": "main",
          "path": "images/",
          "customUrl": "https://ing.w07.us.kg",
          "token": "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",
          "_id": "9b921d00-95f0-47dd-9524-aea7e9ec70e4",
          "_createdAt": 1730352442411,
          "_updatedAt": 1731836528133
        },
        {
          "_configName": "node-1",
          "repo": "zcr07/node-1",
          "branch": "main",
          "token": "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",
          "path": "imgss/",
          "customUrl": "https://node1.zbb25.filegear-sg.me",
          "_id": "dc6c8cac-b260-49d1-b260-8832960dd53d",
          "_createdAt": 1732321803260,
          "_updatedAt": 1733281530319
        },
        {
          "_configName": "node-2",
          "path": "imgss/",
          "customUrl": "https://node2.zbb25.filegear-sg.me",
          "token": "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",
          "branch": "main",
          "repo": "zcr07/node-2",
          "_id": "f2e24856-c89e-4f09-9ef8-670e975cbb5d",
          "_createdAt": 1732321905575,
          "_updatedAt": 1732321905575
        },
        {
          "_configName": "node-3",
          "repo": "zcr07/node-3",
          "branch": "main",
          "token": "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",
          "path": "imgss/",
          "customUrl": "https://node3.zbb25.filegear-sg.me",
          "_id": "00642892-c82e-4b88-b522-37bb09467a17",
          "_createdAt": 1732321935850,
          "_updatedAt": 1732321935850
        }
      ],
      "defaultId": "dc6c8cac-b260-49d1-b260-8832960dd53d"
    }
  },
  "picgo-plugin-autocopy": {
    "template": "Custom",
    "customLink": "<p align='center'><img src=\"$url\" style='width:400px;'><br><br>"
  }
}

```

##  上传脚本

```
#Persistent
#u::

	clipboard := "" 
	Send, ^c
	Sleep, 100  ; 等待剪贴板更新

	filePath := Clipboard  ; 获取剪贴板内容
	if (!FileExist(filePath))
       {
   	 MsgBox, 16, 错误, 剪贴板内容无效，请复制文件后再试。
    	return
      }

	RunWait, cmd /c picgo u "%filePath%", , Hide
	MsgBox, 文件上传完成！
    return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #u  上传剪贴板中的文件   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  000005-2051

#i::

    	Run, "D:\ahk1.0\Lib\0 tool\ScreenCapture\ScreenCapture.exe", , , pid
    	Process, WaitClose, %pid%, 30  ; 等待进程关闭，最长 30 秒

; 确认是否上传
    	MsgBox, 4,, 请在完成截图和编辑后点击“是”确认上传图片。

    	IfMsgBox, No                                         ;---------------选择“否”则退出
        	return             

; 上传图片
    	RunWait, cmd /c "picgo u",, hide
    return
;ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ   #i  上传截图到github/img   ΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞΞ  000002-2000

```






















