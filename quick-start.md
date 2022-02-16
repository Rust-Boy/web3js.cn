# 快速入门

## 最简单的示例
- 安装
```sh
npm install web3
```
- 获取 web3 对象
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:8545"))
console.log(web3)
```
- 输出
```sh
Web3 {
  currentProvider: [Getter/Setter],
  _requestManager: RequestManager {
    provider: HttpProvider {
      withCredentials: false,
      timeout: 0,
      headers: undefined,
      agent: undefined,
      connected: false,
      host: 'HTTP://127.0.0.1:8545',
      httpAgent: [Agent]
    },
    ...
```

## 查看是否连接到节点
```sh
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:7545"))

web3.eth.net.isListening().then(console.log)
```
输出
```sh
true
```

## 查看 web3 连接的节点信息
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:7545"))

web3.eth.getNodeInfo().then(console.log)
```
输出
```sh
EthereumJS TestRPC/v2.13.1/ethereum-js
```