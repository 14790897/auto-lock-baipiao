# Issue Auto Lock

该 Python 脚本使用 GitHub API 自动管理一个 GitHub 仓库的 issues。它特别针对那些没有为仓库点星但提交了 issue 的用户，自动锁定这些用户的 issue，如果这些用户之后为仓库点星，则自动解锁。

## 功能

- **自动检测和锁定**：自动检测所有打开的 issues，如果 issue 提出者没有为仓库点星，则自动锁定该 issue，并添加一条评论，提示用户为仓库点星后考虑解锁
- **自动解锁**：对于已锁定的 issue，如果用户后续为仓库点了星，则自动解锁，并添加一条评论，通知用户 issue 已解锁
  提示： 检测频率请在 action 中的 schedule 中设置，建议每天检测一次

## GitHub Action Marketplace 已上架，可以直接使用(最方便，推荐)

action 市场地址：[issue-auto-lock](https://github.com/marketplace/actions/issue-auto-lock)

### secrets 需要配置两个变量

```sh
GH_REPO: ${{ secrets.GH_REPO }} # 需要检测的仓库名
ISSUE_LABELS: ${{ secrets.ISSUE_LABELS }} # issue 标签
```

### 使用示例

[.github/workflows/issue-auto-lock.yml](.github/workflows/issue-auto-lock.yml)
直接复制到你的仓库的 `.github/workflows` 目录下即可

## 手动执行(只执行一次)

### 安装

1. 克隆此仓库到本地：

   ```sh
   git clone https://github.com/devhaozi/issue-auto-lock
   ```

2. 进入项目目录：

   ```sh
   cd auto-lock-baipiao
   ```

3. 安装依赖：

   ```sh
   pip install -r requirements.txt
   ```

### 设置

1. 创建 `.env` 文件并设置以下环境变量：

   ```sh
   GH_REPO=your_username/your_repo
   GH_TOKEN=your_github_access_token
   ISSUE_LABELS="haven't given me a star"
   ISSUE_CLOSE_COMMENT="Thank you for opening this issue. I noticed that you haven not given me a star yet, so I will close this issue. Please give me a star first and wait for it to be unlocked. Thank you for your understanding."
   ISSUE_REOPEN_COMMENT="Thank you for giving me a star. I have unlocked this issue. If you have any questions, please feel free to ask. Thank you for your support.
   ```

   - `GH_REPO`: 设置为你的 GitHub 用户名和仓库名。
   - `GH_TOKEN`: 设置为你的 GitHub 访问令牌。确保令牌有足够的权限管理 issues。
   - `ISSUE_LABELS`: 在自动创建或更新 issues 时应用的标签。
   - `ISSUE_CLOSE_COMMENT`: 当锁定 issue 时添加的评论。
   - `ISSUE_REOPEN_COMMENT`: 当解锁 issue 时添加的评论。

### 运行脚本

执行脚本：

```sh
python issue_auto_lock.py
```

## 贡献

欢迎通过 Pull Requests 或 Issues 提出改进建议或报告问题。

## 许可

该项目使用 [MIT License](LICENSE) 许可证。
