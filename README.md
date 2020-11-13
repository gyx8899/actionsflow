# Actions flow
认识到 Github Actions 的强大和便捷后，忍不住要搞一些小轮子（小动作）。

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
