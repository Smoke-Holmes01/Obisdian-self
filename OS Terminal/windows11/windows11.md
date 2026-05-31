以下为Windows 11终端（CMD/PowerShell）常用命令的Markdown整理，包含基础操作、系统管理及网络工具：

### 🖥️ 系统信息与管理
```cmd
systeminfo          # 显示详细系统配置
tasklist            # 列出所有运行中的进程
taskkill /IM 进程名.exe /F  # 强制结束进程
shutdown /s /t 0    # 立即关机
shutdown /r /t 0    # 立即重启
msconfig            # 系统配置工具（启动项管理）
```

### 📁 文件与目录操作
```cmd
dir                 # 列出当前目录内容
cd 路径             # 切换目录（例：cd C:\Windows）
mkdir 文件夹名      # 创建新目录
del 文件名          # 删除文件
rmdir /s 文件夹名   # 递归删除目录
copy 源文件 目标路径 # 复制文件
xcopy 源 目标 /E    # 复制目录及子目录
tree /F             # 显示目录树结构
```

### 🌐 网络诊断工具
```cmd
ipconfig /all       # 显示完整网络配置
ping 域名/IP        # 测试网络连通性（例：ping google.com）
tracert 域名        # 跟踪网络路径
netstat -ano        # 显示所有网络连接及PID
netsh wlan show profiles  # 查看保存的WiFi配置
```

### 💾 磁盘管理
```cmd
chkdsk /f           # 检查并修复磁盘错误
diskpart            # 进入磁盘分区工具
format 盘符: /FS:NTFS  # 格式化磁盘（⚠️谨慎使用）
wmic diskdrive get status  # 检查磁盘健康状态
```

### 🔧 系统维护
```cmd
sfc /scannow        # 扫描并修复系统文件
dism /Online /Cleanup-Image /RestoreHealth  # 修复系统映像
powercfg /batteryreport  # 生成电池健康报告
```

### 🛠️ 高级工具
```cmd
gpupdate /force     # 强制更新组策略
mstsc               # 启动远程桌面连接
certmgr.msc         # 证书管理（需PowerShell）
```

### ⚡ Windows 11 专属命令
```powershell
winget list         # 查看已安装应用（包管理器）
Get-WindowsUpdateLog # 获取更新日志(PowerShell)
Start-Process ms-settings:   # 快速打开设置应用
```

### 📦 包管理 (Windows Package Manager)
```powershell
winget search 软件名  # 搜索应用
winget install 软件ID # 安装应用
winget upgrade --all  # 更新所有软件
```

> **提示：**
> 1. 部分命令需**管理员权限**（右键终端选“以管理员身份运行”）
> 2. PowerShell支持大多数CMD命令，并新增 `Get-` 开头的现代命令（如 `Get-Service`）
> 3. 按 `Tab` 键可自动补全路径/文件名
> 4. 使用 `命令 /?` 查看帮助（如 `ping /?`）

### 💻 推荐终端
```powershell
wt                  # 启动现代化Windows Terminal
```

> 注：Windows 11已默认集成PowerShell 5.1及更高版本，建议优先使用PowerShell以获得更强大的功能。