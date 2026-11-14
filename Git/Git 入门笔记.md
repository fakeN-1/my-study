# Git 入门笔记

## 1. Git、GitHub 和 PyCharm 分别做什么

- **Git** 管理代码的版本。每次提交都会记录选中的文件内容、提交人和提交说明，可以查看历史、比较版本，也可以为新功能单独开分支。
- **GitHub** 托管远程 Git 仓库，用来同步代码、协作和审阅改动。
- **PyCharm** 提供 Git 的图形界面。用按钮提交和用终端执行 `git commit`，操作的是同一个本地仓库。

Git 不会在每次保存文件时自动创建版本。**保存**写入本地文件，**提交**写入本地历史，**推送**才会把提交上传到 GitHub。

## 2. 一次修改怎样到达 GitHub

```text
修改并保存文件 → 选中要提交的改动 → Commit → Push
    工作区          本次提交的内容       本地历史   GitHub
```

Git 命令行用 `git add` 把改动放入**暂存区**，用 `git commit` 把暂存区的内容记录成一次提交。在 PyCharm 的默认提交界面里，可以直接勾选文件。PyCharm 会为本次提交处理暂存步骤。

| 操作 | 作用 | 常用命令 |
| --- | --- | --- |
| Status | 查看哪些文件有改动 | `git status` |
| Diff | 对比文件改动 | `git diff` |
| Commit | 创建一次本地提交 | `git commit -m "提交说明"` |
| Push | 把本地提交发送到远程仓库 | `git push` |
| Fetch | 下载远程更新的信息，供查看和比较 | `git fetch` |
| Pull | 下载远程更新，并整合到当前本地分支 | `git pull` |
| Log | 查看提交历史 | `git log --oneline` |

## 3. 用 PyCharm 打开已有仓库

以我的桌面仓库为例：

- 本地目录：`C:\Users\fakeN\Desktop\Git`
- GitHub 仓库：`https://github.com/fakeN-1/Git`
- 当前分支：`main`
- 远程名称：`origin`

1. 在 PyCharm 选择 **File → Open**，打开本地目录。
2. 按 `Ctrl+Alt+S` 打开设置，进入 **Version Control → Git**，点击 **Test** 检查 Git 是否可用。
3. 如果 PyCharm 找不到 Git，在之前成功推送的 Windows 终端运行 `where.exe git`，把对应的 `git.exe` 路径填进 **Path to Git executable**。
4. 在 PyCharm 的 **Terminal** 中运行下面的命令，确认提交身份、分支和远程地址。

```powershell
git config --get user.name
git config --get user.email
git status -sb
git remote -v
```

`origin` 是这条远程地址在本地的名字。`origin/main` 是本地记录的远程 `main` 分支位置。之前推送时使用了 `-u`，已经把本地 `main` 和 `origin/main` 关联起来，后续通常可以直接 Push 或 Pull。 [PyCharm Git 设置](https://www.jetbrains.com/help/pycharm/settings-version-control-git.html)

## 4. 在 PyCharm 提交并推送

第一次可以用一个 `README.md` 练习。它会显示在 GitHub 仓库首页。

1. 在项目根目录新建 `README.md`，写几行项目说明并保存。
2. 按 `Ctrl+K` 打开 **Commit** 界面，勾选 `README.md`。
3. 点击文件检查改动，填写提交说明，例如 `添加项目说明`，然后点击 **Commit**。
4. 按 `Ctrl+Shift+K` 打开 **Push** 窗口，确认目标是 `origin/main`，再点击 **Push**。
5. 打开 GitHub 仓库页面，确认 `README.md` 和提交记录都已出现。

如果想把第三、四步合在一起，可以选择 **Commit and Push**。要回看刚才保存的版本，打开底部的 **Git → Log**，点击某条提交查看它改了哪些文件。 [PyCharm 提交和推送文档](https://www.jetbrains.com/help/pycharm/commit-and-push-changes.html)

## 5. 拉取、分支和冲突

### 拉取远程更新

如果我在 GitHub 网页上改过文件，或在另一台电脑推送过提交，可以在 PyCharm 选择 **Git → Pull**，确认从 `origin/main` 拉取。多人协作时，可以在开始工作前先拉取一次。手头还有改动时，先检查工作区，必要时提交或临时保存，再拉取。

### 用分支开发新功能

分支适合把一组改动集中在一起。例如，要开发文件导入功能：

1. 切换到 `main` 并拉取更新。
2. 点击 PyCharm 的分支菜单，选择 **New Branch**，创建 `feature/file-import` 并切换过去。
3. 在新分支里写代码、提交并推送。
4. 在 GitHub 创建 **Pull Request（PR）**，把目标分支设为 `main`。检查改动后合并。

**Pull** 是把远程更新整合到本地。**Pull Request** 是在 GitHub 上发起的合并提议。

### 处理合并冲突

两个分支都改了同一段代码时，Git 有时无法自动决定保留哪一段。打开 PyCharm 的冲突解决窗口，对照双方的改动，编辑并检查合并后的结果，再按照界面提示完成合并。涉及业务逻辑时，先运行相关代码或测试，再推送。 [PyCharm Git 入门教程](https://www.jetbrains.com/help/pycharm/working-with-git-tutorial.html)

## 6. Python 项目里哪些文件该提交

一般会提交源码、测试、`README.md` 和依赖声明，例如 `pyproject.toml` 或 `requirements.txt`。虚拟环境、运行缓存和包含密钥的本地配置可以加入项目根目录的 `.gitignore`：

```gitignore
.venv/
__pycache__/
*.pyc
.pytest_cache/
.env
```

`.gitignore` 主要作用于尚未被 Git 跟踪的文件。新加一条忽略规则后，已经提交过的文件仍然在历史里。若误推了密码或 API 密钥，应立即撤销或轮换该凭据。

## 7. 常见问题速查

| 遇到的问题 | 怎么处理 |
| --- | --- |
| 提交时提示缺少 `user.name` 或 `user.email` | 在 PyCharm 终端运行 `git config --get user.name` 和 `git config --get user.email`。缺少哪项，就用 `git config --global` 设置哪项。 |
| 提交成功，但 GitHub 上没看到 | 打开 **Git → Push**。如果已经推送，检查 GitHub 页面当前查看的分支。 |
| Push 提示远程有新的提交 | 先查看并整合远程更新，解决可能出现的冲突，再重新推送。 |
| 想撤销已经推送的提交 | 在 **Git → Log** 找到该提交，使用 **Revert Commit** 生成一条反向提交，然后推送。 |
| 桌面的仓库提示 `dubious ownership` | 如果确认是自己的仓库，可以按下面的命令只信任这个目录，然后在 PyCharm 中重试。 |

```powershell
git config --global --add safe.directory "C:/Users/fakeN/Desktop/Git"
```
