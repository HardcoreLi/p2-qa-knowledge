---
title: "TGS Entrance 配置系统"
aliases:
  - "tgs"
  - "entrance"
  - "entrance配置"
  - "bundle配置"
  - "dynamic"
  - "ondemand"
  - "hotfix"
  - "patch"
  - "dlc配置"
tags:
  - "工具"
  - "配置"
  - "DLC"
updated: "2026-02-12"
source: "https://wiki.tap4fun.com/pages/viewpage.action?pageId=135236563"
---

# TGS Entrance 配置系统

## 简答
> TGS 是客户端配置管理系统，用于配置 entrance（bundle源），控制客户端资源版本。权限开通找李映荷。

---

## 权限开通
直接找李映荷添加

## 登录方式

**地址**：https://console.tap4hub.com/login

**登录方式**：
- 国际服/国服：选择 beta，game id 填 p2，谷歌登录
- ~~国服（已弃用）：选择 betacn1，game id 填 p2cn，钉钉登录~~（2025.2国服合并世界服后已弃用）

**配置位置**：登录 → entrance配置

---

## 安装包如何匹配 entrance 配置？

### 1. 匹配 bundle_id

| 渠道 | Bundle ID |
|------|-----------|
| 国际服 iOS | com.tap4fun.ape.appstore |
| 国际服安卓 | com.tap4fun.ape.gplay |
| 国服 iOS | com.tap4fun.ape.appstore.cn |
| 国服安卓 | com.tap4fun.ape.cn.main |
| 国服其他渠道 | com.tap4fun.ape.cn.dummy |

### 2. 通过 bundle_id 匹配版本号

**匹配优先级**：指定版本 > 通配版本 > default

例如：50.3 的包匹配优先级为：`0.50.3` > `0.50.*` > `default`

---

## Entrance 配置内容

每条 entrance 配置包含：
- 客户端版本号
- bundle_id
- bundle源（dynamic）
- bundle源（ondemand）
- bundle源（fteminigame）- 已取消
- bundle源（patch）
- bundle源（hotfix）

---

## 新增 Entrance 配置

### 情况一：新增大版本（如 50→51）

操作：复制上一版本相同 bundle_id 的配置并修改：
1. 客户端版本号改为新版本，命名为 `0.xx.*`（如 0.51.*）
2. bundle_id 去掉"副本"字样
3. 修改 dynamic、ondemand、fteminigame 为最新版本
4. 删除 patch、hotfix（如果有）

### 情况二：新增小版本（如 50.1→50.3）

操作：复制上一版本相同 bundle_id 的配置并修改：
1. 客户端版本号改为新版本，命名为 `0.xx.x`（如 0.50.3）
2. bundle_id 去掉"副本"字样
3. dynamic、ondemand、fteminigame **保持不变**
4. 删除 patch、hotfix（如果有）

---

## 更新 Entrance 配置

### Dynamic（活动资源）

**资源说明**：此类资源本身不包含在包体内，需要手动打出这类资源上传到 CDN 上，然后通过包体内配置的 CDN 下载链接下载到本地进行缓存。

**包含内容**：
- 活动 & 礼包 banner
- 英雄战装图标
- 雷达收集的图片
- 等

**为什么要更新**：新活动需要新 banner，资源在不断迭代

**如何更新**：
1. 在打包机 http://172.20.110.28:8080/view/DLC/ 找到对应的打资源工程
2. 直接执行即可，国服和国际服资源可公用，安卓、iOS 各打一个
3. 失败了可以看下分支是否被改成非 master 了
4. 等待【dlc上传cdn群】出现上传成功消息
5. 在 TGS 找到对应版本的 entrance 配置，修改 dynamic 为上传的版本号
6. 点击提交保存

### Ondemand（按需下载资源）

**资源说明**：此类资源日常会在包体中，在正式包中会通过分包的方式将其从主包体中剔除以减少包体大小，并把这类资源上传到 CDN 上，通过游戏内下载的方式更新。

**包含内容**：
- AC、KVK 下载资源（进入时必须下载的地图资源）
- 游戏音效
- 斗士 & 机甲 & 战车音效
- 赛车小游戏
- 吞噬小游戏
- 香蕉小游戏
- 连塔小游戏
- 解绳子小游戏

**为什么要更新**：每个版本都有新英雄，所以每个版本最好都更新

**如何更新**：
1. 打包时勾选 uploadCDN 选项
2. 查看【dlc上传cdn群】是否有和包版本号相同的资源上传成功
3. 在 TGS 找到对应版本的 entrance 配置，修改 ondemand 为对应版本号
4. 点击提交保存

**另一种更新方式**：构建 dlc（hotfix），CDN 上传成功后，找到对应版本的 entrance 配置，修改 ondemand 的版本号为对应上传的版本号（hotfix 的版本号）

---

## 客户端热更（DLC）

### 说明
一般用于修复线上客户端问题

### 两种更新类型
| 类型 | 名称 | 更新方式 | 配置方式 |
|------|------|----------|----------|
| 启动时更新 | patch | 重启游戏时下载 | 多版本用逗号分隔，往后追加 |
| 游戏内更新 | hotfix | 游戏内静默下载 | 直接覆盖旧版本号 |

⚠️ **注意**：提前跟需求方确认更新方式，如果对方不知道，反馈给组内当日线上bug跟进的负责人统一确认

### 构建 DLC 步骤

**打包机**：http://172.20.110.28:8080/view/DLC/

**使用工程**：
- 安卓：p2-android-asset-bundle
- iOS：p2-ios-asset-bundle

**步骤**：
1. 点击工程进入详情
2. 点击 Build 按钮，进入构建详情界面
3. GitBranch 栏修改分支为 hotfix 或 hotfix_cn（国服）
4. 构建：
   - **启动时更新（patch）**：AssetPatterns 内填入强更内容（跟程序确认），然后构建
   - **游戏内更新（hotfix）**：不做任何修改，直接构建
5. 等待构建完成，develop 群会出现打 dlc 完成的消息
6. 等待【P2 - dlc上传cdn群】确认上传完成
7. 在 TGS 配置 dlc：
   - **patch**：名称填 patch，版本填 dlc 版本号，更新方式选"启动时更新"
   - **hotfix**：名称填 hotfix，版本填 dlc 版本号，更新方式选"游戏内更新"
8. 点击提交，重启游戏客户端后可下载到对应的 dlc

### DLC 配置规则
- **patch**：若之前已配置过，在后面加英文逗号，往后加上最新版本号
- **hotfix**：若之前已配置过，直接覆盖旧版本号

### DLC 验证
- **启动时更新（patch）**：进入游戏时 loading 条加载本次 dlc，进入游戏直接验证
- **游戏内更新（hotfix）**：进入游戏时不会加载，需要重启客户端再验证

### 如何判定 DLC 已下载完？
1. beta 环境快速转圈调出日志面板，搜索"hotfix"：
   - 开始下载：`hotfix start loading`
   - 下载完成：`hotfix loading finished`
2. 打开 fps-dlc-Streaming Groups，hotfix 栏进度条加载成绿色后，证明下载完成

---

## 常见坑点
- **配置不生效**：检查 bundle_id 是否匹配
- **DLC 下载失败**：确认 CDN 上传成功
- **版本号填错**：注意区分 patch 和 hotfix 的配置方式
- **patch 要追加，hotfix 要覆盖**：不要搞混

## 相关链接
- [TGS 后台](https://console.tap4hub.com/login)
- [DLC 打包机](http://172.20.110.28:8080/view/DLC/)
- [Wiki 原文](https://wiki.tap4fun.com/pages/viewpage.action?pageId=135236563)
