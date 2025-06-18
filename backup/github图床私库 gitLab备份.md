## github图床  私库 gitLab备份

[教程](https://www.youtube.com/watch?v=eRqIpeeo9SA)

## Token

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:08:39:48.png" style="width:400px;"></p><br>

[Token](https://github.com/settings/tokens/new)

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:08:42:49.png" style="width:400px;"></p><br>

## cloudflare 新建workers 

[cloudflare](https://dash.cloudflare.com/9e27b7387c208a2ad54e44ada4e24423/workers/services/edit/img1/production)

```
addEventListener('fetch', event => {
  event.respondWith(handleRequest(event.request))
})

async function handleRequest(request) {
  const url = new URL(request.url)
  const path = url.pathname
  
  // 定义环境变量 GITHUB_USERNAME 和 GITHUB_PAT
  const GITHUB_USERNAME = 'zbb07' // 替换为你的 GitHub 用户名
  const GITHUB_PAT = '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' // 替换为你的 GitHub PAT，只开放 repo 权限即可
  
  // 构建 GitHub raw 内容的 URL
  const githubUrl = `https://raw.githubusercontent.com/${GITHUB_USERNAME}${path}`
  
  // 创建新的请求，添加必要的头部
  const modifiedRequest = new Request(githubUrl, {
    method: request.method,
    headers: {
      ...request.headers,
      'Authorization': `token ${GITHUB_PAT}`,
      'Accept': 'application/vnd.github.v3.raw'
    }
  })
  
  // 发送请求并返回响应
  try {
    const response = await fetch(modifiedRequest)
    
    // 如果响应不成功，抛出错误
    if (!response.ok) {
      throw new Error(`GitHub API responded with ${response.status}: ${response.statusText}`)
    }
    
    // 创建新的响应，保留原始内容但移除敏感头部
    const newResponse = new Response(response.body, response)
    newResponse.headers.delete('Authorization')
    
    return newResponse
  } catch (error) {
    return new Response(`Error: ${error.message}`, { status: 500 })
  }
}

```
## 测试  显示 # img1

https://img1.kev071225.workers.dev/img1/main/README.md

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:08:54:09.png" style="width:400px;"></p><br>

## 设置自定义域名 tt.n06.dpdns.org

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:08:56:31.png" style="width:400px;"></p><br>

## 设置PicGo

### 插件设置 安装compress-next 1.5.2

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:08:59:20.png" style="width:400px;"></p><br>

## tinypng 申请 Token

https://tinypng.com/

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:05:45.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:06:33.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:07:24.png" style="width:400px;"></p><br>

6RLd8v72LsrYHn3TpsZQ0Hjx00TFBbyk

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:08:17.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:10:01.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:10:42.png" style="width:400px;"></p><br>

## PicGo设置

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:12:09.png" style="width:400px;"></p><br>

## 图床设置   GitHub

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:13:39.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:17:27.png" style="width:400px;"></p><br>

图床配置名  sikuimg1
设定仓库名  zcr07/img1
设定分支名  main
设定Token   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
设定存储路径 siku/
设定自定义域名 https://tt.zb9.dpdns.org/img1/main

## 上传一张图片测试

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:20:09.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:18:56.png" style="width:400px;"></p><br>

## github中已经上传成功

https://github.com/zbb07/img1/tree/main/img11

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:21:33.png" style="width:400px;"></p><br>

## 备份到gitLab

https://gitlab.com/

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:25:38.png" style="width:400px;"></p><br>

只需要命名 img11  和github上一样就行了

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:27:19.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:29:10.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:31:03.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:31:47.png" style="width:400px;"></p><br>

glpat-bRVj5zf6DyKpc4gJXRU_

## 回到Github

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:34:31.png" style="width:400px;"></p><br>

https://github.com/zbb07/img1/settings/secrets/actions

GITLAB_USERNAME	Gitlab 用户名                  zcr071225
GITLAB_REPO	Gitlab 上创建的项目名          img11
GITLAB_PAT	上面生成的 Gitlab 项目的 PAT   glpat-bRVj5zf6DyKpc4gJXRU_

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:36:48.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:37:33.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:38:18.png" style="width:400px;"></p><br>

## 新增文件

`.github/workflows/sync-to-gitlab.yml`

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:39:39.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:43:17.png" style="width:400px;"></p><br>

```
name: Sync to GitLab

on:
  push:
    branches:
      - main
  workflow_dispatch:

jobs:
  sync:
    runs-on: ubuntu-latest

    env:
      GITLAB_USERNAME: ${{ secrets.GITLAB_USERNAME }}
      GITLAB_REPO: ${{ secrets.GITLAB_REPO }}
      GITLAB_PAT: ${{ secrets.GITLAB_PAT }}

    steps:
    - name: Checkout repository
      uses: actions/checkout@v4.1.1
      with:
        fetch-depth: 0

    - name: Set up Git
      run: |
        git config --global user.name 'github-actions'
        git config --global user.email 'github-actions@github.com'

    - name: Add GitLab remote
      run: git remote add gitlab https://${{ env.GITLAB_USERNAME }}:${{ env.GITLAB_PAT }}@gitlab.com/${{ env.GITLAB_USERNAME }}/${{ env.GITLAB_REPO }}.git

    - name: Force push to GitLab
      run: git push gitlab main --force

```

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:41:40.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:43:55.png" style="width:400px;"></p><br>

## 同步已成功 查看gitLab

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:45:08.png" style="width:400px;"></p><br>

<p align="center"><img src="https://cdn.jsdelivr.net/gh/zb9678/img@main/im8/06.18:09:47:47.png" style="width:400px;"></p><br>

已成功备份到了gitLab上了。