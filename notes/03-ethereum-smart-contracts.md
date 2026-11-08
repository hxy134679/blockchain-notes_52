# 以太坊与智能合约

## 1. 以太坊简介

以太坊（Ethereum）由 Vitalik Buterin 于 2014 年提出、2015 年上线，是第一个引入**图灵完备智能合约**的区块链平台。如果说比特币是一台"分布式账本计算器"，以太坊则是一台"全球分布式计算机"——即所谓的**世界计算机（EVM）**。

## 2. 关键概念

| 概念 | 说明 |
| ---- | ---- |
| 账户（Account） | 分为外部账户（EOA，由私钥控制）与合约账户（由代码控制） |
| Gas | 执行操作的计价单位，防止资源滥用，按 `Gas 用量 × Gas 价格` 计费 |
| EVM | 以太坊虚拟机，智能合约的运行环境 |
| Solidity | 最主流的智能合约开发语言，语法类似 JavaScript |
| 交易（Transaction） | 由外部账户发起、签名广播的状态变更请求 |

## 3. 第一个智能合约

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract HelloWorld {
    string public greeting = "Hello, Blockchain!";

    function setGreeting(string memory _g) public {
        greeting = _g;
    }
}
```

代码解读：

- `pragma solidity ^0.8.20` 声明编译器版本；
- `string public greeting` 是状态变量，写入后会永久保存在链上；
- `setGreeting` 是写操作（需消耗 Gas），读取 `greeting` 是免费的读操作。

## 4. 智能合约的开发流程

1. **编写**：使用 Solidity 编写合约（Remix 在线 IDE 或 Hardhat 本地工具链）；
2. **测试**：编写单元测试，部署到本地测试链验证；
3. **部署**：将合约字节码部署到测试网（如 Sepolia），再视情况部署主网；
4. **验证**：在区块浏览器（Etherscan）上验证源码，保证公开可审计。

## 5. 安全注意事项

- **重入攻击**：外部调用回调本合约修改状态，需遵循"检查-生效-交互"（Checks-Effects-Interactions）模式；
- **整数溢出**：Solidity 0.8 起内置溢出检查，旧版本需使用 SafeMath；
- **权限失控**：`onlyOwner` 等权限控制要谨慎设计，私钥丢失将导致合约无法管理；
- 经典案例：2016 年 The DAO 事件因重入漏洞被窃取约 360 万 ETH，直接导致以太坊硬分叉。

## 参考资料

- Solidity 官方文档：https://docs.soliditylang.org
- Ethereum 官方文档：https://ethereum.org/zh/developers/docs
- ConsenSys《智能合约最佳实践》
