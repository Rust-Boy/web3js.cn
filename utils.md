# 工具包

## 大数据处理工具
以太坊内部总是以 wei 来表示余额（大整数），只有显示余额的时候，才转换为 ether 或其他单位。JavaScript 中默认的数字精度无法确切地表示 wei

webjs 中，自带 BigNumber 库

1 wei = 10 ^ 8

示例
```js
var BigNumber = require("bignumber.js")
var balance = new BigNumber("111111111111111111111111111111111111111111111111111");
console.log(balance)
```
输出
```sh
BigNumber {
  s: 1,
  e: 50,
  c: [ 111111111, 11111111111111, 11111111111111, 11111111111111 ]
}
```

## 将一个大数转化为十进制
```js
var BigNumber = require("bignumber.js")
var balance = new BigNumber("111111111111111111111111111111111111111111111111111");
console.log(balance.toString(10))
```
输出
```sh
111111111111111111111111111111111111111111111111111
```

## 检查是否为 BigNumber 对象
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:7545"))

var BigNumber = require("bignumber.js")
var balance = new BigNumber("111111111111111111111111111111111111111111111111111");
var number = balance.toString(10)

var res = web3.utils.isBigNumber(number)
console.log(res)

res = web3.utils.isBigNumber(balance)
console.log(res)
```
输出
```sh
false
true
```

## 数值转换
> wei 是最小的以太单位

- 将给定的以太金额转换为不同单位的数值
```js
console.log(web3.utils.fromWei('1', 'ether'))
console.log(web3.utils.fromWei('1', 'finney'))
console.log(web3.utils.fromWei('1', 'szabo'))
console.log(web3.utils.fromWei('1', 'shannon'))
```
    输出
    ```sh
    0.000000000000000001
    0.000000000000001
    0.000000000001
    0.000000001
    ```

- 将给定的以太金额转换为以 wei 为单位的数值
```js
console.log(web3.utils.toWei('1', 'ether'))
console.log(web3.utils.toWei('1', 'finney'))
console.log(web3.utils.toWei('1', 'szabo'))
console.log(web3.utils.toWei('1', 'shannon'))
```
输出
```sh
1000000000000000000
1000000000000000
1000000000000
1000000000
```

- 任意值转换为 16 进制字符串
> 数值字符串将解析为数值，文本字符串将解析为 utf8 字符串
```js
console.log(web3.utils.toHex('234'))
console.log(web3.utils.toHex(234))
```
输出
```sh
0xea
0xea
```

- 16 进制字符串转化为数值字符串
```js
console.log(web3.utils.hexToNumberString('0xea'))
```
输出
```sh
234
```

- 一些杂七杂八的转换
```js
console.log(web3.utils.asciiToHex('abcdef'))
console.log(web3.utils.hexToBytes('0x616263ea'))
console.log(web3.utils.bytesToHex([97, 98, 99, 234]))
```
输出
```sh
0x616263ea
```

## 检查是否为地址
```js
console.log(web3.utils.isAddress('0x5B38Da6a701c568545dCfcB03FcB875f56beddC4'))
```
输出
```sh
true
```