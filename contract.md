# 与合约交互

> abi 简绍：相当于智能合约暴漏出来的标准接口，通过这个接口与智能合约交互

## 调用智能合约读函数
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:8545"))

var abi = [/* 这里省略掉 abi */]

var contractAddress = '0x4E4861f95f4cB129Dae9E739458f1583E1100Dd1'
var myContract = new web3.eth.Contract(abi, contractAddress)

myContract.methods.getNumber().call(function(error, result) {
    console.log(result)
})s
```

## 调用智能合约写函数
> 调用写函数，相当于发送了交易
```js
myContract.methods.setNumber(1234)
    .send({ from: '0x956188a6bD41694BdB13AA5CE168543a03B74770' })
    .on('receipt', function(receipt) {
        console.log(receipt)
})
```

## 执行事件查询
合约部分
```solidity
pragma solidity >= 0.7.0 <0.9.0;

contract DemoSimple {
    uint number;

    event myEvent(uint name);

    function setNumber(uint _number) public {
        emit myEvent(_number);
        number = _number;
    }

    function getNumber() public view returns(uint) {
        return number;
    }
}
```
js 部分
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:7545"))

var abi = [/* 这里省略掉 abi */]

var contractAddress = '0x9af62672FA2a5f749Df1e3EdCE2A4825Adb73dF2'
var myContract = new web3.eth.Contract(abi, contractAddress)

myContract.getPastEvents(
    'AllEvents', {
        fromBlock: 0,
        toBlock: 'latest'
    },
    (error, result) => { console.log(result) }
)
```

## 手工部署合约
```js
let Web3 = require("web3")
let web3 = new Web3(new Web3.providers.HttpProvider("HTTP://127.0.0.1:7545"))

var abi = [/* 这里省略掉 abi */]
var myContract = new web3.eth.Contract(abi)

// deplay 的 字节码
var data = /* 字节码 */

var candidateNames = ['0x416c696365', '0x4265747479', '0x5365615361']
myContract.deploy({
    data: data,
    arguments: [candidateNames]
}).send({
    from: '0x88F3f579A8f1A84376884286Bd4A7927593834D7',
    gas: 1500000,
    gasPrice: '1000000'
}, function(error, result) {
    console.log(result)
})
```