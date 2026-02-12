---
title: "测试账号及支付方式"
aliases:
  - "测试账号"
  - "支付测试"
  - "沙盒账号"
  - "ios支付"
  - "安卓支付"
  - "华为支付"
  - "catappult"
  - "flexion"
  - "emulator"
  - "充值中心"
tags:
  - "参考"
  - "测试"
  - "支付"
updated: "2026-02-12"
source: "P2_GM指令 Google Sheet - 测试账号以及支付"
---

# 测试账号及支付方式

## 简答
> iOS 沙盒支付用 `qa_p2@nibirutech.com`，安卓沙盒用 `Androidtest@nibirutech.com`，华为沙盒找章哥设置。各渠道包支付方式不同，catappult 用 AppCoins Wallet，flexion 用 flexion tester，emulator 用银行卡。

---

## iOS 测试账号

| 用途 | 账号 | 密码 | 备注 |
|------|------|------|------|
| **Apple ID 登录** | liyinghe@nibirutech.com | Lyh01010. | 苹果商店登录账号 |
| TestFlight 登录 | p2testflight@gmail.com | Tap4fun99 | 验证码：尾号 90 找德子哥，41 找章哥 |
| **沙盒支付** | qa_p2@nibirutech.com | Tap4fun66@P2 | 先退出 App Store 账号，在游戏内拉起支付后输入 |
| 美区 App Store | ll_neky@163.com | LLhyr@0509 | - |
| 沙盒账号 01-09 | p2sanbox01~09@nibirutech.com | Tap4fun99 | - |
| 俄罗斯账号 | p2sanboxru@nibirutech.com | Tap4fun99 | 俄罗斯包在非俄罗斯 IP 下支付使用 |
| 非俄罗斯账号 | p2sanboxusa@nibirutech.com | Tap4fun99 | - |

---

## iOS 国服审核账号

| 用途 | 账号 | 验证码 |
|------|------|--------|
| **国服审核人员账号** | 13800138000 | 138138 |

> ⚠️ 支付成功弹窗中如果出现 Apple ID 字样且最后没有到账，请先检查支付账号是否正确

---

## 安卓测试账号

| 用途 | 账号 | 密码 | 备注 |
|------|------|------|------|
| **安卓沙盒** | Androidtest@nibirutech.com | Tap4fun202512 | - |
| 越南安卓 | 1109125059@qq.con | s4b7j3o5y9m2 | - |
| Flexion Tester | liyinghe@nibirutech.com | Tap4fun202501. | 需要 Google 验证码 |
| Facebook | 18482139241@163.com | Tap4fun99 | 验证码联系章弟均 |

---

## 华为测试账号

| 账号 | 密码 | 备注 |
|------|------|------|
| wangcunhao@nibirutech.com | Wch843202406 | 华为沙盒支付 |
| 17311629813 | xuanzun24685 | 华为沙盒支付 |
| guoyu1@nibirutech.com | gy19971127 | 华为沙盒支付 |

> 华为 P30 有现成的沙盒账号，测试国内华为包应用市场设置地区为中国，测试海外华为包需要改为俄罗斯或欧洲地区（登 VPN）

---

## VK 账号（俄罗斯 iOS）

| 账号 | 密码 | 备注 |
|------|------|------|
| 8619938104707 | gy19971127 | 验证码联系郭宇 |

> 俄罗斯看不到 VK，需要换 clash 地址：https://bava8u2znaj6bdzzjnfb.wgetcloud.online/link/8e829deb-c7d2-3717-b22e-493db06a18e4?target=clash

---

## 国际服渠道包线上支付

### Catappult 包支付
1. 在设备下载 **AppCoins Aptoide Wallet** 软件
2. 打开软件，在主页点击余额后方的省略号 → 选择恢复钱包
3. 输入恢复代码（见下方）
4. 点击恢复钱包按钮
5. 在游戏内选择 **AppCoins Wallet** 支付

**恢复代码**：
```json
{"address":"0a10911196b2b63a0ca6dc09ae2e81faaebeab51","id":"eece0986-e0c4-4fc6-9c52-c040569a4aab","version":3,"crypto":{"cipher":"aes-128-ctr","cipherparams":{"iv":"751a4d827853aee90d65e6f90e4e196b"},"ciphertext":"cfff3cb0d23d025fd8d5300e3aba4708d2c9ca2423624881a80c5e3b8386112a","kdf":"scrypt","kdfparams":{"dklen":32,"n":512,"p":1,"r":8,"salt":"b60a37e53fbc9d6b5472e33c0d903e2df3468d1eafa60c76a5bd9aec7f531be9"},"mac":"30adf385287e2355d53f6e6c68f1af6cdbefc416a72a45d522438a881896329d"}}
```

> 安装 AppCoins Wallet 后选择 **sandbox** 选项即可正常支付，不需要找平台充值余额
> 钱包激活一次后保质期 1 个月，过期后需要找庞浩东重新激活

---

### Emulator 包支付
点击支付按钮后跳转支付网站 pay2h5.tap4fun.com，使用银行卡支付

**测试银行卡**：
- 卡号：`4514 6175 5276 8170`（550）
- 到期日：28 年 06 月
- 验证码找 luoli 姐

**测试卡**：
- 卡号：`4111 1111 1111 1111`
- 日期：12/40
- 验证码随便填

> 用三星折叠屏，测试环境默认有 card 支付，无 card 支付可以不挂 vpn 用线上环境支付

---

### Flexion 包支付
1. 直接走正常流程进线上进行支付
2. 线上无法支付再走以下流程：
   - 进 OTA，选择 flexion 的 debug 打开游戏
   - 在 FPS 中将环境 Environment 选成 Gold，退出游戏
   - 再次进入 OTA，选择 flexion 的 debug 打开游戏
   - 点击支付按钮打开支付弹窗，选择 success

**Flexion Tester 使用**：
1. 安装 flexion tester（p2 群文件中找 connected-test-mode-app）
2. 登录账号：liyinghe@nibirutech.com / Tap4fun202501.
3. 安装 Google Authenticator 或 2FAS 接收验证码

---

### 华为包支付
1. 找 zhangjinge 把需要支付的华为账号设置为沙盒账号
2. 登录华为沙盒账号，可以直接进行支付

> 用华为 P30pro，不需要梯子，guoyu 账号线上环境支付

---

### 俄罗斯 iOS 包银行卡支付
1. 首先和超帅确认当前版本是否有支付相关代码改动
2. 点击任意礼包的购买按钮，进入网页支付界面
3. 选择 **Sberpay（SBP）** 选项，进入支付界面
4. 把该界面的链接发给平台服务器同学（王煜）
5. 等待服务器同学通知操作成功后，检查礼包是否到账

> 俄罗斯支付除非平台 SDK 有支付改动需求，否则默认不需要验证

---

## 充值中心支付（Airwallex）

### 地址
- 测试服：https://pay2-beta.tap4fun.com/
- 线上：https://pay2.tap4fun.com/

> 国际服充值不再需要挂 vpn，登录国服账号自动切到国服充值，登录国际服账号自动切到国际服充值

### 国服玩家
1. 登录到充值中心界面
2. 登录国服账号（界面自动切换到国服充值界面）
3. 进行购买（支付方式：银行卡、微信、支付宝）

### 国际服玩家（不包含俄罗斯）
1. 登录到充值中心界面
2. 登录国际服账号
3. 选 card 进行购买

**测试卡**：
- 卡号：`4035 5010 0000 0008`
- 日期随意填（填比较大的）
- 验证码随意填

### 俄罗斯玩家
登录国际服账号，选择俄罗斯支付，与俄罗斯 iOS 包银行卡支付表现一致

---

## 国服渠道包线上支付

| 渠道 | 说明 |
|------|------|
| 小米包、海外华为包 | 在 gold 环境测试，beta 环境无法测试 |

---

## 验包注意事项

1. 验包前记得确认 entrance 的线上及测试服都配了，登录提示网络错误检查 entrance
2. iOS 越南包需要先上传 testflight 再下载，广告只能挂 vpn 才能看到，没有 adhoc
3. 国服渠道 entrance 选择：`com.tap4fun.ape.cn.dummy`
4. 国服包支付除了小米都进测试环境测，0.01 价格
5. 国服九游只有香蕉和连塔小游戏
6. PC 包：谷歌模拟器 beta 版登 zhangdijun 的谷歌账号，下载游戏
7. win 包装包需要单独打 dynamic，同时添加新版本的 entrance
8. iOS 国服、越南、国服安卓渠道在验包和未过审阶段会配置 auditing（屏蔽进游戏下载资源+屏蔽酒馆游戏）
9. 海外华为包验证时需要同时检查新号和老号（androidtest@nibirutech.com）登录是否正常

---

## 常见坑点

- **iOS 沙盒支付**：必须先退出 App Store 账号，在游戏内拉起支付后再输入沙盒账号
- **Catappult 钱包过期**：钱包激活一次后保质期 1 个月，过期找庞浩东重新激活
- **华为沙盒设置**：需要找 zhangjinge 把账号设置为沙盒账号
- **俄罗斯支付**：需要挂 VPN 才能看到 VK
