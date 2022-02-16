# Provider 相关

## 查看当前 web3 provider
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:7545"))

console.log(web3.currentProvider)
```
输出
```sh
HttpProvider {
  withCredentials: false,
  timeout: 0,
  headers: undefined,
  agent: undefined,
  connected: false,
  host: 'HTTP://127.0.0.1:7545',
  httpAgent: Agent {
    _events: [Object: null prototype] {
      free: [Function (anonymous)],
      newListener: [Function: maybeEnableKeylog]
    },
    _eventsCount: 2,
    _maxListeners: undefined,
    defaultPort: 80,
    protocol: 'http:',
    options: { keepAlive: true, path: null },
    requests: {},
    sockets: {},
    freeSockets: {},
    keepAliveMsecs: 1000,
    keepAlive: true,
    maxSockets: Infinity,
    maxFreeSockets: 256,
    scheduling: 'lifo',
    maxTotalSockets: Infinity,
    totalSocketCount: 0,
    [Symbol(kCapture)]: false
  }
}
```

## 设置/修改 provider
> 其实就是临时修改为其他的 provider
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:8545"))

// 设置为新的 provider
web3.setProvider(new Web3.providers.HttpProvider("HTTP://127.0.0.1:8545"))
```

## 批处理
> 批处理请求就是将几个请求打包在一起提交，可以保证交易顺序
```js
// 创建批处理对象
var batch = new web3.BatchRequest()

// 添加事务
batch.add(web3.eth.getBalance.request('0x9EC38bFa98Ff2AF34081544BE0d1aA9C709D8283', 'latest', function(error, res) {
    if (error) {
        console.log("s")
    }
}))
```