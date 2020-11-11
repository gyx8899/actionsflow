# Actions flow
Common useful github actions which can copy and paste. (Need add related secrets)

## Actions

### Action: Sync GitHub to Gitee
[sync2gitee.yml](./.github/workflows/sync2gitee.yml)

需要添加 3 个 secrets:

- `GITEE_PRIVATE_KEY`，[Gitee公钥对应的私钥](https://gitee.com/profile/sshkeys)

- `GITEE_TOKEN`，[Gitee对应的用于创建仓库的token](https://gitee.com/profile/personal_access_tokens)

- `GITEE_REPO_NAME`，比如当前项目名：actionsflow

