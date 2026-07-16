# PowerShell 7 基础命令速查

> [!NOTE]
> 本页面向 PowerShell 7（pwsh）。PowerShell 会在管道中传递对象，而不只是文本；路径含空格时请使用单引号或双引号。

## 1. 帮助、版本与别名

| 目的 | 完整 cmdlet | 常用别名 |
| --- | --- | --- |
| 查看版本 | $PSVersionTable | |
| 查找命令 | Get-Command <名称> | gcm |
| 查看帮助 | Get-Help <命令> -Examples | help |
| 在线帮助 | Get-Help <命令> -Online | |
| 查看别名 | Get-Alias | gal |
| 查询别名含义 | Get-Alias ls | |

~~~powershell
Get-Help Get-ChildItem -Examples
Get-Command *service*
~~~

> [!TIP]
> ls、dir、cat、cd、rm 等是兼容别名；学习和脚本中优先使用完整 cmdlet，以便语义清晰、跨环境更稳定。

## 2. 导航与文件

| 目的 | 完整 cmdlet | 常用别名 |
| --- | --- | --- |
| 查看当前位置 | Get-Location | pwd |
| 切换目录 | Set-Location <路径> | cd |
| 列出项目 | Get-ChildItem | ls、dir、gci |
| 创建目录 | New-Item -ItemType Directory <名称> | mkdir |
| 新建空文件 | New-Item -ItemType File <名称> | ni |
| 复制 | Copy-Item <源> <目标> | cp、copy |
| 移动/重命名 | Move-Item <源> <目标> | mv、move |
| 重命名 | Rename-Item <旧名> <新名> | ren |
| 删除 | Remove-Item <路径> | rm、del |
| 查看文本 | Get-Content <文件> | cat、gc |

~~~powershell
# 进入含空格的目录
Set-Location 'C:\Program Files'

# 创建目录与文件
New-Item -ItemType Directory -Path .\project
New-Item -ItemType File -Path .\project\README.md

# 递归列出 Markdown 文件
Get-ChildItem -Path . -Filter '*.md' -Recurse
~~~

> [!WARNING]
> Remove-Item -Recurse -Force 会递归且强制删除。先使用 Get-ChildItem 确认目标，再执行删除。

## 3. 搜索、筛选与对象管道

| 目的 | 完整 cmdlet | 说明 |
| --- | --- | --- |
| 搜索文本 | Select-String -Path <文件> -Pattern <关键字> | 类似 grep |
| 按属性筛选 | Where-Object { 条件 } | 别名为 where、? |
| 选择属性 | Select-Object <属性> | 别名为 select |
| 排序 | Sort-Object <属性> | 别名为 sort |
| 统计 | Measure-Object | 别名为 measure |
| 格式化表格 | Format-Table -AutoSize | 别名为 ft |

~~~powershell
# 在 Markdown 文件中查找 TODO，并显示行号
Select-String -Path .\*.md -Pattern 'TODO'

# 找出大于 100 MB 的文件，按大小降序排列
Get-ChildItem -File -Recurse |
  Where-Object { $_.Length -gt 100MB } |
  Sort-Object Length -Descending |
  Select-Object Name, Length, LastWriteTime

# 统计当前目录下的文件数量
Get-ChildItem -File | Measure-Object
~~~

## 4. 变量、输出与文件编码

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 定义变量 | $name = 'Nyx' | 变量以 $ 开头 |
| 输出变量 | Write-Output $name | 也可直接输入 $name |
| 字符串插值 | "Hello, $name" | 双引号会展开变量 |
| 读取文件 | Get-Content -Path .\a.txt | 默认按行返回字符串数组 |
| 写入文件 | Set-Content -Path .\a.txt -Value '内容' -Encoding utf8 | 覆盖写入 |
| 追加文件 | Add-Content -Path .\a.txt -Value '新行' -Encoding utf8 | 追加写入 |

~~~powershell
$name = 'Nyx'
"Hello, $name"

# 读取、修改并保存文本
$content = Get-Content -Path .\notes.txt -Raw
$content = $content -replace 'old', 'new'
Set-Content -Path .\notes.txt -Value $content -Encoding utf8
~~~

## 5. 进程与服务

| 目的 | 完整 cmdlet | 常用别名 |
| --- | --- | --- |
| 查看进程 | Get-Process | ps、gps |
| 按名称查进程 | Get-Process -Name <名称> | |
| 结束进程 | Stop-Process -Name <名称> | kill、spps |
| 查看服务 | Get-Service | gsv |
| 启动服务 | Start-Service -Name <名称> | sasv |
| 停止服务 | Stop-Service -Name <名称> | spsv |

~~~powershell
# 查找并停止 Node.js 进程
Get-Process -Name node
Stop-Process -Name node -Force

# 查看运行中的服务
Get-Service | Where-Object Status -eq 'Running'
~~~

## 6. 网络与系统

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 查看 IP 配置 | Get-NetIPConfiguration | |
| 测试连接 | Test-Connection <主机> | 类似 ping |
| 测试端口 | Test-NetConnection <主机> -Port <端口> | 别名 tnc |
| 查询 DNS | Resolve-DnsName <域名> | |
| 查看监听端口 | Get-NetTCPConnection -State Listen | |
| 查看系统信息 | Get-ComputerInfo | 信息较多，可按需筛选 |
| 当前用户 | whoami | 外部命令，可直接在 PowerShell 使用 |

~~~powershell
Test-Connection 1.1.1.1 -Count 4
Test-NetConnection github.com -Port 443
Get-NetTCPConnection -LocalPort 3000
~~~

## 7. 模块与实用技巧

| 目的 | 命令 | 说明 |
| --- | --- | --- |
| 列出已安装模块 | Get-InstalledModule | 需要 PowerShellGet |
| 查找模块 | Find-Module <名称> | |
| 安装当前用户模块 | Install-Module <名称> -Scope CurrentUser | 首次安装可能需要确认 |
| 导入模块 | Import-Module <名称> | |
| 执行脚本 | .\script.ps1 | 当前目录脚本必须显式写 .\ |
| 查看执行策略 | Get-ExecutionPolicy -List | |

~~~powershell
# 通过管道查看可用命令，再按名称排序
Get-Command -CommandType Cmdlet |
  Sort-Object Name |
  Select-Object -First 20 Name, ModuleName

# 将目录清单导出为 CSV
Get-ChildItem -File |
  Select-Object Name, Length, LastWriteTime |
  Export-Csv -Path .\files.csv -NoTypeInformation -Encoding utf8
~~~

> [!NOTE]
> 如果脚本被执行策略阻止，先查看 Get-ExecutionPolicy -List 并了解组织安全策略；不要为了临时运行未知脚本而盲目放宽系统策略。
