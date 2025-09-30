# Project Zomboid B42 社区多人补丁服务器

[English Documentation](README.md)

## 项目概述

本项目提供了一个Pterodactyl面板的egg配置，用于部署Project Zomboid B42多人游戏服务器，通过社区开发的补丁实现B42版本的在线多人游戏支持。

## 功能特性

- **B42多人游戏支持**: 社区开发的补丁为B42版本启用了多人游戏功能
- **Pterodactyl面板集成**: 完整的egg配置，便于快速部署
- **SteamCMD集成**: 自动化的游戏安装和更新
- **自定义启动脚本**: 优化的服务器启动，包含适当的Java参数
- **Docker支持**: 使用SteamCMD Debian镜像进行容器化部署

## 技术细节

- **游戏**: Project Zomboid (Steam应用ID: 108600)
- **版本**: B42 (不稳定分支)
- **平台**: Linux
- **依赖**: Java, SteamCMD, 各种Java库
- **许可证**: MIT许可证

## 文件结构

```
├── B42MP-1.57.rar              # 多人补丁 v1.57
├── B42MP-1.58.rar              # 多人补丁 v1.58
├── egg-project-zomboid-b42-community-multiplayer-patch-server-e-n.json  # 英文egg配置
├── egg-project-zomboid-b42-community-multiplayer-patch-server-c-n.json  # 中文egg配置
├── start.sh                    # 服务器启动脚本
└── LICENSE                     # MIT许可证
```

## 服务器配置

服务器支持以下环境变量：

- `SERVER_NAME`: 服务器配置文件名称
- `ADMIN_USER`: 管理员用户名
- `ADMIN_PASSWORD`: 管理员密码
- `STEAM_PORT`: Steam UDP端口 (默认: 16262)
- `STEAM_USER`: Steam账户用户名 (首次安装必须填写)
- `STEAM_PASS`: Steam账户密码 (首次安装必须填写)
- `DEPOT_APPID`: Steam应用ID (108600)
- `DEPOT_SUBID`: Steam应用子ID (108603) - 用于Linux平台
- `DEPOT_MANIFESTID`: 仓库清单ID (249541819024555413) - 更改时需要重新安装。更多信息请查看：https://steamdb.info/depot/108603/manifests/
- `STEAM_BRANCHID`: 测试分支 (unstable)
- `PATCH_LINK`: 多人补丁下载链接
- `DEPOT_LINK`: DepotDownloader工具链接
- `START_SH`: 自定义启动脚本链接

## 安装步骤

1. 将egg配置导入到您的Pterodactyl面板
2. 使用导入的egg创建新服务器
3. 根据需要配置环境变量
4. 启动服务器 - 它将自动安装所有必需的组件

## 使用方法

服务器使用以下命令启动：
```bash
./start.sh -cachedir=/home/container/.server -servername {{SERVER_NAME}} -port {{SERVER_PORT}} -udpport {{STEAM_PORT}} -adminusername {{ADMIN_USER}} -adminpassword {{ADMIN_PASSWORD}}
```

## 重要说明

- 使用没有双重验证的Steam账户，以避免安装过程中输入验证码的问题
- 更新补丁或更改某些配置变量时需要重新安装服务器
- 默认管理员凭据：用户名 `admin`，密码 `P@ssWord`

## 许可证

本项目采用MIT许可证 - 详见[LICENSE](LICENSE)文件。

## 作者

由Shuazi233开发 (shuazi@ixovo.com)