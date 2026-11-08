# 开发环境搭建指南

## 1. 基础工具

| 工具 | 用途 | 获取方式 |
| ---- | ---- | -------- |
| Git | 版本管理与协作 | https://git-scm.com |
| VS Code | 文本编辑器 | https://code.visualstudio.com |
| Node.js (LTS) | 以太坊开发工具链依赖 | https://nodejs.org |

## 2. 以太坊开发环境

### 方式一：Remix（零安装，推荐初学者）

浏览器访问 https://remix.ethereum.org 即可在线编写、编译、部署 Solidity 智能合约。

### 方式二：本地 Hardhat 工具链

```bash
mkdir hello-blockchain && cd hello-blockchain
npm init -y
npm install --save-dev hardhat
npx hardhat init
```

按提示选择 JavaScript 项目模板，初始化完成后即可使用：

```bash
npx hardhat compile    # 编译合约
npx hardhat test       # 运行测试
npx hardhat node       # 启动本地测试链
```

## 3. Hyperledger Fabric 环境（进阶）

- 依赖：Docker、Docker Compose、Go
- 参考 Fabric 官方文档安装 `fabric-samples` 测试网络：

```bash
curl -sSLO https://raw.githubusercontent.com/hyperledger/fabric/main/scripts/install-fabric.sh
chmod +x install-fabric.sh
./install-fabric.sh docker samples
```

## 4. 常见问题

- **npm 安装缓慢**：可切换国内镜像源 `npm config set registry https://registry.npmmirror.com`
- **Docker 拉取镜像失败**：配置国内镜像加速地址后重试
- 遇到其他问题欢迎提交 Issue 讨论
