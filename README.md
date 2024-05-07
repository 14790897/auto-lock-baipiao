
# GitHub Issue Manager

该Python脚本使用GitHub API自动管理一个GitHub仓库的issues。它特别针对那些没有为仓库点星但提交了issue的用户，自动锁定这些用户的issue，如果这些用户之后为仓库点星，则自动解锁。

## 功能

- **自动检测和锁定**：自动检测所有打开的issues，如果issue提出者没有为仓库点星，则自动锁定该issue。
- **自动解锁**：对于已锁定的issue，如果用户后续为仓库点了星，则自动解锁。
- **自动评论**：在锁定issue时自动添加一条评论，提示用户为仓库点星后考虑解锁。


## 安装

1. 克隆此仓库到本地：

    ```
    git clone https://github.com/your-repository-url
    ```

2. 进入项目目录：

    ```
    cd your-repository-directory
    ```

3. 安装依赖：

    ```
    pip install -r requirements.txt
    ```

## 设置

1. 创建 `.env` 文件并设置以下环境变量：

    ```
    GITHUB_REPO=your_username/your_repo
    GITHUB_TOKEN=your_github_access_token
    ISSUE_LABELS=["haven't given me a star"]
    ```

    - `GITHUB_REPO`: 设置为你的GitHub用户名和仓库名。
    - `GITHUB_TOKEN`: 设置为你的GitHub访问令牌。确保令牌有足够的权限管理issues。
    - `ISSUE_LABELS`: 在自动创建或更新issues时应用的标签。

## 运行脚本

执行脚本：

```
python your_script_name.py
```

## 注意事项

- 确保你的GitHub访问令牌安全，并仅在信任的环境中使用此脚本。
- 在使用此脚本之前，确保理解它的操作和潜在的影响。

## 贡献

欢迎通过Pull Requests或Issues提出改进建议或报告问题。

## 许可

该项目使用 [MIT License](LICENSE) 许可证。
