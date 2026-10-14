# FBW Devnet 参考

本页识别 Solana **Devnet** 上既有 **flybrainwork / FBW** 代币和已完成 Wallet Mining V3 验收，供阅读及对账。已完成发行、接管、付款和 Result 关闭不能作为设置步骤重复执行。

## 完整公开身份

| 字段 | 值 |
| --- | --- |
| 网络 | Solana Devnet |
| Genesis | `EtWTRABZaYq6iMfeYKouRu166VU2xqa1wcaWoxPkrZBG` |
| 代币名称 | flybrainwork |
| 符号 / 小数精度 | FBW / 8 |
| Mint | `HCdV49RkqtC7pPwzHCYg5KtkmU8opifjojLbAyZXKgQW` |
| Wallet Mining V3 程序 | `5yxjnH1PSk8iQKfK3ejG4jfSkewkTKfcpJygojdb6sam` |
| 最初有限阶段 | `6CcCZodRjRq3WArpAEkpudVgiK4EhpsSaNiDL5zq8x6x` |
| 初始发行 atoms | 31,183,324,300,000,000 |
| 最初两单位预算 | 200,000,000 atoms / 2 FBW |

名称和符号是展示字段。Mint、genesis、代币程序、精度、权限与结算程序共同识别资产及环境。

## 发行与托管

原供应按三池模型仅发行一次。Wallet Mining V3 将既有供应纳入固定程序控制池，没有发行第二份上限。

Mint 权限已撤销，冻结权限不存在。元数据更新权限仍属于提供的测试钱包。该项目钱包还保留程序升级和获准 Result 关闭权限，因此部署存在明确管理信任。

## 两次最终付款

| 轮次 | 奖励 | 实际 Result 租金 | Finalized 证据 |
| --- | --- | --- | --- |
| 30 | 100,000,000 atoms / 1 FBW | 5,852,160 lamports | [付款交易](https://explorer.solana.com/tx/2ayKE5iZWaPRSmZJ4R3JUHBJvfad7jbGe8VqcfvCp1c8EH2t3G5WyX7hKAy5rcHqzuuLaTUDchJcaSJnKqg7Dvby?cluster=devnet) |
| 31 | 100,000,000 atoms / 1 FBW | 5,852,160 lamports | [付款交易](https://explorer.solana.com/tx/4EcBLHkHA5jTdBWp6TsAVVUMePzgNpx2WVaKjCsNfNXoET7KQ8FZEEVurrs93coi3LaJrqQX9vWPwkgYpEVYkmJU?cluster=devnet) |

两次均在同一授权下完成真实完整模型科学工作和获准的原生完整复算。持有人在付款之间销毁了十个 atoms；后续付款与先前付款恢复成功，无需恢复 mint 权限。

## Result 关闭与提现

第一个专用 Result 在满足保留要求、重新核验归档，并取得两份由真实项目签名授权的归档证书后关闭。租金退给固定项目接收方，永久经济证据保持已付款。

第二个 **1,024 字节 Result** 仍可在 [CUwx4EwnmCQQPpzE2Wkoy5qFL7xdcKJ4mBvFJz7PS8Rv](https://explorer.solana.com/address/CUwx4EwnmCQQPpzE2Wkoy5qFL7xdcKJ4mBvFJz7PS8Rv?cluster=devnet) 读取。

明确撤销授权后，矿工提取 **11,704,320 未使用 lamports**。这是未使用本金退款，不是收回已消耗租金。公开[执行记录](https://github.com/flybrainlabs/docs/blob/main/docs/WALLET_MINING_V3_EXECUTION.md)关联关闭与退款回执。

## 当前状态与检查

最初两个单位已解决，预算全部付清。永久单位和付款证据保持不变。

## 当前用户任务供给阶段

`task-supply-20261013-v1` 使用相同 Devnet genesis、程序、mint、政策与权限，阶段为 `PKG52R51QHcTS2ENH4jJJUpDawnvEVsUVK1DCNXFHuG`。两个此前未使用的校准下游群体具有独立 ScientificTaskId 和永久经济单位。发布前预留新预算 **200,000,000 atoms / 2 FBW**，每个验证通过赢家对应 **100,000,000 atoms / 1 FBW**。计划修订 3 开启第 32 轮并排队下一目标。

阶段与两个预留均有最终回执，见[任务供给初始化](https://github.com/flybrainlabs/contracts/blob/main/deploy/wallet-mining-v3/task-supply-20261013/initialization.json)。运营者提交三笔预算交易。该次更新没有创建替代 mint、矿工授权、获胜候选或奖励付款，单位留供浏览器参与者使用。实时剩余供给与预算会变化，开始前请查看挖矿页面。

结合[项目 Explorer](/explorer/)、公开配置和最终链上账户检查。RPC 故障应保留已信任的 finalized 证据。不能将不可用余额编造为零，也不能因为临时 Result 关闭就认定付款未发生。

这是 Devnet 验收，不激活主网、正式发行、收费 Marketplace 服务或生产资金。
