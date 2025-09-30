# Project Zomboid B42 Community Multiplayer Patch Server

[中文文档](README_CN.md)

## Project Overview

This project provides a Pterodactyl panel egg configuration for deploying a Project Zomboid B42 multiplayer server with community-developed patches that enable online multiplayer support for the B42 version.

## Features

- **B42 Multiplayer Support**: Community-developed patches enable multiplayer functionality for the B42 version
- **Pterodactyl Panel Integration**: Complete egg configuration for easy deployment
- **SteamCMD Integration**: Automated game installation and updates
- **Custom Startup Script**: Optimized server startup with proper Java arguments
- **Docker Support**: Containerized deployment using SteamCMD Debian images

## Technical Details

- **Game**: Project Zomboid (Steam App ID: 108600)
- **Version**: B42 (unstable branch)
- **Platform**: Linux
- **Dependencies**: Java, SteamCMD, various Java libraries
- **License**: MIT License

## File Structure

```
├── B42MP-1.57.rar              # Multiplayer patch v1.57
├── B42MP-1.58.rar              # Multiplayer patch v1.58
├── egg-project-zomboid-b42-community-multiplayer-patch-server-e-n.json  # English egg config
├── egg-project-zomboid-b42-community-multiplayer-patch-server-c-n.json  # Chinese egg config
├── start.sh                    # Server startup script
└── LICENSE                     # MIT License
```

## Server Configuration

The server supports the following environment variables:

- `SERVER_NAME`: Server configuration file name
- `ADMIN_USER`: Administrator username
- `ADMIN_PASSWORD`: Administrator password
- `STEAM_PORT`: UDP port for Steam (default: 16262)
- `STEAM_USER`: Steam account username (required for first installation)
- `STEAM_PASS`: Steam account password (required for first installation)
- `DEPOT_APPID`: Steam Application ID (108600)
- `DEPOT_SUBID`: Steam Application Sub ID (108603) - Linux platform specific
- `DEPOT_MANIFESTID`: Depot Manifest ID (6529967175871940863) - requires reinstallation when changed. For more information, check: https://steamdb.info/depot/108603/manifests/
- `STEAM_BRANCHID`: Test branch (unstable)
- `PATCH_LINK`: Multiplayer patch download URL
- `DEPOT_LINK`: DepotDownloader tool URL
- `START_SH`: Custom startup script URL

## Installation

1. Import the egg configuration into your Pterodactyl panel
2. Create a new server using the imported egg
3. Configure the environment variables as needed
4. Start the server - it will automatically install all required components

## Usage

The server starts with the following command:
```bash
./start.sh -cachedir=/home/container/.server -servername {{SERVER_NAME}} -port {{SERVER_PORT}} -udpport {{STEAM_PORT}} -adminusername {{ADMIN_USER}} -adminpassword {{ADMIN_PASSWORD}}
```

## Important Notes

- Use a Steam account without two-factor authentication to avoid verification code issues during installation
- The server requires reinstallation when updating patches or changing certain configuration variables
- Default admin credentials: username `admin`, password `P@ssWord`

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Developed by Shuazi233 (shuazi@ixovo.com)