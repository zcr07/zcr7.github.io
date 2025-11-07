# picgo 设置


```

npm uninstall -g picgo

```

```

npm install -g picgo

```


# 设置上传器为 GitHub

```

picgo set uploader github

```

# 设置 GitHub 仓库

```

picgo set githubRepo                       zb9678/node-3

```

# 设置分支

```

picgo set githubBranch                 main

```

# 设置仓库内存储路径

```

picgo set githubPath                      images/

```

# 设置自定义域名

```

picgo set githubCustomUrl            https://node1.zcr5.qzz.io

```

# 设置 GitHub Token                         zb9678

https://github.com/settings/tokens      

```

picgo set githubToken               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

```

# 设置CF GitHub Token   第12行       zb9678

https://dash.cloudflare.com/67409d2d85f857acbae76bd86edbe9fc/workers/services/edit/billowing-morning-node123/production
                                                    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

================================================

最新
C:\Users\zb967\.picgo\config.json

## 仅输出网址

```

{
  "picBed": {
    "uploader": "github",
    "current": "github",
    "github": {
      "repo": "zb9678/node-3",
      "branch": "main",
      "token": "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",
      "path": "images/",
      "customUrl": "https://node1.zcr5.qzz.io"
    }
  },
  "picgoPlugins": {
    "picgo-plugin-autocopy": true
  }
}

```

##  输出自定义

 `<p align='center'><img src="https://node1.zcr5.qzz.io/images/20251107150503301.png" style='width:400px;'><br><br>` 

```

{
  "picBed": {
    "uploader": "github",
    "current": "github",
    "github": {
      "repo": "zb9678/node-3",
      "branch": "main",
      "token": "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",
      "path": "images/",
      "customUrl": "https://node1.zcr5.qzz.io"
    }
  },
  "picgoPlugins": {
    "picgo-plugin-autocopy": true
  },
  "picgo-plugin-autocopy": {
    "template": "Custom",
    "customLink": "<p align='center'><img src=\"$url\" style='width:400px;'><br><br>"
  }
}

```

=================================================================

老地址不用了
C:\Users\zb967\OneDrive\.picgo\config.json

==================================================================

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