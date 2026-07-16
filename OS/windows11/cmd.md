# CMD 基础命令速查

> [!NOTE]
> 本页收录 Windows 命令提示符（CMD）的日常高频命令。路径含空格时请使用双引号；带省略号的内容请替换为实际名称。

## 1. 帮助与终端

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 查看内置命令 | help | 显示 CMD 内置命令列表 |
| 查看某命令说明 | &lt;命令&gt; /? | 例如 dir /? |
| 清空屏幕 | cls | 不会删除历史记录 |
| 查看命令位置 | where &lt;程序名&gt; | 例如 where git |
| 查看命令历史 | doskey /history | 查看当前会话已执行的命令 |

~~~cmd
:: 查看 Windows 版本与系统信息
ver
systeminfo

:: 在新窗口中运行命令
start cmd
~~~

## 2. 导航与目录

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 查看当前目录 | cd | 也可使用 chdir |
| 列出文件 | dir | dir /a 显示隐藏文件；dir /b 仅显示名称 |
| 进入目录 | cd &lt;目录&gt; | 例如 cd Documents |
| 切换盘符 | D: | 直接输入目标盘符加冒号 |
| 跨盘切换目录 | cd /d D:\Work | 同时切换盘符和目录 |
| 返回上级目录 | cd .. | 可连续使用，如 cd ..\.. |
| 创建目录 | mkdir &lt;目录名&gt; | md 是同义写法 |
| 删除空目录 | rmdir &lt;目录名&gt; | rd 是同义写法 |

~~~cmd
:: 路径有空格时加双引号
cd /d "C:\Program Files"

:: 一次创建多层目录
mkdir project\src\assets
~~~

## 3. 文件操作与查看

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 复制文件 | copy &lt;源&gt; &lt;目标&gt; | 适合单个或少量文件 |
| 复制目录 | xcopy &lt;源目录&gt; &lt;目标目录&gt; /e /i | /e 包含空目录；/i 视目标为目录 |
| 移动或重命名 | move &lt;源&gt; &lt;目标&gt; | 同目录内可用于重命名 |
| 删除文件 | del &lt;文件&gt; | del /q 不询问确认 |
| 删除目录树 | rmdir /s /q &lt;目录&gt; | 会递归删除，请先确认路径 |
| 查看文本 | type &lt;文件&gt; | 适合短文本文件 |
| 分页查看 | more &lt;文件&gt; | 按空格翻页 |
| 比较文本 | fc &lt;文件1&gt; &lt;文件2&gt; | 显示两份文本的差异 |

~~~cmd
:: 复制并重命名文件
copy report.txt report-backup.txt

:: 查找当前目录下所有 .log 文件
dir /s /b *.log
~~~

> [!WARNING]
> del 和 rmdir /s /q 不会移入回收站。执行前先用 dir 确认目标路径。

## 4. 搜索与重定向

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 在文本中查找 | findstr /s /i /n "关键字" *.txt | /s 递归、/i 忽略大小写、/n 显示行号 |
| 输出到文件 | &lt;命令&gt; > 输出.txt | 覆盖写入 |
| 追加到文件 | &lt;命令&gt; >> 输出.txt | 在文件末尾追加 |
| 管道传递输出 | <命令1> | <命令2> | 将前一命令输出交给后一命令 |

~~~cmd
:: 在当前目录及子目录的 Markdown 文件中搜索“TODO”
findstr /s /i /n "TODO" *.md

:: 将当前目录文件清单保存到文件
dir /s /b > file-list.txt
~~~

## 5. 环境变量与路径

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 查看全部变量 | set | |
| 查看单个变量 | echo %变量名% | 例如 echo %PATH% |
| 临时设置变量 | set 变量名=值 | 仅当前 CMD 窗口有效 |
| 永久设置用户变量 | setx 变量名 "值" | 在新开终端中生效 |
| 临时追加 PATH | set PATH=%PATH%;C:\Tools | 仅当前会话有效 |

~~~cmd
:: 设置当前会话的项目环境
set NODE_ENV=development
echo %NODE_ENV%
~~~

> [!TIP]
> setx 写入的是持久变量，但不会刷新当前终端；关闭并重新打开终端后再验证。

## 6. 进程与任务

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 查看进程 | tasklist | tasklist /fi "imagename eq node.exe" 可按名称过滤 |
| 结束进程 | taskkill /im &lt;程序名&gt; /f | /f 强制结束 |
| 按 PID 结束 | taskkill /pid &lt;PID&gt; /f | PID 可从 tasklist 获取 |
| 查看已计划任务 | schtasks /query | 显示计划任务清单 |

~~~cmd
:: 查找并结束某个 Node.js 进程
tasklist /fi "imagename eq node.exe"
taskkill /im node.exe /f
~~~

## 7. 网络与系统信息

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 查看 IP 配置 | ipconfig | ipconfig /all 显示完整配置 |
| 刷新 DNS 缓存 | ipconfig /flushdns | |
| 测试连通性 | ping &lt;主机&gt; | 例如 ping 1.1.1.1 |
| 查询 DNS | nslookup &lt;域名&gt; | |
| 查看端口连接 | netstat -ano | -o 显示 PID |
| 追踪路由 | tracert &lt;主机&gt; | |
| 查看当前用户 | whoami | |
| 查看磁盘空间 | wmic logicaldisk get name,freespace,size | 旧版工具，部分新系统可能不可用 |

~~~cmd
:: 找出占用 3000 端口的 PID，再结束该进程
netstat -ano | findstr :3000
taskkill /pid <PID> /f
~~~

## 8. 常用组合

~~~cmd
:: 创建空文件
type nul > notes.txt

:: 将命令输出同时保存为日志
command > output.log 2>&1

:: 递归搜索文件名后分页查看
dir /s /b *keyword* | more
~~~
