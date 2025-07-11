## config.json

### 如剪贴板中已显示有链接，但此链接却打开错误

- 有链接显示，证明图片已上传至Github，链接打开显示错误则证明cloufare中的worker.js中的Token出了问题 。
  
- 应更换 `CloudFlare` 的worker.js  中的第12行中的 Token 。   

CF位置

- zb9  billowing-morning-node123

- https://dash.cloudflare.com/67409d2d85f857acbae76bd86edbe9fc/workers/services/edit/billowing-morning-node123/production

注：具体脚本在  `config.json 7.10  补充worker.js`

- https://github.com/zcr07/zcr7.github.io/issues/39

<p align='center'><img src="https://node1.zcr5.qzz.io/images/20250711105632.png" style='width:400px;'><br><br>


===================================================================


###  如果上传后，剪贴板中无内容

- 则应更换 `config.json` 中的 Token  


### picgo core

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
      "_configName": "node-3",
      "repo": "zb9678/node-3",
      "branch": "main",
      "token": "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",
      "path": "images/",
      "customUrl": "https://node1.zcr5.qzz.io",
      "_id": "545107ed-f91a-4665-8732-e1666c42ccca",
      "_createdAt": 1751677919508,
      "_updatedAt": 1751677919508
    },
    "transformer": "compress-next",
    "gitlab-files-uploader": {
      "_configName": "2411",
      "gitUrl": "https://gitlab.com",
      "projectId": "64778826",
      "branch": "main",
      "gitToken": "glpat-fc-zZtmnhwccnLnbJUBd",
      "fileName": "im/{fileName}",
      "commitMessage": "Upload {fileName} By PicGo gitlab files uploader at {year}-{month}-{day}",
      "_id": "456e8667-44e8-41a5-847b-6942c65f9756",
      "_createdAt": 1732375929167,
      "_updatedAt": 1732375966064,
      "gitVersionUnderThirteen": null,
      "deleteRemote": null,
      "deleteMessage": null,
      "deleteInform": null,
      "authorMail": null,
      "authorName": null
    },
    "aws-s3": {
      "_configName": "zcr071225",
      "accessKeyID": "005171e1ce22c070000000001",
      "secretAccessKey": "K005zX/ZFPp9yMBgRBR42iCuh0lETAA",
      "bucketName": "zcr071225",
      "uploadPath": "files/{fileName}.{extName}",
      "endpoint": "https://s3.us-east-005.backblazeb2.com",
      "_id": "c9350f54-fb5c-41d5-aa6a-f53801c3efae",
      "_createdAt": 1733450557313,
      "_updatedAt": 1733461500299,
      "region": null,
      "proxy": null,
      "urlPrefix": "https://cdn.jsdelivr.net/gh",
      "urlSuffix": "",
      "pathStyleAccess": false,
      "rejectUnauthorized": true,
      "acl": "",
      "disableBucketPrefixToURL": false
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
    "pasteStyle": "URL",
    "customLink": ""
  },
  "needReload": false,
  "picgoPlugins": {
    "picgo-plugin-compress-next": true,
    "picgo-plugin-autocopy": true,
    "picgo-plugin-gitlab-files": true,
    "picgo-plugin-s3": true,
    "picgo-plugin-custom-uploader-fix": true
  },
  "picgo-plugin-compress-next": {
    "Compress Type": "webp-converter",
    "Gif compress Type": "webp-converter",
    "Auto Refresh TinyPng Key Across Months": true,
    "TinyPng API Key": ""
  },
  "uploader": {
    "github": {
      "configList": [
        {
          "_configName": "img",
          "repo": "zcr07/img",
          "branch": "main",
          "path": "images/",
          "customUrl": "https://cdn.jsdelivr.net/gh/zcr07/img@main",
          "token": "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",
          "_id": "9b921d00-95f0-47dd-9524-aea7e9ec70e4",
          "_createdAt": 1730352442411,
          "_updatedAt": 1748072188413
        },
        {
          "_configName": "node-1",
          "repo": "zb9678/node-1",
          "branch": "main",
          "token": "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",
          "path": "images/",
          "customUrl": "https://node1.zcr5.qzz.io",
          "_id": "ce0eed96-9c41-4470-a462-328e028af4d7",
          "_createdAt": 1751677748671,
          "_updatedAt": 1751677748671
        },
        {
          "_configName": "node-2",
          "repo": "zb9678/node-2",
          "branch": "main",
          "token": "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",
          "path": "images/",
          "customUrl": "https://node1.zcr5.qzz.io",
          "_id": "f594113f-9721-40b4-8726-b2795aee0b5e",
          "_createdAt": 1751677888728,
          "_updatedAt": 1751677888728
        },
        {
          "_configName": "node-3",
          "repo": "zb9678/node-3",
          "branch": "main",
          "token": "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",
          "path": "images/",
          "customUrl": "https://node1.zcr5.qzz.io",
          "_id": "545107ed-f91a-4665-8732-e1666c42ccca",
          "_createdAt": 1751677919508,
          "_updatedAt": 1751677919508
        }
      ],
      "defaultId": "a6f7484a-d0c2-4c63-8f9d-66a77b93cf09"
    },
    "gitlab-files-uploader": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "dc3bf286-6209-4748-bfc6-e1a61327ebaa",
          "_createdAt": 1732375525821,
          "_updatedAt": 1732375525821
        },
        {
          "_configName": "2411",
          "gitUrl": "https://gitlab.com",
          "projectId": "64778826",
          "branch": "main",
          "gitToken": "glpat-fc-zZtmnhwccnLnbJUBd",
          "fileName": "im/{fileName}",
          "commitMessage": "Upload {fileName} By PicGo gitlab files uploader at {year}-{month}-{day}",
          "_id": "456e8667-44e8-41a5-847b-6942c65f9756",
          "_createdAt": 1732375929167,
          "_updatedAt": 1732375966064,
          "gitVersionUnderThirteen": null,
          "deleteRemote": null,
          "deleteMessage": null,
          "deleteInform": null,
          "authorMail": null,
          "authorName": null
        }
      ],
      "defaultId": "456e8667-44e8-41a5-847b-6942c65f9756"
    },
    "aws-s3": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "f11fb1f3-7b77-4dee-9cfd-dea20b39b579",
          "_createdAt": 1733450209143,
          "_updatedAt": 1733450209143
        },
        {
          "_configName": "zcr071225",
          "accessKeyID": "005171e1ce22c070000000001",
          "secretAccessKey": "K005zX/ZFPp9yMBgRBR42iCuh0lETAA",
          "bucketName": "zcr071225",
          "uploadPath": "files/{fileName}.{extName}",
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "_id": "c9350f54-fb5c-41d5-aa6a-f53801c3efae",
          "_createdAt": 1733450557313,
          "_updatedAt": 1733461500299,
          "region": null,
          "proxy": null,
          "urlPrefix": "https://cdn.jsdelivr.net/gh",
          "urlSuffix": "",
          "pathStyleAccess": false,
          "rejectUnauthorized": true,
          "acl": "",
          "disableBucketPrefixToURL": false
        }
      ],
      "defaultId": "c9350f54-fb5c-41d5-aa6a-f53801c3efae"
    }
  },
  "picgo-plugin-autocopy": {
    "template": "Custom",
    "customLink": "<p align='center'><img src=\"$url\" style='width:400px;'><br><br>"
  }
}
```

============================================================

### picgo

- C:\Users\z\AppData\Roaming\picgo\data.json

```
{
  "picBed": {
    "current": "aws-s3-own",
    "uploader": "aws-s3-own",
    "smms": {
      "token": ""
    },
    "list": [
      {
        "type": "tcyun",
        "name": "腾讯云COS",
        "visible": false
      },
      {
        "type": "aliyun",
        "name": "阿里云OSS",
        "visible": false
      },
      {
        "type": "smms",
        "name": "SM.MS",
        "visible": false
      },
      {
        "type": "github",
        "name": "GitHub",
        "visible": false
      },
      {
        "type": "qiniu",
        "name": "七牛云",
        "visible": false
      },
      {
        "type": "imgur",
        "name": "Imgur",
        "visible": false
      },
      {
        "type": "upyun",
        "name": "又拍云",
        "visible": false
      },
      {
        "type": "custom-uploader-fix",
        "name": "自定义API图床",
        "visible": false
      },
      {
        "type": "gitlab-files-uploader",
        "name": "gitlab files 图片上传",
        "visible": false
      },
      {
        "type": "aws-s3",
        "name": "Amazon S3",
        "visible": false
      },
      {
        "type": "aws-s3-own",
        "name": "Amazon S3 Own",
        "visible": true
      },
      {
        "type": "web-uploader",
        "name": "自定义Web图床",
        "visible": false
      }
    ],
    "github": {
      "_configName": "node-1",
      "repo": "zb9678/node-1",
      "branch": "main",
      "token": "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",
      "path": "images/",
      "customUrl": "https://node1.zcr5.qzz.io",
      "_id": "ce0eed96-9c41-4470-a462-328e028af4d7",
      "_createdAt": 1751677748671,
      "_updatedAt": 1751727401443
    },
    "transformer": "compress-next",
    "gitlab-files-uploader": {
      "_configName": "img2",
      "gitUrl": "https://gitlab.com",
      "projectId": "71398858",
      "branch": "main",
      "gitToken": "glpat-5m2X_ZUDsYh13CuBegbc",
      "fileName": "images/{fileName}",
      "commitMessage": "Upload {fileName} By PicGo gitlab files uploader at {year}-{month}-{day}",
      "_id": "443bbf8b-e6c9-488f-a4e0-91a88f56db04",
      "_createdAt": 1751785982309,
      "_updatedAt": 1751786021347,
      "gitVersionUnderThirteen": null,
      "deleteRemote": null,
      "deleteMessage": null,
      "deleteInform": null,
      "authorMail": null,
      "authorName": null
    },
    "aws-s3": {
      "_configName": "kevzcr-1",
      "accessKeyID": "005171e1ce22c070000000006",
      "secretAccessKey": "K005eVKFoFB9rhcd60PYp2flle/Elp4",
      "bucketName": "kevzcr1",
      "uploadPath": "images/{fileName}.{extName}",
      "_id": "64a0b7e8-8b21-46e0-8b93-f9648064deec",
      "_createdAt": 1751806119663,
      "_updatedAt": 1751885918283,
      "region": null,
      "endpoint": "https://s3.us-east-005.backblazeb2.com",
      "proxy": "",
      "rejectUnauthorized": false,
      "acl": "",
      "pathStyleAccess": false,
      "outputURLPattern": "",
      "urlPrefix": null,
      "urlSuffix": "",
      "disableBucketPrefixToURL": false
    },
    "custom-uploader-fix": {
      "_configName": "Default",
      "_id": "1301fd83-33f1-4c1c-9d99-6673199d2d07",
      "_createdAt": 1748073081029,
      "_updatedAt": 1748073081029
    },
    "proxy": "",
    "aws-s3-own": {
      "_configName": "kevzcr 3",
      "endpoint": "http://s3.us-east-005.backblazeb2.com",
      "uploadPath": "images/{fileName}.{extName}",
      "secretAccessKey": "K005bV0nxzCqoS8WO4Ajj54CZZ8jRvk",
      "accessKeyID": "005e634d18d70550000000001",
      "bucketName": "kevzcr3",
      "_id": "4fb61a1e-abcc-404d-a148-69c3ab8df16e",
      "_createdAt": 1752024843867,
      "_updatedAt": 1752025625630,
      "trimmedUploadPath": "{year}{month}/original/{md5}.{extName}",
      "region": null,
      "proxy": null,
      "urlPrefix": null,
      "urlSuffix": "",
      "pathStyleAccess": false,
      "rejectUnauthorized": false,
      "acl": "",
      "disableBucketPrefixToURL": false
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
    "pasteStyle": "Custom",
    "customLink": "https://node1.zcr5.qzz.io/images/$fileName$extName",
    "uploadNotification": false,
    "npmProxy": "",
    "npmRegistry": ""
  },
  "needReload": false,
  "picgoPlugins": {
    "picgo-plugin-compress-next": true,
    "picgo-plugin-autocopy": true,
    "picgo-plugin-gitlab-files": true,
    "picgo-plugin-s3": true,
    "picgo-plugin-custom-uploader-fix": true,
    "picgo-plugin-web-uploader": true,
    "picgo-plugin-s3-own": true
  },
  "picgo-plugin-compress-next": {
    "Compress Type": "webp-converter",
    "Gif compress Type": "webp-converter",
    "Auto Refresh TinyPng Key Across Months": false,
    "TinyPng API Key": ""
  },
  "uploader": {
    "github": {
      "configList": [
        {
          "_configName": "picc",
          "_id": "d4b75295-a443-4075-ad2e-73caf72e078c",
          "_createdAt": 1730352070049,
          "_updatedAt": 1750252690127,
          "repo": "kevzcr/picc",
          "branch": "main",
          "token": "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",
          "path": "img/",
          "customUrl": "https://picc.j07.dpdns.org/"
        },
        {
          "_configName": "imggong",
          "repo": "zcr07/img",
          "branch": "main",
          "path": "images/",
          "customUrl": "https://cdn.jsdelivr.net/gh/zcr07/img@main",
          "token": "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",
          "_id": "9b921d00-95f0-47dd-9524-aea7e9ec70e4",
          "_createdAt": 1730352442411,
          "_updatedAt": 1750260415884
        },
        {
          "_configName": "node-1gong",
          "repo": "zcr07/node-1",
          "branch": "main",
          "token": "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",
          "path": "imgss/",
          "customUrl": "https://cdn.jsdelivr.net/gh/zcr07/node-1@main",
          "_id": "dc6c8cac-b260-49d1-b260-8832960dd53d",
          "_createdAt": 1732321803260,
          "_updatedAt": 1750262086024
        },
        {
          "_configName": "node-2gong",
          "path": "imgss/",
          "customUrl": "https://cdn.jsdelivr.net/gh/zcr07/node-2@main",
          "token": "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",
          "branch": "main",
          "repo": "zcr07/node-2",
          "_id": "f2e24856-c89e-4f09-9ef8-670e975cbb5d",
          "_createdAt": 1732321905575,
          "_updatedAt": 1750262090766
        },
        {
          "_configName": "node-3gong",
          "repo": "zcr07/node-3",
          "branch": "main",
          "token": "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",
          "path": "imgss/",
          "customUrl": "https://cdn.jsdelivr.net/gh/zcr07/node-3@main",
          "_id": "00642892-c82e-4b88-b522-37bb09467a17",
          "_createdAt": 1732321935850,
          "_updatedAt": 1750262096694
        },
        {
          "_configName": "ttuk",
          "repo": "zcr07/ttuk",
          "branch": "main",
          "token": "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",
          "path": "imgss/",
          "customUrl": "https://ttuk.zcr4.ip-ddns.com",
          "_id": "a6f7484a-d0c2-4c63-8f9d-66a77b93cf09",
          "_createdAt": 1748072373720,
          "_updatedAt": 1750262149619
        },
        {
          "_configName": "s1",
          "repo": "zcr07/img1",
          "branch": "main",
          "token": "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",
          "path": "ku/",
          "customUrl": "https://tt.zb9.dpdns.org/img1/main",
          "_id": "ecde49bd-0a2a-4786-b3e2-a189511b76b4",
          "_createdAt": 1750176553003,
          "_updatedAt": 1750262162727
        },
        {
          "_configName": "kev",
          "repo": "zbb07/img1",
          "branch": "main",
          "token": "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",
          "path": "img11/",
          "customUrl": "https://tt.n06.dpdns.org/img1/main",
          "_id": "0539e0c1-d5ad-4ca8-9c6b-227ade89097d",
          "_createdAt": 1750209468454,
          "_updatedAt": 1750262116492
        },
        {
          "_configName": "imgy",
          "repo": "zyy200712/imgy",
          "branch": "main",
          "token": "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",
          "path": "im/",
          "customUrl": "https://tt.zc08.dpdns.org//imgy/main",
          "_id": "78220a13-a774-4ace-ae7a-baf4f8b49235",
          "_createdAt": 1750296500096,
          "_updatedAt": 1750296500096
        },
        {
          "_configName": "img7",
          "repo": "zbb7001/img7",
          "branch": "main",
          "token": "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",
          "path": "ku/",
          "customUrl": "https://tt.y07.dpdns.org/img7/main",
          "_id": "e35fd9f1-ec22-4701-8385-63ea6146e311",
          "_createdAt": 1750298689399,
          "_updatedAt": 1750299085697
        },
        {
          "_configName": "node-1",
          "repo": "zb9678/node-1",
          "branch": "main",
          "token": "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",
          "path": "images/",
          "customUrl": "https://node1.zcr5.qzz.io",
          "_id": "ce0eed96-9c41-4470-a462-328e028af4d7",
          "_createdAt": 1751677748671,
          "_updatedAt": 1751727401443
        },
        {
          "_configName": "node-2",
          "repo": "zb9678/node-2",
          "branch": "main",
          "token": "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",
          "path": "images/",
          "customUrl": "https://node1.zcr5.qzz.io",
          "_id": "f594113f-9721-40b4-8726-b2795aee0b5e",
          "_createdAt": 1751677888728,
          "_updatedAt": 1751677888728
        },
        {
          "_configName": "node-3",
          "repo": "zb9678/node-3",
          "branch": "main",
          "token": "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",
          "path": "images/",
          "customUrl": "https://node1.zcr5.qzz.io",
          "_id": "545107ed-f91a-4665-8732-e1666c42ccca",
          "_createdAt": 1751677919508,
          "_updatedAt": 1751677919508
        }
      ],
      "defaultId": "ce0eed96-9c41-4470-a462-328e028af4d7"
    },
    "gitlab-files-uploader": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "dc3bf286-6209-4748-bfc6-e1a61327ebaa",
          "_createdAt": 1732375525821,
          "_updatedAt": 1732375525821
        },
        {
          "_configName": "2411",
          "gitUrl": "https://gitlab.com",
          "projectId": "70179121",
          "branch": "main",
          "gitToken": "glpat-dtUM3WpXP_151s827W_m",
          "fileName": "images/{fileName}",
          "commitMessage": "Upload {fileName} By PicGo gitlab files uploader at {year}-{month}-{day}",
          "_id": "456e8667-44e8-41a5-847b-6942c65f9756",
          "_createdAt": 1732375929167,
          "_updatedAt": 1748171691018,
          "gitVersionUnderThirteen": null,
          "deleteRemote": null,
          "deleteMessage": null,
          "deleteInform": null,
          "authorMail": null,
          "authorName": null
        },
        {
          "_configName": "img3",
          "gitUrl": "https://gitlab.com",
          "projectId": "70919927",
          "branch": "main",
          "gitToken": "glpat-zYYzfwRsWz-evMSiSeV7",
          "fileName": "img33/{fileName}",
          "commitMessage": "Upload {fileName} By PicGo gitlab files uploader at {year}-{month}-{day}",
          "_id": "986a9bbb-01c5-478f-8483-35e8e8f91634",
          "_createdAt": 1750216001414,
          "_updatedAt": 1750216001414
        },
        {
          "_configName": "img2",
          "gitUrl": "https://gitlab.com",
          "projectId": "71398858",
          "branch": "main",
          "gitToken": "glpat-5m2X_ZUDsYh13CuBegbc",
          "fileName": "images/{fileName}",
          "commitMessage": "Upload {fileName} By PicGo gitlab files uploader at {year}-{month}-{day}",
          "_id": "443bbf8b-e6c9-488f-a4e0-91a88f56db04",
          "_createdAt": 1751785982309,
          "_updatedAt": 1751786021347,
          "gitVersionUnderThirteen": null,
          "deleteRemote": null,
          "deleteMessage": null,
          "deleteInform": null,
          "authorMail": null,
          "authorName": null
        }
      ],
      "defaultId": "443bbf8b-e6c9-488f-a4e0-91a88f56db04"
    },
    "aws-s3": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "f11fb1f3-7b77-4dee-9cfd-dea20b39b579",
          "_createdAt": 1733450209143,
          "_updatedAt": 1733450209143
        },
        {
          "_configName": "zcr071225",
          "accessKeyID": "005171e1ce22c070000000003",
          "secretAccessKey": "K005dZCagHbsKeKGs6JCDSEQxUqyess",
          "bucketName": "zcr071225",
          "uploadPath": "files/{fileName}.{extName}",
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "_id": "c9350f54-fb5c-41d5-aa6a-f53801c3efae",
          "_createdAt": 1733450557313,
          "_updatedAt": 1751815675221,
          "region": null,
          "proxy": "",
          "urlPrefix": "https://cdn.jsdelivr.net/gh",
          "urlSuffix": "",
          "pathStyleAccess": false,
          "rejectUnauthorized": false,
          "acl": "",
          "disableBucketPrefixToURL": false,
          "outputURLPattern": ""
        },
        {
          "_configName": "kevzcr-1",
          "accessKeyID": "005171e1ce22c070000000006",
          "secretAccessKey": "K005eVKFoFB9rhcd60PYp2flle/Elp4",
          "bucketName": "kevzcr1",
          "uploadPath": "images/{fileName}.{extName}",
          "_id": "64a0b7e8-8b21-46e0-8b93-f9648064deec",
          "_createdAt": 1751806119663,
          "_updatedAt": 1751885918283,
          "region": null,
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "proxy": "",
          "rejectUnauthorized": false,
          "acl": "",
          "pathStyleAccess": false,
          "outputURLPattern": "",
          "urlPrefix": null,
          "urlSuffix": "",
          "disableBucketPrefixToURL": false
        },
        {
          "_configName": "kevzcr-2",
          "accessKeyID": "005a798057f86250000000001",
          "secretAccessKey": "K005n7cwUFP5CLKsTfT0xgw0pJuwSaI",
          "bucketName": "kevzcr2",
          "uploadPath": "images/{fileName}.{extName}",
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "proxy": "",
          "_id": "47871ddc-fd2b-461b-86cd-fa5926bdbb5f",
          "_createdAt": 1751848840193,
          "_updatedAt": 1751864467504,
          "region": null,
          "rejectUnauthorized": false,
          "acl": "",
          "pathStyleAccess": false,
          "outputURLPattern": "",
          "urlPrefix": null,
          "urlSuffix": "",
          "disableBucketPrefixToURL": false
        },
        {
          "_configName": "kevzcr-3",
          "accessKeyID": "005e634d18d70550000000001",
          "secretAccessKey": "K005bV0nxzCqoS8WO4Ajj54CZZ8jRvk",
          "bucketName": "kevzcr3",
          "uploadPath": "images/{fileName}.{extName}",
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "proxy": "",
          "_id": "6c35ec1b-8ba9-4309-84fa-06fde8fc9425",
          "_createdAt": 1751849139837,
          "_updatedAt": 1751864483776,
          "region": null,
          "rejectUnauthorized": false,
          "acl": "",
          "pathStyleAccess": false,
          "outputURLPattern": "",
          "urlPrefix": null,
          "urlSuffix": "",
          "disableBucketPrefixToURL": false
        }
      ],
      "defaultId": "64a0b7e8-8b21-46e0-8b93-f9648064deec"
    },
    "custom-uploader-fix": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "1301fd83-33f1-4c1c-9d99-6673199d2d07",
          "_createdAt": 1748073081029,
          "_updatedAt": 1748073081029
        }
      ],
      "defaultId": "1301fd83-33f1-4c1c-9d99-6673199d2d07"
    },
    "aws-s3-own": {
      "configList": [
        {
          "_configName": "Default",
          "_id": "03d998b0-e135-4ba5-a4dd-bb27f20455f1",
          "_createdAt": 1752022098002,
          "_updatedAt": 1752022098002
        },
        {
          "_configName": "kevzcr 1",
          "bucketName": "kevzcr1",
          "accessKeyID": "005171e1ce22c070000000006",
          "secretAccessKey": "K005eVKFoFB9rhcd60PYp2flle/Elp4",
          "uploadPath": "images/{fileName}.{extName}",
          "urlPrefix": "",
          "_id": "41bb9dfb-23fc-46b6-9a3a-ee3fc9326f41",
          "_createdAt": 1752022209995,
          "_updatedAt": 1752024955772,
          "trimmedUploadPath": "{year}{month}/original/{md5}.{extName}",
          "region": null,
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "proxy": null,
          "urlSuffix": "",
          "pathStyleAccess": false,
          "rejectUnauthorized": false,
          "acl": "",
          "disableBucketPrefixToURL": false
        },
        {
          "_configName": "kevzcr 2",
          "bucketName": "kevzcr2",
          "accessKeyID": "005a798057f86250000000001",
          "secretAccessKey": "K005n7cwUFP5CLKsTfT0xgw0pJuwSaI",
          "uploadPath": "images/{fileName}.{extName}",
          "endpoint": "https://s3.us-east-005.backblazeb2.com",
          "_id": "030902e5-596c-46a3-9eb9-4be8535e9d91",
          "_createdAt": 1752022489946,
          "_updatedAt": 1752024948026,
          "trimmedUploadPath": "{year}{month}/original/{md5}.{extName}",
          "region": null,
          "proxy": null,
          "urlPrefix": null,
          "urlSuffix": "",
          "pathStyleAccess": false,
          "rejectUnauthorized": false,
          "acl": "",
          "disableBucketPrefixToURL": false
        },
        {
          "_configName": "kevzcr 3",
          "endpoint": "http://s3.us-east-005.backblazeb2.com",
          "uploadPath": "images/{fileName}.{extName}",
          "secretAccessKey": "K005bV0nxzCqoS8WO4Ajj54CZZ8jRvk",
          "accessKeyID": "005e634d18d70550000000001",
          "bucketName": "kevzcr3",
          "_id": "4fb61a1e-abcc-404d-a148-69c3ab8df16e",
          "_createdAt": 1752024843867,
          "_updatedAt": 1752025625630,
          "trimmedUploadPath": "{year}{month}/original/{md5}.{extName}",
          "region": null,
          "proxy": null,
          "urlPrefix": null,
          "urlSuffix": "",
          "pathStyleAccess": false,
          "rejectUnauthorized": false,
          "acl": "",
          "disableBucketPrefixToURL": false
        }
      ],
      "defaultId": "4fb61a1e-abcc-404d-a148-69c3ab8df16e"
    }
  },
  "picgo-plugin-autocopy": {
    "template": "Custom",
    "customLink": "<p align='center'><img src=\"$url\" style='width:400px;'><br><br>"
  }
}
```