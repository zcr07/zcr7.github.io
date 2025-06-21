
name: Close Unauthorized Issues

on:
  issues:
    types: [opened]

permissions:
  issues: write  # 添加issues的写入权限

jobs:
  close-issue:
    runs-on: ubuntu-latest
    # 添加允许列表，只有不在允许列表中且不是仓库所有者的用户创建的Issue才会被关闭
    # 注意：这里使用的是GitHub用户名（username），不是邮箱
    # 例如：https://github.com/username 中的 username 就是用户名
    # 添加其他用户的例子：
    #  github.event.issue.user.login != 'MyFriend' &&
    #  github.event.issue.user.login != 'Collaborator123'
    if: |
      github.event.issue.user.login != github.repository_owner
    steps:
      - uses: actions/github-script@v6
        with:
          github-token: ${{secrets.GITHUB_TOKEN}}
          script: |
            await github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: '此仓库的Issue由所有者通过特定工作流创建管理，不接受未授权用户创建的Issue。此Issue将被自动关闭。如有建议，请通过其他渠道联系仓库所有者。'
            });
            
            await github.rest.issues.update({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              state: 'closed'
            });

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwODA5MTIyNzZdfQ==
-->