---
title: "版本上线 Checklist"
aliases:
  - "上线checklist"
  - "发正式包"
  - "发布流程"
  - "上线流程"
  - "提审流程"
  - "正式包发布"
tags:
  - "流程"
  - "上线"
  - "发布"
updated: "2026-02-12"
source: "P2测试安排表-2025 - 上线checklist"
---

# 版本上线 Checklist

## 简答
> 版本上线需要完成打包版本号确认、清理打包机、部署审核服、配置 entrance、各渠道包验证、上传备份等步骤。

---

## 发正式包流程

| 序号 | 时间点 | 内容 | 如何操作 | 备注 |
|------|--------|------|----------|------|
| 1 | 通知客户端合并 hotfix 时 | 确认 hotfix 分支的打包版本号 | 找客户端负责合并 hotfix 的同学确认 | |
| 2 | 打正式包前半天 | 清理打包机 | 第一次清理勾选 CleanBundleBuilds，之后再清不勾选 | 正式包出来后跟超哥确认整包大小是否 OK |
| 3 | 更新审核服前 | 跟服务器确认是否需要部署 pay 服 | 与服务器确认：pay 服部署是否影响老包支付、pay 服不部署是否影响审核服新包支付 | 理论上测试对应功能时就可以确认 |
| 4 | 审核服部署 | 正式服测试前需要部署审核服 | 1. 通知策划合并 master 配置，给出最终 tag<br>2. 通知服务器合并分支，部署审核服 | |
| 5 | 审核服测试前 | 更新运营资源 dynamic | 打一遍最新的 iOS 和安卓运营资源，并配置验证 | 防止 iOS 或安卓运营资源缺失 |
| 6 | 审核服测试前 | 配置线上新版本 entrance | 由组长或版本负责人添加 | |
| 7 | GP 包验证通过后 | 国际服 flexion、模拟器等 4 个 apk 打包 | 参考打包文档 | |
| 8 | flexion 等 4 个包验证通过后 | 国际服 PC games 包（Chrome OS）、Win 包 | 每个版本都默认出 | |
| 9 | main 包验证通过后 | 国服变体包导出、测试、上传百度网盘、taptap 等 4 个包上传 box | 参考文档 | |
| 10 | 正式包验证通过后 | 更新版本发布表记录 | 在表里按格式新增一行记录 | |
| 11 | 正式包发布后 | box 上传备份包 | 负责验包的同学将正式包下载至本地，再上传到 box 地址中，由版本负责人最后确认全部上传 | 地址：smb://box.nibirutech.com/Department/QAteam/P2/安装包 |
| 12 | 正式包发布后 | 第 9 步完成后，等线上正式包发布，转发到给包群 | | |
| 13 | 越南、国服 iOS、小米提审前 | TGS 增加屏蔽进游戏下载、酒馆游戏的配置 | TGS 中对越南 iOS、国服 iOS、小米的 SDK 增加 `"auditing":true` 配置 | 整包提审通过后需要删除该配置 |

---

## 各渠道包提审方式

| 渠道包 | 提审方式 |
|--------|----------|
| iOS 世界服、俄罗斯、国服 | 出包后自动上传，验证通过后在发布群内 @超哥提审 |
| GP、PC、Win、8 个马甲包 | 出包后自动上传，验证通过后在发布群内 @超哥提审（若自动上传失败，需要李映荷手动上传） |
| 越南包 | iOS 自动上传、安卓李映荷手动上传，验证通过后版本号转发给 zoe 提审 |
| flexion、模拟器、海外华为、catappult、main、华为、oppo、小米、九游、变体包 | 验证通过后，转发到给包群，@市场部同学（flexion 是 zoe 直接后台提交，需要提醒 zoe 修改提审版本号） |

**注意**：
- 如商店自动上传失败，先用 Jenkins 上传，仍失败在打包机上下载包，李映荷手动上传
- 如符号表上传失败，提醒康哥处理

---

## 打包机使用规则

| 环境 | 打包机 | 说明 |
|------|--------|------|
| 世界服 | 10 打包机 | 世界服包必须用 10 打包机 |
| 国服 | 8 打包机 | 国服包用 8 打包机 |

才能保证整包和 DLC 大小正常无过大差异（世界服 + 国服 DLC 28、国服 DLC 8）

---

## 各渠道打包参数

### 世界服 iOS（iOS、iOS俄罗斯、iOS越南）

| 项目 | 配置 |
|------|------|
| 打包机 | 10 |
| 打包工程 | p2-ios-temp |
| 分支名 | hotfix |
| 勾选 | UploadCDN |
| 勾选打包项 | AppStore、俄罗斯、越南（几个包可以一起打） |
| 取消勾选 | adhoc |
| 操作人 | 版本测试负责人 |

**备注**：
1. 出 master 后，大概 10 分钟后会同步自动出 adhoc 包
2. 下包点击对应的 adhoc-直接下载即可
3. 越南 iOS 目前暂无 adhoc 包，通过转 testflight 下载测试

### PC 包

| 项目 | 配置 |
|------|------|
| 打包机 | 10 |
| 打包工程 | p2-android-master |
| 分支名 | hotfix |
| Builder | 选择 BuildAndroidProjectChromeOSPipeline |
| 勾选 | UploadSymbolFileToFirebase、UploadCDN、ExportPackage、BuildAppBundle、PublishToGooglePlay |
| 勾选打包项 | ChromeOS（PC） |
| 操作人 | 版本测试负责人 |

**备注**：
1. 勾选 BuildAppBundle 是出 aab，不勾选出 apk
2. 勾选 UploadSymbolFileToFirebase 后打包失败可查找失败原因
3. 要出 PC 包注意 Builder 中必须选 BuildAndroidProjectChromeOSPipeline

### flexion、模拟器、海外华为、catappult

| 项目 | 配置 |
|------|------|
| 打包机 | 10 |
| 打包工程 | p2-android-master |
| 分支名 | hotfix |
| 勾选 | UploadSymbolFileToFirebase、UploadCDN、ExportPackage |
| 取消勾选 | BuildAppBundle、PublishToGooglePlay |
| 勾选打包项 | Flexion、模拟器、海外华为、Catappult |
| 操作人 | 版本测试负责人 |

**备注**：这四个是出 apk（其他国际服安卓都是 aab）

### GP、马甲包、越南包

| 项目 | 配置 |
|------|------|
| 打包机 | 10 |
| 打包工程 | p2-android-master |
| 分支名 | hotfix |
| 勾选 | UploadSymbolFileToFirebase、UploadCDN、ExportPackage、BuildAppBundle、PublishToGooglePlay |
| 勾选打包项 | gp、mj1、mj2、mj3、mj4、mj5、mj6、mj8、vn |
| 操作人 | 版本测试负责人 |

**备注**：导包不能勾选 UploadCDN、UnityBuild，其他与正常打包一致

### Windows 包

| 项目 | 配置 |
|------|------|
| 打包机 | 8 |
| 打包工程 | p2-win-x64 |
| 分支名 | hotfix |
| 操作人 | 版本测试负责人 |

**备注**：Win 包需要单独打运营资源

### 国服 iOS

| 项目 | 配置 |
|------|------|
| 打包机 | 8 |
| 打包工程 | p2-ios-temp-cn |
| 分支名 | hotfix（75 分支已统一） |
| 勾选 | UploadCDN、useXcodeBuildAgent、incrementalBuild |
| 勾选打包项 | 国服 |
| 取消勾选 | adhoc |
| 操作人 | 版本测试负责人 |

### 国服安卓（main、华为、oppo、小米、九游）

| 项目 | 配置 |
|------|------|
| 打包机 | 8 |
| 打包工程 | android-channel-build-cn |
| 分支名 | hotfix |
| 勾选打包项 | 主包、华为、oppo、小米、九游 |
| 操作人 | 版本测试负责人 |

**备注**：
1. 如已出过第一个包，打其他渠道只需点导出 apk 即可，不需要勾上传
2. 符号文件只有世界服才有，国服不用管

---

## 封 DLC 流程

| 序号 | 时间点 | 内容 | 备注 |
|------|--------|------|------|
| 1 | 封正式 DLC 前准备 | 大版本正式合并前，需要往回合一次分支：master → hotfix → bugfix → dev | 合并完成后需要验证 bugfix 环境无异常 |
| 2 | 版本尾期准备封正式 DLC 时 | 找版本配置负责人、客户端负责人从 hotfix 拉分支（命名格式一般为 hotfix_v**） | 用于 bugfix 合并 hotfix 后未发布前解决线上 bug |
| 3 | 拉取分支后，bugfix 上的功能基本测试完成且无阻塞 | 1. 找策划版本负责人将配置从 bugfix 合并至 hotfix<br>2. 配置合并完成后再找客户端版本负责人将 bugfix 合并至 hotfix | 要合配置时提前告知策划准备 |
| 4 | 合并完成后 | 1. 使用 28 机器打正式 DLC<br>2. 验证功能常规<br>3. 有 ondemand + hotfix 更新，需验证 ondemand 大小、仅拉到 ondemand 时所有前期小游戏流程正常<br>4. 发布表上填写好 DLC 信息，等待发布 | 注意提醒客户端、策划合并后改的 bug 提交至 hotfix |
| 5 | DLC 验证通过后 | 1. 发布前配置 hotfix → master 合并，出配置 tag（最早合并时间为部署前一天晚上）<br>2. 发布当天早上提醒服务器合并分支（bugfix → hotfix） | 提前与超哥确认服务器部署时间、部署范围、DLC 发布时间 |
| 6 | 确定时间后 | 1. 部署当天上午安排预部署测试<br>2. 预部署测试通过后，在约定的时间找服务器部署线上全服 | 预部署的服务器需要先验证非白名单玩家无法进入服务器 |

**注意**：封 DLC 时有 ondemand 更新需加个测试 mj 包的流程（跑所有 mj 包的前期）

---

## 强更方法

1. **第一步**：在 TGS 的"客户端版本号"中搜索 default，将搜索出的几项配置的客户端最低兼容版本改为要强更到的版本
   - 世界服有两项配置（GP 和 iOS）
   - 国服有三项配置（安卓主包、安卓渠道包、iOS）
   
2. **第二步**：删除低于客户端最低兼容版本的配置

**重要**：两个步骤缺一不可，操作顺序也不可更改

**删除规则示例**（线上已有 63.*、64.*）：
- 强更到 64.* → 直接删除 63.*
- 强更到 63.x，且 63.x 为最高版本 → 更新到 63.x
- 强更到 63.x，但 63.x 为中间版本 → 保持 63.*，该条配置下的【客户端最低兼容版本】更新为 63.x（更保险）

---

## 马甲包差异说明

| 渠道包 | 差异说明 |
|--------|----------|
| mj1（射击） | FTE 无小游戏选择，直接进射击小游戏玩法 |
| mj2（吞噬） | FTE 二选一：吞噬、香蕉 |
| mj3（连塔） | FTE 无小游戏选择，直接进连塔小游戏玩法 |
| mj4（赛车） | FTE 无小游戏选择，直接进赛车小游戏玩法 |
| mj5（mob control 小游戏） | FTE 无小游戏选择，直接进 mob control 小游戏 |
| mj6（塔防小游戏） | FTE 无小游戏选择，直接进塔防小游戏 |
| mj7 | 新前期，无小游戏 |
| mj8 | Ape commandos，直接进类似迷宫的小游戏 |
| 主包（国际服 GP + 四个渠道包、iOS、国服所有包） | FTE 三选一：香蕉、连塔、射击 |

**小游戏更新方式**：
- 射击小游戏：hotfix
- 其他所有小游戏：ondemand

**备注**：
1. 所有小游戏均有卡牌关卡，与普通关卡分别走 ABTest 按照比例控制
2. mj 包与主包共有的小游戏，关卡配置表

---

## 常见坑点

- **打包机选错**：世界服必须用 10 打包机，国服必须用 8 打包机
- **忘记清理打包机**：第一次清理要勾选 CleanBundleBuilds
- **审核配置未删除**：越南、国服 iOS、小米提审通过后需要删除 `"auditing":true` 配置
- **强更顺序错误**：必须先改最低兼容版本，再删除旧配置
- **符号表上传失败**：提醒康哥处理

---

## 相关链接
- [P2测试安排表-2025](https://docs.google.com/spreadsheets/d/1AtQ7xxwKW3689-P83yedFjjxkovMB8Jec1xOWuBwlxM)
- [Box 备份地址](smb://box.nibirutech.com/Department/QAteam/P2/安装包)
