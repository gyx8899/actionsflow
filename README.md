# Actions flow
认识到 Github Actions 的强大和便捷后，忍不住要搞一些小轮子（小动作）。

## Secrets - 基础

### Github: `GITHUB_TOKEN`
If you choose github_token, this token is auto created when workflow launches. No extra operation is needed.

### Github: `PERSONAL_TOKEN`
- 创建一个个人的 [Access Token](https://docs.github.com/cn/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token).
- 添加一个 `token` 作为一个 [repo secret](https://docs.github.com/cn/free-pro-team@latest/actions/reference/encrypted-secrets).

> Secret name: `PERSONAL_TOKEN`
>
> Secret value: `<token>`

## Actions
站在巨人的肩膀上到底有多香，期待不如行动。

### Action: Sync GitHub to Gitee
Github 仓库每一次提交后，通过 Github Action 自动将仓库同步到 Gitee 上。

点击上代码 [sync2gitee.yml](./.github/workflows/sync2gitee.yml)

#### 步骤：

- 在个人 Github 需要同步的仓库上添加 3 个 secrets: (Setting -> Secrets -> New repository secret)

    - `GITEE_USER`，比如个人的 Gitee user: [steper](https://gitee.com/steper)
    - `GITEE_PRIVATE_KEY`，[Gitee公钥对应的私钥](https://gitee.com/profile/sshkeys)
    - `GITEE_TOKEN`，[Gitee对应的用于创建仓库的token](https://gitee.com/profile/personal_access_tokens)

- 在 Github 仓库上提交改动（如修改 README.md），查看 Github Actions 的运行，并到 [Gitee](https://gitee.com/) 上对应仓库验证是否同步成功。

#### 示例：
Github 仓库 Action [gyx8899/blog](https://github.com/gyx8899/blog/actions)
Gitee 仓库 [steper/blog](https://gitee.com/steper/blog)

### Action: gitbook publish to gh-pages

[Publish Gitbook · Actions · GitHub Marketplace](https://github.com/marketplace/actions/publish-gitbook)

> 官方介绍非常详细，直接收录。
