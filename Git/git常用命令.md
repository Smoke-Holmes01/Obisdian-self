# Git 常用命令速查手册

## 一、配置

```bash
# 用户信息
git config --global user.name "Your Name"           # 设置全局用户名
git config --global user.email "your@email.com"     # 设置全局邮箱
git config --local user.name "Project Name"         # 仅当前仓库
git config --global core.editor "code --wait"       # 设置默认编辑器
git config --global merge.tool "vimdiff"            # 设置合并工具

# 查看配置
git config --list                                    # 列出所有配置
git config --global --list                           # 全局配置
git config --local --list                            # 当前仓库配置
git config user.name                                 # 查看单项配置

# 别名
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.lg "log --graph --oneline --all --decorate"

# 换行符 & 编码
git config --global core.autocrlf true               # Windows: true, Mac/Linux: input
git config --global core.safecrlf true
git config --global i18n.commitencoding utf-8
git config --global i18n.logoutputencoding utf-8

# 代理
git config --global http.proxy http://proxy:8080
git config --global https.proxy http://proxy:8080
git config --global --unset http.proxy               # 取消代理
```

---

## 二、创建与初始化

```bash
git init                                             # 初始化新仓库
git init <目录名>                                     # 在指定目录初始化
git init --bare <目录名>                              # 创建裸仓库（服务器端用）
git clone <url>                                      # 克隆远程仓库
git clone <url> <目录名>                              # 克隆到指定目录
git clone --depth 1 <url>                            # 浅克隆（只拉最近一次提交）
git clone --branch <分支名> <url>                     # 克隆指定分支
git clone --recurse-submodules <url>                 # 克隆并初始化子模块
```

---

## 三、基础操作

### 3.1 文件状态

```bash
git status                                           # 查看工作区状态
git status -s                                        # 精简输出（Short）
git status -b                                        # 显示分支信息
```

### 3.2 添加 / 移除

```bash
git add <文件>                                       # 添加文件到暂存区
git add .                                            # 添加所有变更
git add -A                                           # 同上，添加所有（包括删除）
git add -p                                           # 交互式逐块添加（patch mode）
git add -i                                           # 交互式添加
git add -f <文件>                                     # 强制添加（忽略 .gitignore）
git add --all -- ':!node_modules'                    # 添加全部但排除某目录
git add --dry-run .                                  # 试运行，看会添加什么但不实际执行

git rm <文件>                                        # 删除工作区 + 暂存区
git rm --cached <文件>                                # 仅从暂存区删除（保留工作区文件）
git rm -r <目录>                                      # 递归删除目录
git rm -f <文件>                                      # 强制删除（有未暂存修改时用）

git mv <旧名> <新名>                                  # 重命名文件
```

### 3.3 提交

```bash
git commit -m "提交信息"                              # 提交暂存区
git commit -a -m "提交信息"                           # 跳过暂存区，直接提交所有已跟踪文件
git commit --amend -m "新信息"                        # 修改最近一次提交的信息
git commit --amend --no-edit                        # 不改信息，把暂存区追加到上次提交
git commit --allow-empty                            # 允许空提交
git commit --date="2024-01-01 12:00:00"             # 指定提交时间
git commit -m "feat: 添加用户登录功能"                  # 推荐：约定式提交格式
```

### 3.4 查看差异

```bash
git diff                                             # 工作区 vs 暂存区
git diff --staged                                    # 暂存区 vs 上次提交（同 --cached）
git diff HEAD                                        # 工作区 vs 最近一次提交
git diff <分支1> <分支2>                              # 两个分支差异
git diff <分支1>..<分支2>                             # 同上
git diff <分支1>...<分支2>                            # 分支2 有但分支1 没有的变更
git diff <提交1> <提交2>                              # 两个提交之间的差异
git diff --stat                                      # 只显示变更统计（文件数、行数）
git diff --name-only                                 # 只显示变更的文件名
git diff --word-diff                                 # 以单词为单位显示差异
git diff --check                                     # 检查是否有空白错误
git diff -w                                          # 忽略空白差异
```

---

## 四、分支管理

```bash
# 查看分支
git branch                                           # 本地分支列表
git branch -v                                        # 显示分支及最近提交
git branch -vv                                       # 显示追踪关系（上游分支）
git branch -r                                        # 远程分支列表
git branch -a                                        # 所有分支（本地+远程）
git branch --merged                                  # 已合并到当前分支的
git branch --no-merged                               # 未合并的

# 创建 / 切换
git branch <分支名>                                   # 创建分支
git branch <分支名> <提交ID>                           # 从指定提交创建分支
git checkout <分支名>                                 # 切换分支
git checkout -b <分支名>                              # 创建并切换
git switch <分支名>                                   # 切换（新版 Git 推荐）
git switch -c <分支名>                                # 创建并切换

# 重命名
git branch -m <旧名> <新名>                           # 重命名分支
git branch -M <新名>                                  # 强制重命名当前分支

# 删除
git branch -d <分支名>                                # 删除分支（已合并才能删）
git branch -D <分支名>                                # 强制删除分支
git push origin --delete <分支名>                     # 删除远程分支
git push origin :<分支名>                             # 同上（老语法）

# 关联追踪
git branch -u origin/<分支名>                         # 设置上游分支
git branch --set-upstream-to=origin/<分支名>           # 同上
git branch --unset-upstream                          # 取消上游关联
```

---

## 五、远程仓库

```bash
git remote -v                                         # 查看远程仓库
git remote add <别名> <url>                           # 添加远程仓库
git remote remove <别名>                              # 删除远程仓库
git remote rename <旧名> <新名>                        # 重命名
git remote set-url <别名> <新url>                      # 修改远程地址
git remote show <别名>                                 # 查看远程详情
git remote prune origin                               # 清理远程已删除的分支引用

# 拉取
git fetch                                            # 拉取远程所有分支
git fetch origin                                     # 拉取指定远程
git fetch origin <分支名>                             # 拉取指定分支
git fetch --all                                      # 拉取所有远程
git fetch --prune                                    # 拉取并清理已删除的远程分支引用
git fetch --tags                                     # 拉取所有标签

git pull                                             # fetch + merge
git pull --rebase                                    # fetch + rebase（推荐，线性历史）
git pull origin <分支名>                              # 拉取指定分支
git pull --no-commit                                 # 拉取但不自动提交
git pull --ff-only                                   # 仅快进合并，失败则放弃

# 推送
git push                                             # 推送到默认远程
git push origin <分支名>                              # 推送分支
git push -u origin <分支名>                           # 推送并设置上游（首次推送常用）
git push --all                                       # 推送所有分支
git push --tags                                      # 推送所有标签
git push origin --delete <分支名>                     # 删除远程分支
git push --force                                     # 强制推送（危险！）
git push --force-with-lease                          # 安全强制推送（比 --force 安全）
git push --atomic origin <分支1> <分支2>               # 原子推送（都成功或都不成功）
```

---

## 六、撤销与回退

```bash
# 工作区撤销（未暂存）
git restore <文件>                                    # 撤销工作区修改（新版）
git checkout -- <文件>                                # 同上（老版）
git restore .                                        # 撤销所有工作区修改
git restore --source HEAD~2 <文件>                    # 还原到两个版本前的状态

# 暂存区撤销
git restore --staged <文件>                           # 取消暂存（新版）
git reset HEAD <文件>                                 # 同上（老版）
git reset                                            # 取消所有暂存

# 提交回退
git reset --soft HEAD~1                              # 撤销上次提交，保留暂存区
git reset --mixed HEAD~1                             # 撤销上次提交，保留工作区（默认）
git reset --hard HEAD~1                              # 撤销上次提交，丢弃所有修改（危险！）

git reset --hard <提交ID>                             # 回退到指定提交
git reset --soft <提交ID>                             # 把 HEAD 移到指定提交，之后所有变更留在暂存区
git reset --keep <提交ID>                             # 保留工作区未提交的修改

# revert（安全回退：通过新提交撤销）
git revert HEAD                                      # 撤销最近一次提交
git revert <提交ID>                                  # 撤销指定提交
git revert --no-commit <提交ID>                       # 不自动提交（多个 revert 合并用）
git revert -m 1 <合并提交ID>                          # 撤销合并提交

# 清理
git clean -n                                         # 试运行，显示会删除什么
git clean -f                                         # 删除未跟踪文件
git clean -fd                                        # 删除未跟踪文件 + 目录
git clean -fx                                        # 删除包括被 .gitignore 忽略的文件
git clean -nd                                        # 试运行，显示未跟踪目录
```

---

## 七、日志与历史

```bash
# 基本日志
git log                                              # 提交历史
git log --oneline                                    # 一行显示
git log --graph                                      # 图形化显示分支
git log --all                                        # 显示所有分支
git log -n 5                                         # 最近 5 条

# 格式化输出
git log --oneline --graph --all --decorate            # 经典完整视图
git log --pretty=format:"%h - %an, %ar : %s"         # 自定义格式
  # 常用占位符: %h(短哈希) %H(完整哈希) %an(作者名) %ae(作者邮箱)
  #            %ad(日期) %ar(相对日期) %s(提交信息) %d(ref名称)

# 过滤
git log --author="用户名"                             # 按作者过滤
git log --since="2024-01-01"                         # 从某日期起
git log --until="2024-06-30"                         # 到某日期止
git log --grep="关键字"                               # 按提交信息搜索
git log -S "函数名"                                   # 按代码内容搜索（Pickaxe）
git log -G "正则"                                    # 按正则搜索变更
git log -- <文件路径>                                 # 查看某个文件的提交历史
git log -- <目录>                                    # 查看某个目录的提交历史
git log --no-merges                                  # 排除合并提交
git log --merges                                     # 只显示合并提交

# 统计
git log --stat                                       # 显示文件变更统计
git log --shortstat                                  # 精简统计
git log --numstat                                    # 数字格式统计

# 追溯
git blame <文件>                                     # 每行谁改的
git blame -L 10,20 <文件>                            # 查看指定行范围
git blame -w <文件>                                  # 忽略空白变动
git blame -C <文件>                                  # 检测代码复制来源
```

---

## 八、标签

```bash
# 创建
git tag <标签名>                                      # 轻量标签
git tag -a <标签名> -m "说明"                          # 附注标签（推荐）
git tag -a <标签名> <提交ID> -m "说明"                  # 为历史提交打标签

# 查看
git tag                                              # 列出标签
git tag -l "v2.*"                                    # 按模式搜索
git show <标签名>                                     # 查看标签详情

# 推送
git push origin <标签名>                              # 推送单个标签
git push origin --tags                               # 推送所有标签

# 删除
git tag -d <标签名>                                   # 删除本地标签
git push origin --delete <标签名>                      # 删除远程标签
git push origin :refs/tags/<标签名>                    # 同上（老语法）

# 检出
git checkout <标签名>                                 # 切换到标签（分离 HEAD）
git checkout -b <新分支名> <标签名>                     # 从标签创建分支
```

---

## 九、合并与变基

```bash
# 合并
git merge <分支名>                                    # 合并分支到当前
git merge --no-ff <分支名>                            # 禁止快进合并（保留分支历史）
git merge --ff-only <分支名>                          # 仅快进合并
git merge --squash <分支名>                           # 压扁合并（把所有提交合并成一次）
git merge --abort                                    # 中止合并（有冲突时）
git merge --continue                                 # 继续合并（解决冲突后）

# 变基
git rebase <分支名>                                   # 变基到目标分支
git rebase -i HEAD~3                                 # 交互式变基，修改最近 3 次提交
git rebase --onto <目标> <起点> <终点>                  # 精选变基
git rebase --abort                                   # 中止变基
git rebase --continue                                # 继续变基（解决冲突后）
git rebase --skip                                    # 跳过当前提交

# 交互式变基常用操作
# pick   = 保留提交
# reword = 修改提交信息
# edit   = 保留提交但暂停以修改内容
# squash = 合并到前一个提交
# fixup  = 合并但不保留提交信息
# drop   = 删除提交
```

---

## 十、储藏 (Stash)

```bash
git stash                                            # 储藏当前修改
git stash push -m "说明"                              # 带说明储藏
git stash -u                                         # 包含未跟踪文件（--include-untracked）
git stash -a                                         # 包含所有文件（--all，含 gitignore 文件）

git stash list                                       # 查看储藏列表
git stash show                                       # 查看最新储藏内容
git stash show -p                                    # 查看详细 diff

git stash pop                                        # 恢复并删除最新储藏
git stash apply                                      # 恢复但不删除
git stash apply stash@{2}                            # 恢复指定储藏
git stash drop stash@{1}                             # 删除指定储藏
git stash clear                                      # 清空所有储藏
git stash branch <分支名>                              # 从储藏创建分支
```

---

## 十一、子模块 (Submodule)

```bash
git submodule add <url> <路径>                        # 添加子模块
git submodule init                                   # 初始化子模块配置
git submodule update                                 # 更新子模块到记录版本
git submodule update --init --recursive              # 递归初始化更新所有子模块
git submodule sync                                   # 同步远程 URL 变更
git submodule foreach git pull origin main           # 在每个子模块中执行命令
git submodule status                                 # 查看子模块状态
```

---

## 十二、远程同步高级

```bash
# 镜像仓库
git clone --mirror <url> <目录名>                     # 完整镜像克隆
git push --mirror <url>                              # 推送完整镜像

# 同步上游仓库（fork 场景）
git remote add upstream <原仓库url>                   # 添加上游仓库
git fetch upstream                                   # 拉取上游
git checkout main && git merge upstream/main         # 合并上游到本地
```

---

## 十三、重置与恢复

```bash
# ORPHAN 分支（独立分支，无共同历史）
git checkout --orphan <分支名>                        # 创建无历史分支

# 恢复文件到指定版本
git restore --source <提交ID> -- <文件>                # 指定版本恢复

# Reflog（救命稻草！记录所有 HEAD 变化）
git reflog                                           # 查看所有 HEAD 操作历史
git reflog --relative-date                           # 带相对时间
git reset --hard HEAD@{2}                            # 恢复到 reflog 中的位置
git reflog expire --expire=now --all                 # 清空 reflog

# 垃圾回收
git gc                                               # 优化仓库
git gc --aggressive                                  # 激进优化
git fsck                                             # 检查仓库完整性
git count-objects -vH                                # 查看仓库大小
```

---

## 十四、补丁与归档

```bash
# 生成补丁
git format-patch <提交ID>                             # 从某个提交开始生成补丁
git format-patch -1 HEAD                             # 生成最近一次提交的补丁
git format-patch --stdout <提交ID> > patch.diff       # 输出到单个文件

# 应用补丁
git apply patch.diff                                 # 应用补丁
git apply --check patch.diff                         # 检查补丁是否可应用
git am patch.diff                                    # 作为邮件应用补丁

# 归档
git archive -o project.zip HEAD                      # 打包当前 HEAD
git archive --format=tar --prefix=project/ HEAD | gzip > project.tar.gz
```

---

## 十五、高级工具

```bash
# Bisect（二分查找引入 bug 的提交）
git bisect start                                      # 开始二分查找
git bisect bad                                        # 标记当前为坏
git bisect good <提交ID>                              # 标记某个提交为好
git bisect reset                                      # 结束查找
git bisect run <脚本>                                 # 自动运行脚本判断

# Grep（仓库内搜索）
git grep "关键字"                                     # 搜索工作区
git grep "关键字" <提交ID>                             # 搜索历史版本
git grep -n "关键字"                                  # 显示行号
git grep -i "关键字"                                  # 忽略大小写
git grep --name-only "关键字"                          # 只显示文件名

# Cherry-pick（精选提交）
git cherry-pick <提交ID>                              # 把其他分支的某次提交应用到当前
git cherry-pick <提交1> <提交2>                        # 应用多个提交
git cherry-pick <开始提交>..<结束提交>                  # 范围精选
git cherry-pick -x <提交ID>                           # 保留来源信息
git cherry-pick --continue                            # 解决冲突后继续
git cherry-pick --abort                               # 中止

# Worktree（同时检出多个分支）
git worktree add <路径> <分支名>                       # 添加工作树
git worktree list                                     # 列出工作树
git worktree remove <路径>                            # 移除
git worktree prune                                   # 清理已删除的工作树引用
```

---

## 十六、Git 钩子（Hooks）

`.git/hooks/` 目录下的可执行脚本，常用钩子：

| 钩子 | 触发时机 |
|------|----------|
| `pre-commit` | `git commit` 前，可用于 lint/测试 |
| `prepare-commit-msg` | 提交信息编辑前 |
| `commit-msg` | 提交信息编辑后 |
| `post-commit` | `git commit` 后 |
| `pre-push` | `git push` 前 |
| `pre-receive` | 服务端接收推送前 |
| `update` | 服务端更新分支前 |
| `post-receive` | 服务端接收推送后 |

```bash
# 示例：pre-commit 钩子（运行单元测试）
#!/bin/sh
npm test
if [ $? -ne 0 ]; then
    echo "❌ 测试未通过，提交取消"
    exit 1
fi
```

> 使用 `git init` 后 `.git/hooks/` 下会有 `.sample` 示例文件，去掉后缀即可启用。

---

## 十七、Git 忽略规则 (.gitignore)

常见模式：

```
# 注释
*.log                  # 所有 .log 文件
build/                 # build 目录
dist/                  # dist 目录
node_modules/          # node_modules
.env                   # 环境变量文件
!.env.example          # 但不忽略 .env.example
/TODO                  # 仅仓库根目录下的 TODO
docs/*.html            # docs 下所有 .html（不递归）
docs/**/*.html         # docs 下所有 .html（递归）
*.[oa]                 # .o 和 .a 文件
```

```bash
# 查看忽略规则生效情况
git check-ignore -v <文件>
```

---

## 十八、常见工作流

### 日常提交

```bash
git checkout -b feature/my-feature    # 从 main 切出功能分支
git add -p                            # 交互式暂存
git commit -m "feat: 实现 X 功能"      # 提交
git rebase main                        # 同步主分支
git push -u origin feature/my-feature # 推送
# → 发起 PR/Merge Request
```

### 紧急修复

```bash
git stash                             # 储藏当前工作
git checkout -b hotfix/crash main     # 从 main 切修复分支
# ... 修复代码 ...
git commit -a -m "fix: 修复崩溃"       # 提交
git push origin hotfix/crash          # 推送
git checkout feature/my-feature       # 回到原分支
git stash pop                         # 恢复工作
```

### 后悔药系列

```bash
# 改最近一次提交信息
git commit --amend -m "新信息"

# 不小心 commit 了，想撤回但保留修改
git reset --soft HEAD~1

# 不小心 commit 了，想完全丢弃
git reset --hard HEAD~1

# 已在远程，想撤销
git revert HEAD
git push

# 误删了分支但记得哈希
git reflog            # 找到哈希
git checkout -b <分支名> <哈希>
```

### 合并多个提交

```bash
git rebase -i HEAD~4   # 合并最近 4 次提交
# 编辑：将后三个 pick 改为 squash 或 fixup
# pick  a123456  feat: A
# squash b234567  feat: B
# squash c345678  feat: C
# squash d456789  feat: D
```

---

## 十九、Git 对象与底层命令

```bash
# 对象存储
git hash-object <文件>                            # 计算文件 Git 哈希
git hash-object -w <文件>                         # 计算并写入对象仓库
git cat-file -p <哈希>                            # 查看对象内容
git cat-file -t <哈希>                            # 查看对象类型（blob/tree/commit）
git cat-file -s <哈希>                            # 查看对象大小

# 树对象
git write-tree                                    # 从暂存区写入树对象
git ls-tree <哈希>                                # 列出树对象内容

# 引用
git rev-parse HEAD                                # 解析 HEAD 指向的哈希
git rev-parse --abbrev-ref HEAD                   # 获取当前分支名
git symbolic-ref HEAD                             # 查看 HEAD 引用的分支
git update-ref refs/heads/<分支名> <哈希>           # 手动更新引用
```

---

## 二十、实用技巧

```bash
# 快速查看某次提交改了哪些文件
git show --name-only <提交ID>

# 查找谁改了一行代码
git blame -L <行号>,<行号> <文件>

# 找出两个分支的共同祖先
git merge-base <分支1> <分支2>

# 统计个人代码量
git log --author="用户名" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "新增: %s, 删除: %s, 净增: %s\n", add, subs, loc }'

# 查看最近一次提交的变更列表
git show --stat HEAD

# 从某次提交摘出特定文件
git checkout <提交ID>^-- <文件路径>

# 找出所有未合并到主分支的提交
git log --oneline main..HEAD

# 对比两个分支的文件列表
git diff --name-status main..feature

# 查看某个 commit 所属的标签
git describe <提交ID>
git describe --tags --abbrev=0

# 在当前分支基础上创建一个空的 orphan 分支
git checkout --orphan <新分支名>
git rm -rf .
```

---

## 附录：参数速查

| 参数 | 含义 |
|------|------|
| `-a` / `--all` | 全部 |
| `-b` | 创建分支 (`checkout -b`) |
| `-d` / `-D` | 删除分支（安全/强制） |
| `-f` | 强制 |
| `-i` | 交互式 |
| `-m` | 移动/重命名 / 合并信息 |
| `-n` | 试运行/不自动提交 |
| `-o` | 仅 (`fetch -o` = `--prune`) |
| `-p` | 补丁模式（逐块操作） |
| `-r` | 远程分支 |
| `-s` | 精简输出 |
| `-u` | 设置上游 |
| `-v` | 详细信息 |
| `--tags` | 标签相关 |
| `--force-with-lease` | 安全强制推送 |
| `--no-ff` | 禁止快进合并 |
| `--squash` | 压扁合并 |
| `--rebase` | 变基方式拉取 |
| `--prune` | 清理已删除的远程引用 |
| `--depth <N>` | 浅克隆深度 |
```
