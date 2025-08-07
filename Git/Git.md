## Git基础命令

### Git版本查看

*   `git --version`: 查看Git版本。

### 初始化与配置

*   `git init`: 在当前目录初始化一个新的Git仓库。
*   `git init --bare`: 在当前目录初始化一个新的Git裸库(不带工作区,用于远程库创建)。
*   `git config`: 设置Git的配置项，全局配置信息保存在\~/.gitconfig文件中。
    *   `git config [--global] --list`: 显示当前配置。
    *   `git config [--global] user.name "[name]"`: 设置提交用户名。
    *   `git config [--global] user.email "[email]"`: 设置提交用户邮箱。

### 工作区与暂存区操作

*   `git add <file>`: 将指定文件添加到暂存区。
*   `git add .` 或 `git add -A`: 添加所有修改（包括新建、修改和删除的文件）到暂存区。
*   `git restore <file>`: 丢弃工作区的改动
*   `git rm --cache <file>`: 从暂存区移除文件。

### 提交与历史查询

*   `git commit -m "[message]"`: 提交暂存区的改动，附带提交消息。
*   `git commit --amend -m "[message]"`: 修改最后一次提交。
*   `git status`: 查看工作区和暂存区的状态。
*   `git status -s`: 查看工作区和暂存区的简短状态。
*   `git diff`: 显示工作区与暂存区的差异。
*   `git diff --cached` 或 `git diff --staged`: 显示暂存区与最近提交的差异。
*   `git diff <commit> <commit>`: 比较两次提交之间的差异。
*   `git show <commit>`: 展示特定提交的详情（包括改动、提交消息等）。
*   `git log`: 显示提交历史。
*   `git log --oneline`: 以简洁格式显示提交历史。
*   `git log --graph --decorate --oneline --all`: 以分支合并图格式显示提交历史。
*   `git reflog`: 显示引用日志，便于找回丢失的提交。
*   `git blame <file>`: 显示文件每一行的最后修改者及其提交信息。

### 分支与标签

*   `git branch`: 列出本地分支。
*   `git branch -v`: 列出本地分支及最后一次提交信息。
*   `git branch -r`: 列出远程分支。
*   `git branch -a`: 列出所有分支（包括远程分支）。
*   `git branch <branch-name>`: 创建新分支。
*   `git branch -d <branch>`: 删除已合并的分支。
*   `git branch -D <branch>`: 强制删除分支（即使未合并）。
*   `git checkout <branch>`: 切换到指定分支。
*   `git checkout -b <new-branch>`: 创建并切换到新分支。
*   `git merge <branch>`: 合并指定分支到当前分支。
*   `git rebase <branch>`: 在另一个分支基础上重新应用当前分支的改动。
*   `git tag <tag-name>`: 创建标签。
*   `git tag -d <tag-name>`: 删除标签。
*   `git tag -a <tag-name> -m "[message]"`: 创建带有说明的annotated标签。
*   `git tag -s <tag-name> -m "[message]"`: 使用GPG签署的annotated标签。
*   `git tag`: 列出所有标签。
*   `git show <tag>`: 展示标签详情。
*   `git push origin <tag>`: 推送标签到远程仓库。
*   `git push origin --tags`: 推送所有未推送的标签到远程仓库。
*   `git push origin :refs/tags/<tag>`: 删除远程标签。

### 远程仓库交互

*   `git clone <url>`: 克隆远程仓库到本地。
*   `git remote`: 管理远程仓库。
    *   `git remote add <name> <url>`: 添加远程仓库。
    *   `git remote rm <name>`: 删除远程仓库。
    *   `git remote -v`: 显示远程仓库URL及其跟踪的分支。
*   `git fetch [remote]`: 从远程仓库获取最新数据（不自动合并）。
*   `git pull [remote] [branch]`: 获取远程分支并自动合并到当前分支。
*   `git push [remote] [branch]`: 将本地分支推送到远程仓库。

### 版本回溯与重置

*   `git reset <commit>`: 回退到指定提交（默认保留工作区改动）。
    *   `git reset --hard <commit>`: 回退到指定提交并丢弃所有未提交的改动。
    *   `git reset --soft <commit>`: 回退到指定提交，保留所有改动在暂存区。
    *   `git reset --mixed <commit>`: 回退到指定提交，保留所有改动在工作区。
*   `git revert <commit>`: 回退到指定提交，并新建一个版本号。
*   `git checkout <file>`: 将指定文件从最近提交恢复到工作区（丢弃未提交的改动）。
*   `git clean`: 清理未追踪的文件。
    *   `git clean -f`: 删除未追踪的文件。
    *   `git clean -fd`: 删除未追踪的文件和目录。
    *   `git clean -n`: 模拟清理，显示将要删除的文件列表。

### 存储与恢复工作进度

*   `git stash`: 将当前未提交的改动暂存起来，恢复工作区至上次提交状态。
*   `git stash list`: 列出所有stash记录。
*   `git stash apply [<stash>]`: 应用某个stash（默认最近的）的改动到工作区。
*   `git stash pop [<stash>]`: 应用并删除某个stash的改动。
*   `git stash drop [<stash>]`: 删除指定stash。

## 创建SSH密钥

*   `ssh-keygen -t rsa -C "注释"`: 创建ssh密钥

## Git忽略文件.gitignore

    #
    *
    **
    ?
    [1-9][a-z]

