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

点击上代码 [sync2gitee.yml](./workflows/sync2gitee.yml)

#### 步骤：

- 在个人 Github 需要同步的仓库上添加 3 个 secrets: (Setting -> Secrets -> New repository secret)

    - `GITEE_USER`，比如个人的 Gitee user: [steper](https://gitee.com/steper)
    - `GITEE_PRIVATE_KEY`，获取方法(如果已有，直接设置) - [Gitee公钥对应的私钥](https://gitee.com/profile/sshkeys)
        新建 private key 方法：
        - [生成 SSH 公钥](https://gitee.com/help/articles/4181#article-header0)
        - [将 SSH 公钥添加到 Gitee 公钥](https://gitee.com/profile/sshkeys)
        - 同时将公钥添加到 Github 项目的 secrets 中;
    - `GITEE_TOKEN`，获取方法 - [Gitee对应的用于创建仓库的token](https://gitee.com/profile/personal_access_tokens)
        新建 token 方法：
        - 点击上面的链接并登录 Gitee, 点击“生成新令牌”，
        - 添加描述，比如用处 - Github 仓库同步到 Gitee；
        - 权限默认全选，点击提交，显示出生成的 token 值；（注意保存，需要填到 Github 的 secrets 中）

- 在 Github 仓库上提交改动（如修改 README.md），查看 Github Actions 的运行，并到 [Gitee](https://gitee.com/) 上对应仓库验证是否同步成功。

#### 示例：
Github 仓库 Action [gyx8899/blog](https://github.com/gyx8899/blog/actions)
Gitee 仓库 [steper/blog](https://gitee.com/steper/blog)

### Action: gitbook publish to gh-pages

[Publish Gitbook · Actions · GitHub Marketplace](https://github.com/marketplace/actions/publish-gitbook)

> 官方介绍非常详细，直接收录。

## 发现的技巧

- `on push` 状态下，过滤不必要的改动提交，如提交信息中包含`[build]`的时候才执行 Action，示例如下

```yaml
jobs:
  format:
    runs-on: ubuntu-latest
    if: "contains(github.event.head_commit.message, '[build]')"

  # 取反的情况
  # if: "! contains(github.event.head_commit.message, 'wip')"
```
