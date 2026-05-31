# Git 与 GitHub 详细介绍与使用方法

> 适合对象：**零基础到中级用户**，尤其是计算机专业、软件工程、课程设计、个人项目与团队协作场景。

------

## 一、Git 是什么？

### 1. Git 的定义

**Git 是一个分布式版本控制系统（DVCS）**，用于：

- 记录代码（或文件）的**历史变化**
- 支持多人**协同开发**
- 可以随时**回退到任意历史版本**

简单理解：

> Git = 给代码拍“时间快照”的工具

------

### 2. 为什么要用 Git？

如果不用 Git，常见问题包括：

- 文件名混乱：`final.cpp`、`final2.cpp`、`final_真的最终.cpp`
- 改错代码后无法回退
- 多人改同一份代码，互相覆盖

Git 可以解决：

- ✅ 自动保存每一次修改
- ✅ 清楚知道“谁在什么时候改了什么”
- ✅ 支持分支开发，互不干扰

------

### 3. Git 的核心特点

| 特点       | 说明                   |
| ---------- | ---------------------- |
| 分布式     | 每个人本地都有完整仓库 |
| 快照式存储 | 每次提交保存整体状态   |
| 分支强大   | 创建/切换分支非常轻量  |
| 离线可用   | 本地即可提交、查看历史 |

------

## 二、GitHub 是什么？

### 1. GitHub 的定义

**GitHub 是一个基于 Git 的代码托管平台**，主要功能：

- 托管 Git 仓库
- 团队协作开发
- Issue（问题管理）
- Pull Request（代码审查）

> 类比：
>
> - Git = 本地记账软件
> - GitHub = 云端共享账本

------

### 2. Git 和 GitHub 的关系

| Git      | GitHub          |
| -------- | --------------- |
| 工具     | 平台            |
| 本地运行 | 云端服务        |
| 版本控制 | 代码托管 + 协作 |

⚠️ 注意：

- **Git 不等于 GitHub**
- 不联网也能用 Git

------

## 三、Git 的基本概念（非常重要）

### 1. 三个区域

```
工作区（Working Directory）
      ↓ git add
暂存区（Staging Area）
      ↓ git commit
本地仓库（Repository）
```

| 区域     | 作用               |
| -------- | ------------------ |
| 工作区   | 实际编辑文件的地方 |
| 暂存区   | 准备提交的文件     |
| 本地仓库 | 保存历史版本       |

------

### 2. 仓库（Repository）

一个 Git 仓库 = 一个被 Git 管理的项目目录

包含：

- 所有文件
- 所有历史记录
- 所有分支信息

------

### 3. 提交（Commit）

一次提交代表：

- 某一时刻
- 对项目的一组修改

每个 commit 都有：

- 唯一 ID（hash）
- 提交人
- 提交说明

------

### 4. 分支（Branch）

分支用于并行开发：

- `main / master`：主分支
- `dev`：开发分支
- `feature-xxx`：功能分支

> 分支 = 平行世界

------

## 四、Git 的安装与初始化

### 1. 安装 Git

- Windows：安装 Git for Windows
- macOS：`brew install git`
- Linux：`sudo apt install git`

安装完成后验证：

```bash
git --version
```

------

### 2. 初始配置（只需一次）

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱"
```

查看配置：

```bash
git config --list
```

------

## 五、本地 Git 的完整使用流程

### 1. 创建仓库

#### 方式一：新项目

```bash
git init
```

#### 方式二：已有远程仓库

```bash
git clone 仓库地址
```

------

### 2. 查看状态

```bash
git status
```

常见状态：

- 未跟踪（Untracked）
- 已修改（Modified）
- 已暂存（Staged）

------

### 3. 添加到暂存区

```bash
git add 文件名
git add .    # 添加所有文件
```

------

### 4. 提交到本地仓库

```bash
git commit -m "提交说明"
```

提交说明规范：

- 简洁
- 描述做了什么

------

### 5. 查看历史记录

```bash
git log
git log --oneline
```

------

## 六、分支操作（核心技能）

### 1. 查看分支

```bash
git branch
```

### 2. 创建分支

```bash
git branch dev
```

### 3. 切换分支

```bash
git checkout dev
# 或
git switch dev
```

### 4. 创建并切换

```bash
git checkout -b feature-login
```

### 5. 合并分支

```bash
git checkout main
git merge dev
```

------

### 6. 冲突（Conflict）

产生原因：

- 两个分支修改了**同一行代码**

解决步骤：

1. 手动编辑冲突文件
2. 删除冲突标记
3. 重新 add + commit

------

## 七、GitHub 的使用流程

### 1. 创建远程仓库

在 GitHub 上点击 **New Repository**

------

### 2. 关联远程仓库

```bash
git remote add origin 仓库地址
```

查看远程：

```bash
git remote -v
```

------

### 3. 推送代码到 GitHub

```bash
git push -u origin main
```

------

### 4. 从远程拉取代码

```bash
git pull origin main
```

------

## 八、团队协作（GitHub 核心）

### 1. Fork（复刻）

- 把别人的仓库复制到自己账号

### 2. Pull Request（PR）

流程：

1. Fork 项目
2. 本地修改
3. Push 到自己仓库
4. 提交 Pull Request

------

### 3. Issue

用于：

- 提 Bug
- 讨论需求
- 任务分配

------

## 九、常用命令速查表

```bash
git init
git status
git add .
git commit -m "msg"
git log --oneline
git branch
git checkout -b dev
git merge dev
git push
git pull
```

------

## 十、学习建议（非常重要）

1. **多用命令行**，不要只依赖 GUI
2. 每次 commit 都写清楚说明
3. 不要在 main 分支直接写大功能
4. 多看 `git status`

------

如果你愿意，我可以：

- ✅ 给你画一张 **Git 工作流程图**
- ✅ 用你熟悉的 **C++ / Three.js 项目**举例
- ✅ 教你 **课程实验/小组作业** 的 Git 使用规范
- ✅ 专门讲 **Git 冲突怎么解决**

你可以直接告诉我你的使用场景 👍