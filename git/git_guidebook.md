# Git 基本用法

## 目录
1. [Git 简介](#git-简介)
2. [Git 安装与配置](#git-安装与配置)
3. [Git 基本命令](#git-基本命令)
   - [初始化仓库](#初始化仓库)
   - [克隆仓库](#克隆仓库)
   - [查看状态](#查看状态)
   - [添加文件到暂存区](#添加文件到暂存区)
   - [提交更改](#提交更改)
   - [查看提交历史](#查看提交历史)
   - [撤销更改](#撤销更改)
   - [分支管理](#分支管理)
   - [合并分支](#合并分支)
   - [远程仓库操作](#远程仓库操作)
4. [Git 工作流程](#git-工作流程)
   - [基本工作流程](#基本工作流程)
   - [分支工作流程](#分支工作流程)
5. [Git 高级操作](#git-高级操作)
   - [标签管理](#标签管理)
   - [暂存更改](#暂存更改)
   - [重置提交](#重置提交)
   - [查看差异](#查看差异)
6. [Git 最佳实践](#git-最佳实践)

---

## Git 简介
Git 是一个分布式版本控制系统，用于跟踪文件的更改并协调多人协作开发。它由 Linus Torvalds 于 2005 年创建，现已成为最流行的版本控制工具。

---

## Git 安装与配置
### 安装 Git
- 在 Linux 上：`sudo apt-get install git`
- 在 macOS 上：使用 Homebrew 安装：`brew install git`
- 在 Windows 上：从 [Git 官网](https://git-scm.com/) 下载安装程序。

### 配置 Git
- 设置用户名：`git config --global user.name "Your Name"`
- 设置邮箱：`git config --global user.email "your.email@example.com"`
- 查看配置：`git config --list`

---

## Git 基本命令

### 初始化仓库
- 在当前目录初始化一个新的 Git 仓库：
  `git init`

### 克隆仓库
- 克隆远程仓库到本地：
  `git clone <repository-url>`

### 查看状态
- 查看工作区和暂存区的状态：
  `git status`

### 添加文件到暂存区
- 将文件添加到暂存区：
  `git add <file-name>`
- 添加所有更改的文件：
  `git add .`

### 提交更改
- 提交暂存区的更改并添加提交信息：
  `git commit -m "Your commit message"`

### 查看提交历史
- 查看提交历史：
  `git log`
- 查看简化的提交历史：
  `git log --oneline`

### 撤销更改
- 撤销工作区的更改：
  `git checkout -- <file-name>`
- 撤销暂存区的更改：
  `git reset HEAD <file-name>`

### 分支管理
- 查看所有分支：
  `git branch`
- 创建新分支：
  `git branch <branch-name>`
- 切换分支：
  `git checkout <branch-name>`
- 创建并切换到新分支：
  `git checkout -b <branch-name>`
- 删除分支：
  `git branch -d <branch-name>`

### 合并分支
- 将指定分支合并到当前分支：
  `git merge <branch-name>`

### 远程仓库操作
- 查看远程仓库：
  `git remote -v`
- 添加远程仓库：
  `git remote add origin <repository-url>`
- 推送本地分支到远程仓库：
  `git push origin <branch-name>`
- 拉取远程仓库的更新：
  `git pull origin <branch-name>`

---

## Git 工作流程

### 基本工作流程
1. 初始化或克隆仓库。
2. 在工作区修改文件。
3. 将更改添加到暂存区：`git add`。
4. 提交更改：`git commit`。
5. 推送更改到远程仓库：`git push`。

### 分支工作流程
1. 创建新分支：`git checkout -b <branch-name>`。
2. 在新分支上开发并提交更改。
3. 切换回主分支：`git checkout main`。
4. 合并新分支：`git merge <branch-name>`。
5. 推送合并后的更改：`git push origin main`。

---

## Git 高级操作

### 标签管理
- 创建标签：
  `git tag <tag-name>`
- 查看所有标签：
  `git tag`
- 推送标签到远程仓库：
  `git push origin <tag-name>`

### 暂存更改
- 暂存当前工作区的更改：
  `git stash`
- 恢复暂存的更改：
  `git stash apply`

### 重置提交
- 重置到指定提交（保留工作区更改）：
  `git reset <commit-hash>`
- 重置到指定提交（丢弃工作区更改）：
  `git reset --hard <commit-hash>`

### 查看差异
- 查看工作区与暂存区的差异：
  `git diff`
- 查看暂存区与最新提交的差异：
  `git diff --cached`

---

## Git 最佳实践
1. **频繁提交**：将更改分解为小的、逻辑独立的提交。
2. **编写清晰的提交信息**：提交信息应简洁明了，描述更改的目的。
3. **使用分支**：为每个功能或修复创建独立的分支。
4. **定期拉取更新**：在开始工作前拉取远程仓库的最新更改。
5. **避免直接推送到主分支**：使用 Pull Request 或 Merge Request 进行代码审查。

---

## 总结
Git 是一个强大的版本控制工具，掌握其基本用法和最佳实践可以显著提高开发效率和代码质量。通过合理使用分支、提交和远程仓库操作，可以更好地管理项目并与团队协作。
