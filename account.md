# 账户相关操作

## 查询节点包含的账户个数
> 返回当前节点控制的账户列表
```js
web3.eth.getAccounts().then(console.log)
```
输出
```sh
[
  '0xb588f29312fA735457C21436f12Ce247B6476fB6',
  '0x9e91F5c51C69870f74106FC4A9589dad6dCAf4C6',
  '0x8fCd25752F2e64ef6CdDc2E605c3955053ae32Ad',
  '0xB3B03c58C7478e4FA1c96083404ecd0639bC7857',
  '0x1d8Abb14b2487c729C60d59a030c7920f126DEE2',
  '0x4d0641e688a9c13F84e1eFa2B9f255D5f3e410a4',
  '0xb4b01371ad3657C61cAa06ec6bE4AfBCB89639e2',
  '0x8b0eBf077E25cB7f47B6094629fca38b8a33763C',
  '0x2f5e8BDE3818353E37966Cdd8269813a8796B615',
  '0x744B76c21Fa9761896298e0f0FC99B2B3fBe8872'
]
```

## 创建账户
```js
web3.eth.personal.newAccount('!@abc').then(console.log)
```
输出
```sh
0x7c0c312566163Fa73fd013Bf9C127b3388B4b435
```

## 查询获得奖励的账户地址
```js
web3.eth.getCoinbase().then(console.log)
```
输出
```sh
0xb588f29312fa735457c21436f12ce247b6476fb6
```

## 查询是否正在挖矿
```js
web3.eth.isMining().then(console.log)
```
输出
```sh
true
```