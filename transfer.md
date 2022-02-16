# 交易相关操作

## 获取指定块中特定账户地址的余额
函数原型
```js
web3.eth.getBalance(address [, defaultBlock] [, callback])
```
    defaultBlock：表执行到指定的区块时的余额
    区块号
    区块的 hash 值
    字符串 “earliest”、“latest”、“pending
示例
```js
web3.eth.getBalance('0x956188a6bD41694BdB13AA5CE168543a03B74770', function(error, result) {
    if (error) {
        console.log("something error.")
    } else {
        var balance = result.toString()
        console.log(web3.utils.fromWei(balance, "ether"))
    }
})
```
输出
```sh
0
```

## 查询平均 gas 价格
> 获取当前 gas 价格，该价格由最近的若干块的 gas 价格中值决定
```js
web3.eth.getGasPrice().then(console.log)
```
输出
```sh
20000000000
```

## 发送交易
```js
var transactionObject = {
    from: '0xb588f29312fA735457C21436f12Ce247B6476fB6',
    to: '0x9e91F5c51C69870f74106FC4A9589dad6dCAf4C6',
    value: web3.utils.toWei('1', 'ether'),
    data: web3.utils.toHex(234)
}

web3.eth.sendTransaction(transactionObject).then(console.log)
```
输出
```sh
{
  transactionHash: '0x1e7b41544f9e71ccee670d8a3560376446c49743ee64f07c5e36a17be707877e',
  transactionIndex: 0,
  blockHash: '0x5ee052595201447637a17973e7493a8fef06e543022c389b80e904c272ae28b0',
  blockNumber: 1,
  from: '0xb588f29312fa735457c21436f12ce247b6476fb6',
  to: '0x9e91f5c51c69870f74106fc4a9589dad6dcaf4c6',
  gasUsed: 21016,
  cumulativeGasUsed: 21016,
  contractAddress: null,
  logs: [],
  status: true,
  logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'                                                                       
}
```

## 查询交易信息
函数原型
```js
web3.eth.getTransaction(transactionHash [, callback])	返回具有指定哈希值的交易对象
```
- transactionHash - 交易哈希

示例
```js
web3.eth.getTransaction('0x1e7b41544f9e71ccee670d8a3560376446c49743ee64f07c5e36a17be707877e').then(console.log)
```
输出
```sh
{
  hash: '0x1e7b41544f9e71ccee670d8a3560376446c49743ee64f07c5e36a17be707877e',
  nonce: 0,
  blockHash: '0x5ee052595201447637a17973e7493a8fef06e543022c389b80e904c272ae28b0',
  blockNumber: 1,
  transactionIndex: 0,
  from: '0xb588f29312fA735457C21436f12Ce247B6476fB6',
  to: '0x9e91F5c51C69870f74106FC4A9589dad6dCAf4C6',
  value: '1000000000000000000',
  gas: 90000,
  gasPrice: '20000000000',
  input: '0xea',
  v: '0x26',
  r: '0x9d02df03d72fe5099192e3348d74da0a6f5f00645c48a19bb4f99ac22583b2a',
  s: '0x51a7939ed360fbfa466c8431e5279e03f0642a45a7bcd8d63e32071053d89517'
}
```

## 查询交易收据
函数原型
```js
web3.eth.getTransactionReceipt(hash [,callback])
//返回指定交易的收据对象，如果交易处于 pending 状态，则返回 null
```
示例
```js
web3.eth.getTransactionReceipt('0x11e1559508147c7ea2d3e9ce0dfb65be29d42d7a9077f9cef3e80ad64d38b3b8').then(console.log)
```
输出
```sh
{
  transactionHash: '0x1e7b41544f9e71ccee670d8a3560376446c49743ee64f07c5e36a17be707877e',
  transactionIndex: 0,
  blockHash: '0x5ee052595201447637a17973e7493a8fef06e543022c389b80e904c272ae28b0',
  blockNumber: 1,
  from: '0xb588f29312fa735457c21436f12ce247b6476fb6',
  to: '0x9e91f5c51c69870f74106fc4a9589dad6dcaf4c6',
  gasUsed: 21016,
  cumulativeGasUsed: 21016,
  contractAddress: null,
  logs: [],
  status: true,
  logsBloom: '0x00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000'                                                                       
}
```